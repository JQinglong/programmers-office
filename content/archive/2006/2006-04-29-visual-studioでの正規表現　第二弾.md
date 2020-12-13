---
title: Visual Studioでの正規表現　第二弾
type: post
date: 2006-04-29T09:53:10+00:00
url: /visual-studioでの正規表現　第二弾/
post_views_count:
  - 882

---
ファイルの先頭に固定文字を挿入したいということがありまして、ちょっと悩みましたが・・・  
仮に著作権表示を追加するとすると  
検索する文字列  
{(.|\n)+}  
置換後の文字列  
#Region &#8220;Copyright&#8221;\n&#8217;Copyright(c) KONNO Kiyotaka 2005-2006 All rights reserved.\n#End Region\n\n\1  
こんな感じでした。  
要するに、ファイル全体をマッチさせてそれにタグをつけ、固定文字＋タグに置換するということですね。  
タグ付き正規表現バンザイ＼(^o^)／