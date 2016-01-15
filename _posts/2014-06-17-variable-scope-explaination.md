---
id: 715
title: Variable Scope Explaination
date: 2014-06-17T08:31:31+00:00
author: Rolando Islas
layout: post
guid: http://rolandoislas.com/blog/?p=715
permalink: /variable-scope-explaination/
dsq_thread_id:
  - 2772456382
categories:
  - Random
tags:
  - Java
  - pseudocode
  - variable
  - Visual Basic
---
When you begin learning to program, the variable scope might not be important to you. You might not even be aware of it, but as you progress you may realize that at some point you&#8217;ll need to know how it works. I will try to explain it the best that I can while using pseudocode examples for clarity.<!--more-->


  
If you started programming without the use of modules (methods/functions) you&#8217;ll probably be the most familiar with this type of code:

<pre class="brush: plain; title: ; notranslate" title="">Module main()
    string someVariable = "Hello!"
    Display someVariable
End Module
</pre>

Here we don&#8217;t have to worry about the variable scope because all our variables are in one function. Let&#8217;s add another function:

<pre class="brush: plain; title: ; notranslate" title="">Module main()
    string someVariable = "Hello!"
    setVariable()
    Display someVariable
End Module
 
Module setVariable()
    string someVariable = "No hello for you!"
End Module
</pre>

Now you may be thinking the user will be presented with &#8220;No hello for you!&#8221;, but they infact get &#8220;Hello!&#8221;. What? But the setVariable() function set our variable &#8220;someVariable&#8221; to a different string. How could it retain the older string? Well, the setVariable() function set a new variable with the name &#8220;someVariable&#8221; to that string. this variable is only visible to that function. The &#8220;someVaraible&#8221; variable from the main function is also only visible to the code within the main function, so setVariable would not be able to set it anyway. Let&#8217;s correct this code:

<pre class="brush: plain; title: ; notranslate" title="">Module main()
    string someVariable = "Hello!"
    someVariable = setVariable()
    Display someVariable
End Module
 
Module setVariable()
    string someVariable = "No hello for you!"
    return someVariable
End Module
</pre>

Now we are overwriting &#8220;someVariable&#8221; with the return value of setVariable(). What if you want a variable that can be seen from both of these function? That looks like this:

<pre class="brush: plain; title: ; notranslate" title="">string someVariable
 
Module main()
    someVariable = "Hello!"
    setVariable()
    Display someVariable
End Module
 
Module setVariable()
    someVariable = "No hello for you!"
End Module
</pre>

What happened to the return statement? It is no longer needed. We could have kept the return statement and continued to overwrite &#8220;someVariable&#8221; in main(), but since the variable is visible to both functions we can just set the value of it directly in setVariable().

Note: this variable would be visible to all the functions in the within the class it is declared.

Here is the end result:

<pre class="brush: vb; collapse: true; light: false; title: Visual Basic; toolbar: true; notranslate" title="Visual Basic">Module Module1
 
    Dim someVariable As String
 
    Sub Main()
        someVariable = "Hello!"
        setVariable()
        Console.WriteLine(someVariable)
    End Sub
 
    Sub setVariable()
        someVariable = "No hello for you!"
    End Sub
 
End Module
</pre>

<pre class="brush: java; collapse: true; light: false; title: Java; toolbar: true; notranslate" title="Java">public class someClass {
 
    private String someVariable;
 
    public someClass() {
        someVariable = "Hello!"
        setVariable()
        System.out.println(someVariable)
    }
 
    private void setVariable() {
        someVariable = "No hello for you!"
    }
 
}
</pre>