---
title: WFSamplesの歩き方(6)：WorkflowSerialization
type: post
date: 2006-09-03T15:30:22+00:00
url: /wfsamplesの歩き方6：workflowserialization/
post_views_count:
  - 104

---
寝る前にもう一つ、「WorkflowSerialization」。 WFSamples\Technologies\Markup\WorkflowSerialization

フローを作って、XAMLにシリアライズして、それをまた読み込んで実行するというサンプルです。作られたxomlファイルをVisualStudioで開いてみると確かにこんな感じでできています。  
<a href="https://i0.wp.com/jqinglong.html.xdomain.jp/bimg/WFSamples6WorkflowSerialization_71C/image%7B0%7D%5B2%5D.png" atomicselection="true"><img style="border-right: 0px; border-top: 0px; border-left: 0px; border-bottom: 0px" height="240" src="https://i1.wp.com/jqinglong.html.xdomain.jp/bimg/WFSamples6WorkflowSerialization_71C/image%7B0%7D_thumb.png?resize=204%2C240" width="204" border="0" data-recalc-dims="1" /></a> 

シリアライズでは、WorkflowMarkupSerializerというのが準備されている、読み込みは  
Using reader As XmlReader = XmlReader.Create(workflowFilename) &nbsp;&nbsp;&nbsp;&nbsp;deserializedWorkflow = workflowRuntime.CreateWorkflow(reader)  
End Using  
でできてしまうということで、スマートですね。これはいけちゃうかもな～。まだちょっと怖いですけど。