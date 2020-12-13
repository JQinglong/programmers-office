---
title: MagentoのSQL解析
author: KONNO Kiyotaka
type: post
date: 2018-09-22T07:30:48+00:00
url: /magentoのsql解析/
post_views_count:
  - 822
categories:
  - プログラミング
tags:
  - Magento

---
自分で作成したページ・ウィジェット・ブロックに思うように商品が表示されない。

ならば、どのようなSQLが流れていて、何が引っかかって表示されないのか調べてみよう、という活動です。

## 1.環境整備

### (1)SSH接続用ターミナルソフト

Tera TermでもPuttyでも、お好きなものをどうぞ。  
ではあるのですが、AWS内bitnamiで構築した環境のMy SQLに接続する、という観点で。

Puttyでは、Host Nameにユーザ名@xxxを記載しますが、bitnamiで構築した場合は、  
ubuntu@xx.us-east-2.compute.amazonaws.com  
というようになります。

そして、Connection＞SSH＞Auth　でPrivate keyにppkファイルを登録します。

この接続状態をそのまま保存しておいて、次回からはSaved Sessionから呼び出すだけなので、現在は基本的にはPuttyを使用しています。

Tera Termでは、ホスト欄にxx.us-east-2.compute.amazonaws.comを入力しOK、ユーザ名にubuntu、「RSA/DSA/ECDSA/ED25519鍵を使う」で、ppkファイルではなくpemファイルを指定する、という形になり、ホスト名以外は次回に覚えてくれていないので、ちょっと面倒だなと思っています。ターミナル上での見た目はTeraの方がきれいなので好きなのですが。

### (2)WinSCP

ファイルのアップ・ダウンロード用にはこちら。

SFTPで、ホスト名はxx.us-east-2.compute.amazonaws.com、ユーザ名はubuntu、設定＞SSH＞認証の秘密鍵にppkファイルを指定します。

これも、保存しておけば、次回以降の接続はリストから選択するだけなので、よいです。

### (3)A5 : SQL Mk-2

これが本日のポイント。  
<a title="https://a5m2.mmatsubara.com/" href="https://a5m2.mmatsubara.com/" target="_blank" rel="noopener">https://a5m2.mmatsubara.com/</a>

DB接続ツールは色々ありますけど、個人的にはこれが最強だと思っています。  
特に、最強なのがSQL整形機能。今回のように、ログからSQLを取り出して解析しようと思う時に、Ctrl-Q一発でSQLを見やすくしてくれるのは、非常に助かるので、普段の会社の仕事でも使っております。

これの接続は、ちょっとばかり難しいです。トンネリングでの接続になります。  
A5 : SQL の接続を作成する際にはMySQL/MariaDBを選択できます。その中の設定で、SSH2トンネルの指定ができます。  
「SSH2トンネル」タブのSSH2ホスト名をxx.us-east-2.compute.amazonaws.com、ユーザーIDをubuntuにして、秘密鍵ファイルにpemファイルを指定します。  
その上で、「基本」タブのサーバー名にはSSH2サーバーから見たサーバー名を指定するので、初期の状態ならlocalhostを指定します。Magento用に作成したユーザーID、パスワードを指定しますが、  
grant select on \*.\* to home;  
が必要だったように思います（記録し忘れている）。

ということで、この3点セットがそろうと、割と自由にDBもいじれるかと思います。

## 2.MySQLのクエリトレース

普段はSQL Serverが主戦場なので、トレース取得はProfilerを便利に使用させていただいています。

ではMySQLはどうかということで、こちらを参考にさせていただきました。  
<a title="http://blog.szmake.net/archives/496" href="http://blog.szmake.net/archives/496" target="_blank" rel="noopener">http://blog.szmake.net/archives/496</a>

my.cnfはどこにあるかというと、これはbitnami特有で、/opt/bitnami/mysql/　にあります。

また、my.confを編集した後、MySQLをリスタートするのですが、これもbitnami特有で  
sudo /opt/bitnami/ctlscript.sh restart mysql  
となります。

bitnamiでは、/opt/bitnami　配下に色々なものが存在する、ということを認識しておくだけでもいろいろはかどるかと思います。

## 3.Magentoで実行されるSQL

