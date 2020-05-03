---
layout: post
title: "Everything you need to know about Shellshock"
author: Keshiba
featured: true
---

![Shellcode Image](/assets/img/posts/shellshock.jpg)

*Shellshock*, also known as Bashdoor, is a family of security bugs in the Unix Bash shell, the first of which was disclosed on 24 September 2014. Shellshock could enable an attacker to cause Bash to execute arbitrary commands and gain unauthorized access to many Internet-facing services, such as web servers, that use Bash to process requests.

## Initial report (CVE-2014-6271)

This original form of the vulnerability ([CVE-2014-6271][LINK-CVE-2014-6271]) involves a specially crafted environment variable containing an exported function definition, followed by arbitrary commands. Bash incorrectly executes the trailing commands when it imports the function. The vulnerability can be tested with the following command:

{% highlight bash %}
env x='() { :;}; echo vulnerable' bash -c "echo this is a test"
{% endhighlight %}

In systems affected by the vulnerability, the above commands will display the word "vulnerable" as a result of Bash executing the command "echo vulnerable", which was embedded into the specially crafted environment variable named "x".


### CGI-based web server

When a web server uses the Common Gateway Interface (CGI) to handle a document request, it copies certain information from the request into the environment variable list and then delegates the request to a handler program. If the handler is a Bash script, or if it executes one for example using the system(3) call, Bash will receive the environment variables passed by the server and will process them as described above. This provides a means for an attacker to trigger the Shellshock vulnerability with a specially crafted document request.
Security documentation for the widely used Apache web server states: "CGI scripts can ... be extremely dangerous if they are not carefully checked," and other methods of handling web server requests are typically used instead. There are a number of online services which attempt to test the vulnerability against web servers exposed to the Internet

[LINK-CVE-2014-6271]: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2014-6271