---
layout: post
title:  "Custom Exceptions in PowerShell"
date:   2021-06-27 14:27:19 -0500
categories: jekyll update
---

Here is an example how to create and use custom exceptions in PowerShell. Custom exceptions provide great flexibility by being able to seperate different types for your catch statements.

#### Create & Override Constructor:
{% highlight powershell %}
class CustomException: System.Exception {
    CustomException([string] $x) :
        base ("This is a custom exception for: $x") {}
}
{% endhighlight %}

#### Use:
{% highlight powershell %}
throw [CustomException] $x

# need to use 'new' static method if 2 parameters
throw [CustomException2]::New($x, $y)

# catching errors
try {
    Invoke-Func 
} catch [CustomException1] {
    # handle errors
} catch [CustomException2] {
   # handle errors
}
{% endhighlight %}