で、トレースを取ってみた結果です。  
例えば、  
SELECT \`mg\_store\_website\`.* FROM \`mg\_store\_website\`  
↓  
website\_id    code    name    sort\_order    default\_group\_id    is_default  
みたいなのが取れることが分かるだけでも、今後の理解には役立ちそうです。

今回のポイントは、下に書いたSQLでした（A5 : SQL ではこのように整形してくれます。これがよいのです）。  
まず、全部LEFT JOINにして、  
stock\_status\_index.stock_status = 1  
をコメントアウトすると検索対象になるので、これを何とかする必要があることが分かります。  
また、コメントアウトしても、mg\_catalog\_category\_product\_index_store1がINNER JOINのままだと、2件しかヒットしないので、visibilityあたりが怪しそうだと考えます。

そうしてみてみると、商品の設定で、在庫状況が在庫切れになっています。  
実は、これは在庫ありにしたつもりだったのですが、Advanced Inventoryの子画面で、個数を入力して在庫ありにしないと反映されません。  
そもそも、ピザ屋さんのピザなんて在庫管理しない商品にしておくべきで、その辺を属性セットとして登録しておくべきな訳ですが、それはまだ試していません。

また、Visibilityという項目で表示設定を行います。  
ここで。「カタログ,検索」を指定しないと表示されません。  
これの使い方として、例えば、商品タイプとして、Configurable Productを指定した時に、基本商品は一覧に出すけど、サイズ別の商品設定は一覧には出さない、という場合には、サイズ別の商品は非表示にしておくことでそのような動作になります。  
[<img style="margin: 0px; display: inline; background-image: none;" title="image" src="https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2018/09/image_thumb-2.png?resize=244%2C154&#038;ssl=1" alt="image" width="244" height="154" border="0" data-recalc-dims="1" />][1]

こんな感じで、SQLを見ながら商品設定をしていくと表示されるようになるのですが、最後の砦として、システム＞キャッシュ管理　で更新することにより表示された、ということもありましたので、油断は禁物です。

こんな感じで、商品を表示するめどは立ってきました。

> SELECT DISTINCT  
> \`e\`.*  
> , \`cat\_index\`.\`position\` AS \`cat\_index_position\`  
> , \`price_index\`.\`price\`  
> , \`price\_index\`.\`tax\_class_id\`  
> , \`price\_index\`.\`final\_price\`  
> , IF (  
> price\_index.tier\_price IS NOT NULL  
> , LEAST(price\_index.min\_price, price\_index.tier\_price)  
> , price\_index.min\_price  
> ) AS \`minimal_price\`  
> , \`price\_index\`.\`min\_price\`  
> , \`price\_index\`.\`max\_price\`  
> , \`price\_index\`.\`tier\_price\`  
> , \`stock\_status\_index\`.\`stock\_status\` AS \`is\_salable\`  
> FROM  
> \`mg\_catalog\_product_entity\` AS \`e\`  
> left JOIN \`mg\_catalog\_category\_product\_index\_store1\` AS \`cat\_index\`  
> ON cat\_index.product\_id = e.entity_id  
> AND cat\_index.store\_id = &#8216;1&#8217;  
> AND cat_index.visibility IN (2, 4)  
> AND cat\_index.category\_id = &#8216;2&#8217;  
> left JOIN \`mg\_catalog\_product\_index\_price\` AS \`price_index\`  
> ON price\_index.entity\_id = e.entity_id  
> AND price\_index.website\_id = &#8216;1&#8217;  
> AND price\_index.customer\_group_id = 0  
> left JOIN \`mg\_cataloginventory\_stock\_status\` AS \`stock\_status_index\`  
> ON e.entity\_id = stock\_status\_index.product\_id  
> AND stock\_status\_index.website_id = 0  
> AND stock\_status\_index.stock_id = 1  
> WHERE  
> (((IFNULL(\`attribute\_set\_id\`, 0) = &#8217;16&#8217;)))  
> AND (stock\_status\_index.stock_status = 1)  
> LIMIT  
> 10

&nbsp;

#### 関連記事

  * [Magento ホームページカスタマイズへの道][2]
  * [Magento(マジェント)始めました][3]

 [1]: https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2018/09/image-2.png?ssl=1
 [2]: https://www.programmers-office.ml/2018/09/22/magento-%e3%83%9b%e3%83%bc%e3%83%a0%e3%83%9a%e3%83%bc%e3%82%b8%e3%82%ab%e3%82%b9%e3%82%bf%e3%83%9e%e3%82%a4%e3%82%ba%e3%81%b8%e3%81%ae%e9%81%93/
 [3]: https://www.programmers-office.ml/2018/09/17/magento%e3%83%9e%e3%82%b8%e3%82%a7%e3%83%b3%e3%83%88%e5%a7%8b%e3%82%81%e3%81%be%e3%81%97%e3%81%9f/