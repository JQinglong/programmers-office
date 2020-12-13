---
title: Code4StartUp ～ UberEatsを作ろう ～ Facebook認証
author: KONNO Kiyotaka
type: post
date: 2018-06-09T00:26:26+00:00
url: /code4startup-～-ubereatsを作ろう-～-facebook認証/
post_views_count:
  - 933
categories:
  - プログラミング
tags:
  - Code4Startup

---
<a href="https://code4startup.com/?ref=kiyotakakonno" target="_blank">Code4Startup</a>

続いて、oauthによるFacebook認証。  
この辺の実践感がこの講座の良いところ。

<a href="https://developers.facebook.com/" target="_blank">https://developers.facebook.com/</a>  
スタートガイド→Facebook for Developersアカウントを作成するところから始めます。  
画面構成は講義ビデオの時からは大分変っているようですが、何とか進められます。  
で、django-rest-framework-social-oauth2==1.0.4をインストールすることになっているのですが、  
ImportError: No module named &#8216;social_django&#8217;  
となります。  
↓  
<a href="https://teratail.com/questions/115059" target="_blank">https://teratail.com/questions/115059</a>  
pip install social-auth-app-django  
↓  
ImportError: No module named &#8216;braces&#8217;  
↓  
pip install django-rest-framework-social-oauth2 -U  
→django-rest-framework-social-oauth2==1.1.0  
↓  
OK  
という感じで（分かりますか(^_^;;;)）、結局最新バージョンでないとライブラリ間の構成が合わないという話。  
requirements.txt　の記述は  
django-rest-framework-social-oauth2==1.0.4  
のままだけど・・・

でうまくいったかと思いきや、アプリ画面を開くと  
You may need to add &#8216;x.x.x.x&#8217; to ALLOWED_HOSTS. のエラー。  
settings.py  
のALLOWED_HOSTS に追記すれば確かに起動するようになった。  
<a href="https://www.deep-blog.jp/engineer/archives/4287" target="_blank">https://www.deep-blog.jp/engineer/archives/4287</a>  
しかし、これまで書いていなかったのになぜ？ちょっと気持ち悪い。

Facebook認証の流れについては、  
<a title="https://stackoverflow.com/questions/18995448/rails-api-authenticate-users-from-native-mobile-apps-using-username-password-or" href="https://stackoverflow.com/questions/18995448/rails-api-authenticate-users-from-native-mobile-apps-using-username-password-or" target="_blank">https://stackoverflow.com/questions/18995448/rails-api-authenticate-users-from-native-mobile-apps-using-username-password-or</a>  
と同じ内容の図がもう少しきれいに書かれていて、なるほど、と思いました。

そして、ブラウザ・サーバアプリ・Facebook間でのやり取りは、アプリを作る前に試しましょうということで、POSTMAN。  
このJSON大流行のこのタイミングで、このツールをぶつけてくるところがなかなか（たまたま）。

python-social-auth のPipelineの説明は、ビデオ見てると行方不明になりますが、下記になります。  
<a href="https://github.com/python-social-auth/social-docs/blob/master/docs/pipeline.rst" target="_blank">https://github.com/python-social-auth/social-docs/blob/master/docs/pipeline.rst</a>

ちょっと、Facebook認証で情報を取り出せるようになるので、GDPRが気になるところ。  
個人で試しているうちは気にしなくても良いかもしれませんが、早急に考えないといけないかと思っています。

<a href="https://code4startup.com/?ref=kiyotakakonno" target="_blank">Code4Startup</a>

<table style="border: currentcolor; border-image: none;" border="0" cellpadding="5">
  <tr>
    <td valign="top" style="border: currentcolor; border-image: none;">
      <a href="https://www.amazon.co.jp/exec/obidos/ASIN/4822292274/jqinglong-22/" target="_blank"><img style="margin-right: 10px;" src="https://i0.wp.com/images-fe.ssl-images-amazon.com/images/I/51%2BScGc8DAL._SL160_.jpg?ssl=1" border="0" data-recalc-dims="1" /></a>
    </td>
    <td valign="top" style="border: currentcolor; border-image: none; text-align: left;">
      <div class="kaerebalink-name" style="line-height: 120%; margin-bottom: 10px;">
        <a href="https://www.amazon.co.jp/exec/obidos/ASIN/4822292274/jqinglong-22/" target="_blank">独学プログラマー Python言語の基本から仕事のやり方まで</a>
      </div>
      <div class="kaerebalink-detail" style="margin-bottom: 5px;">
        コーリー・アルソフ 日経BP社 2018-02-24
      </div>
      <div class="kaerebalink-salesranking" style="margin-bottom: 5px;">
        売り上げランキング : 204
      </div>
      <table style="border: currentcolor; border-image: none; margin-top: 10px;">
        <tr>
          <td style="border: currentcolor; border-image: none; text-align: left;">
          </td>
          <td style="border: currentcolor; border-image: none; padding-left: 10px; font-size: x-small; vertical-align: bottom;">
            by <a href="https://kaereba.com" target="_blank" rel="nofollow">カエレバ</a>
          </td>
        </tr>
      </table>
    </td>
  </tr>
</table>