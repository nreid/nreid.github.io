---
layout: post
title: Testing code snippets. 
comments: True
---

I'm just writing this to see how code snippets work using markdown and jekyll...

Here is a simple thing I often do to summarize distributions of pieces of information from the INFO field of a vcf file...

{% highlight r %}

cl <- "tabix my.vcf.bgz Scaffold10 | grep -oP '(?<=DP=)[^;]+'"
dp <- scan(pipe(cl))
hist(dp,xlab="Depth",breaks=100)

{% endhighlight %}

Here I've extracted the contents of the tag 'DP', which contains the depth of coverage of the variant. 

In this case I'm feeding a line of code to the system, "cl", with `pipe()`, and reading the results into R with `scan()`. 

To break down "cl": I use tabix to quickly access arbitrary chunks of VCF files, then pipe the output to grep. The flag `-o` extracts the regex match, and `-P` allows me to use what's called a 'positive lookahead'. That's the section `(?<=DP=)`. This requires the regex to match "DP=", but doesn't return it as part of the match. Then I match the characters in the field with `[^;]+`, which matches one or more of any character except ";", which is the field delimiter. 

Here's the result:

![histogram](/assets/test.hist.png)