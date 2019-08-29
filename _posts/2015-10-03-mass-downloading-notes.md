---
layout: post
title:  "Mass downloading notes"
date:   2015-10-03 11:25:00
categories: bash
---

# Open book Exams
Now that VIT has introduced open-book exams ( "open self-notes" to be more precise ) for CAT-2 ,
I needed to make notes from ( at-least ) all the material uploaded in the course page in the
Academics portal.

# The "conventional" way
The conventional way is to right-click each hyper-link and save to a location.
That is fine for one or two files but for it is really painful to manually download and rename each file.

( I forgot to mention, all files have a prefix like `FALLSEM2015-16_CP0270_15-Oct-2015_RM01`. This adds data regarding when it was uploaded etc. )

# The script
Being lazy, I hacked up bash script to do all that work for me.
It takes a file containing the course page as an html document.


Since the Academics portal is a bit old, it is built with html iframes and ajax requests, so you would not find the html source by simply using the view page source option of your browser.

However if you dig deeper and look under the hood by inspecting the requests sent and response received, or use inspect element to see the final generated document, you'll find it quite easily.

I'm putting the script here for anyone to use.

{% highlight bash %}

#!/usr/bin/env bash
#find all anchor tag urls in input file
for url in  $(grep -Po "(?<=href=')[^']*" $1)
do
    #cleaned file name
    outfile="$(echo $url | cut -d '_' -f5)"
    #fetch file
    wget $url --output-document="$outfile"
done;

{% endhighlight %}
