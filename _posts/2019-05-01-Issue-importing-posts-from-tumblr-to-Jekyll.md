---
layout: post
title: Issue importing posts from tumblr to Jekyll
---


Quite a few people seem to be moving from Tumblr to Jekyll installations. There is an  [official importer](https://import.jekyllrb.com/docs/tumblr/),
and there are some good guides out there - for example:
[How to export and rehost your Tumblr site · GitHub](https://gist.github.com/ndarville/5f8a7fb93191801de460c5ebe21cc9d4)

I experienced a couple of issues trying this, so here are the fixes I found:

## Jekyll-importer failed to install

I noted an issue where Jekyll-importer failed to install. Looking at the output it appeared to be failing while trying to install nokogiri

A search on stackoverflow reveals this is an issue with needing to tell it to use the libxml2 from xcode

[nokogiri gem installation error - Stack Overflow](https://stackoverflow.com/questions/24251494/nokogiri-gem-installation-error)

`gem install nokogiri -- --use-system-libraries=true --with-xml2-include=/Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX10.13.sdk/usr/include/libxml2/`

Installing  nokogiri first with the stackoverflow arguments was successful, and then Jekyll-importer installed straightforwardly


## Problems getting past GPDR page

Then there was an issue with tumblr's GPDR page.
This could be resolved by manually editing a few lines in one of the files (tumblr.rb) - hopefully the change will be included in a forthcoming version by default:

[Comparing jekyll:master...lambada:fix-tumblr-gdpr · jekyll/jekyll-import · GitHub](https://github.com/jekyll/jekyll-import/compare/master...lambada:fix-tumblr-gdpr)

To get spotlight to find the file that needs editing, you need to ask it to return system files also.



