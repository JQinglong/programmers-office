---
title: WFSamplesの歩き方(4)：WorkflowWithParameters
type: post
date: 2006-09-03T04:13:18+00:00
archives:
    - 2006
url: /wfsamplesの歩き方4：workflowwithparameters/
post_views_count:
  - 102

---
前回の続きのようになりますが、「WorkflowWithParameters」。  
WFSamples\Technologies\BasicWorkflows\WorkflowWithParameters

条件判断で使う値をパラメタとして渡したいと言う場合に、CreateWorkflowメソッドに名前付き引数を渡すことができますと。

&#8216; Set up the parameters  
&#8216; &#8220;amount&#8221; is an &#8220;in&#8221; parameter and specifics the order amount  
&#8216; if the amount is < 500 the status will be &#8220;approved&#8221; &#8220;rejected&#8221; otherwise  
Dim parameters As Dictionary(Of String, Object) = New Dictionary(Of String, Object)()  
parameters.Add(&#8220;Amount&#8221;, Convert.ToInt32(args(0), CultureInfo.InvariantCulture)) 

&#8216; Get the workflow type  
Dim type As Type = GetType(SequentialWorkflow) 

&#8216; Create and start an instance of the workflow  
currentWorkflowRuntime.CreateWorkflow(type, parameters).Start() 

こんな感じで、ワークフローが持っている「Amount」プロパティに値がセットされているのと同様になると言う感じです。Genericってまだあまりよく分かっていないんですよね。使えそうな雰囲気は伝わってきました。