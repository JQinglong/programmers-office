---
title: Effective Java プログラミング言語ガイド
type: post
date: 2006-12-16T06:31:29+00:00
url: /effective-java-プログラミング言語ガイド/
post_views_count:
  - 394

---
実はずいぶん前に頂いた本ですが、やっと読みました。 

<div class="hreview">
  <a class="item url" href="http://www.amazon.co.jp/exec/obidos/ASIN/4894714361/konnokiyotaka-22/ref=nosim/"><img class="photo" style="padding-right: 0px; padding-left: 0px; float: left; padding-bottom: 0px; margin: 0px 15px 10px 10px; border-top-style: none; padding-top: 0px; border-right-style: none; border-left-style: none; border-bottom-style: none" alt="photo" src="https://i2.wp.com/ec1.images-amazon.com/images/P/4894714361.09._SCMZZZZZZZ_V1056618813_.jpg" data-recalc-dims="1" /></a> </p> 
  
  <dl style="font-size: 12px; min-height: 168px; margin-bottom: 0.5em; line-height: 16px; text-align: left">
    <dt class="fn">
      <a class="item url" href="http://www.amazon.co.jp/exec/obidos/ASIN/4894714361/konnokiyotaka-22/ref=nosim/">Effective Java プログラミング言語ガイド</a> </p>
      <dd>
        Joshua Bloch ジョシュア・ブロック </p> 
        
        <dd>
          ピアソン・エデュケーション 2001-12-03
        </dd></dl> 
        
        <dl style="font-size: 11px; line-height: 12px">
          <dt>
            <strong>おすすめ平均 </strong><img alt="star" src="https://i2.wp.com/g-images.amazon.com/images/G/01/detail/stars-4-5.gif" border="0" data-recalc-dims="1" /> </p> 
            
            <dd>
              <img alt="star" src="https://i1.wp.com/g-images.amazon.com/images/G/01/detail/stars-5-0.gif" border="0" data-recalc-dims="1" />上を目指す人の基礎固め </p> 
              
              <dd>
                <img alt="star" src="https://i1.wp.com/g-images.amazon.com/images/G/01/detail/stars-5-0.gif" border="0" data-recalc-dims="1" />脱初心者に必須 </p> 
                
                <dd>
                  <img alt="star" src="https://i1.wp.com/g-images.amazon.com/images/G/01/detail/stars-5-0.gif" border="0" data-recalc-dims="1" />Effective C++とともに最良の書籍 </p> 
                  
                  <dd>
                    <img alt="star" src="https://i1.wp.com/g-images.amazon.com/images/G/01/detail/stars-5-0.gif" border="0" data-recalc-dims="1" />JAVA言語を理解するための効果的な実践書です。 </p> 
                    
                    <dd>
                      <img alt="star" src="https://i1.wp.com/g-images.amazon.com/images/G/01/detail/stars-5-0.gif" border="0" data-recalc-dims="1" />翻訳も良いと思う
                    </dd></dl> 
                    
                    <p class="gtools" style="font-size: 10px">
                      by <a href="http://www.goodpic.com/mt/aws/index.html">G-Tools</a> , <abbr class="dtreviewed" title="2006/12/16">2006/12/16</abbr>
                    </p></div> 
                    
                    <p>
                      題材がJavaというだけで、.NETプログラマーでも十分に役立ちます。<br />私のようなパンピー（一般プログラマ）では、スレッドの辺りはあまり使わないので飛ばしてしまいましたが・・・。
                    </p>
                    
                    <p>
                      まず、自分的に一番ホットな内容だったのは、「継承よりコンポジションを選ぶ」。<br />元となるプログラムがあって、その機能を拡張するために継承を使うということを考える場合があると思います。<br />実は私も以前やったことがあり、どうもうまくいかないという感じがありました。ここでは問題点と解決法が明確に書かれており<br />・サブクラスはスーパークラスの実装に依存する→スーパークラスの変更でサブクラスの動作が不正になる可能性がある<br />・スーパークラスにメソッドが追加される可能性がある→サブクラスのメソッドとぶつかる可能性がある<br />そこで、コンポジションを使いましょうということで<br />・新クラス（ラッパクラス）に元クラスのインスタンスを持つ<br />・転送メソッドで、元クラスのメソッドを呼び出す<br />・拡張したいメソッドだけを実装する<br />という形で、元クラスのカプセル化を壊さないで実現するというわけです。<br />他でも読んだ記憶がありますが、継承はサブクラスがスーパークラスにis-a関係が成り立つときだけ使いましょうということです。
                    </p>
                    
                    <p>
                      次にいいと思ったのは、「nullではなく、長さゼロの配列を返す」。こうしておけば、最初にnullチェックをせずにいきなりループ処理に入っても安全なわけですね。
                    </p>
                    
                    <p>
                      あと、基本ですけどなかなかできていないこととして「メソッドのシグニチャを注意深く設計する」の中の「パラメータ型に関しては、クラスよりインタフェースを選ぶ」。余談ですが、画面コントロール（テキストボックスとか）をインターフェースの実装にできたら、記述が楽になるのかなと思ったり。
                    </p>
                    
                    <p>
                      さらに、「ローカル変数のスコープを最小限にする」の中で、変数宣言は使用の直前で、と言われているのは、好まない人もいると思いますが（最初に宣言が固まっていたほうが見やすい）、直前の方が安全だと思いますし、さらにループカウンタは別に宣言するのではなく、ループ変数を使うようにする（For i As Integer = 0 To n　みたいな宣言）というのも、使う変数を間違えないようにする等の効果が挙げられていてよいです。
                    </p>
                    
                    <p>
                      というわけで、コンポジッションは即実践！
                    </p>