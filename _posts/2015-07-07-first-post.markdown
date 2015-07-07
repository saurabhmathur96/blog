---
layout: post
title:  "First Post"
date:   2015-07-07 18:44:43
categories: jekyll
---

#Hello, World !

Finally ! I have setup this blog using the awesome static site generator [Jekyll][jekyll]. Now I can blog like a *Hacker*.

{% highlight python %}
#Python
def say_hello(name):
  print 'Hello, '+name+' !'

#=> Prints Hello, World ! to STDOUT
say_hello('World')
{% endhighlight %}

{% highlight cpp %}
//C++
#include <iostream>
#include <string>


void say_hello(std::string name){
	std::cout << "Hello, " << name << " !";
}

int main(void){
	say_hello("World");
	return 0;
}

{% endhighlight %}


[jekyll]:      http://jekyllrb.com
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-help]: https://github.com/jekyll/jekyll-help
