---
title: Windows Workflow Foundation素振り
type: post
date: 2006-08-19T02:25:59+00:00
url: /windows-workflow-foundation素振り/
post_views_count:
  - 104

---
そろそろ仕事でもやり始めることになりそうなので素振り開始。  
NAgiler航海日誌v2　さん  
<http://d.hatena.ne.jp/takakuro/20060718>  
経由で  
.NET Framework 3.0 FAN Wikiさんのこちらを参考にインストール開始。  
<http://wiki.wince.ne.jp/winfx/?%BC%C2%B9%D4%A4%B9%A4%EB%BE%E5%A4%C7%C9%AC%CD%D7%A4%CA%A4%E2%A4%CE%A1%CA%A5%E9%A5%F3%A5%BF%A5%A4%A5%E0%A1%CB>  
最新はJuly 2006 CTPですかね。  
Microsoft Pre-Release Software Microsoft .NET Framework 3.0 &#8211; July 2006 CTP  
<http://www.microsoft.com/downloads/details.aspx?familyid=62057A6F-185F-41DB-ABE5-678F6FC388F0&displaylang=en>  
MicrosoftR WindowsR Software Development Kit (SDK) for July CTP (ISO Image)  
<http://www.microsoft.com/downloads/details.aspx?familyid=1D7F16B3-D2D5-48F7-9494-6696117EE712&displaylang=en>  
MicrosoftR Visual StudioR 2005 Extensions for WindowsR Workflow Foundation Release Candidate 4  
<http://www.microsoft.com/downloads/details.aspx?FamilyID=e74fecc8-1278-444e-b775-21f9e8e2a586&DisplayLang=en>  
最初は、あっさりインストール失敗。あれやこれやの試行錯誤の後、  
・完全版をインストールする必要がある（上記両サイトで書いてくださってました）  
・上の順番でインストール  
・NAgiler航海日誌v2　さんではJuneCTPは問題ありそうということだったのでJulyCTPを入れたところ、こちらは日本語XPSP2、日本語VS2005TeamEditionでOK  
という状況です。  
とりあえず、Microsoft SDKs\Windows\v6.0\Samples\WFSamples.zip内にPersistenceHost\VB\DocumentApprovalWorkflowというのがあったので動かしてみると、まだ、何をやっているかはわかりませんが動きました。デザイナでも開けました。  
&#8212;  
試行錯誤中の、June　CTPシリーズも覚書。  
http://www.microsoft.com/downloads/details.aspx?familyid=1A994549-94CB-4F61-903D-A8C8E453EEF4&displaylang=en  
の情報を参考にすると  
.NET Framework 3.0 (June CTP)  
http://www.microsoft.com/downloads/details.aspx?familyid=8D09697E-4868-4D8D-A4CF-9B82A2AE542D&displaylang=en  
MicrosoftR WindowsR Software Development Kit (SDK) for June CTP of Windows Vista and .NET Framework 3.0 Runtime Components (ISO)  
http://www.microsoft.com/downloads/details.aspx?familyid=D6CD6490-AF1A-48C3-AEBD-389DAF45003C&displaylang=en  
Microsoft Visual Studio Code Name “Orcas” Community Technology Preview &#8211; Development Tools for .NET Framework 3.0  
http://www.microsoft.com/downloads/details.aspx?familyid=1A994549-94CB-4F61-903D-A8C8E453EEF4&displaylang=en  
MicrosoftR Visual StudioR 2005 Extensions for WindowsR Workflow Foundation Release Candidate 2（本当は3）  
http://www.microsoft.com/downloads/details.aspx?familyid=63A80A4B-BD27-4124-A2A5-61786ADB626E&displaylang=en  
という感じで入れることになると思います。  
&#8212;  
こちらも覚書  
http://www.atmarkit.co.jp/fdotnet/special/winworkflow/winworkflow_01.html