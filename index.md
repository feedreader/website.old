---
layout: default
title: Welcome
---

# {{ page.title }}

<div class="toc" markdown="1">
Contents:

* [What's Pluto?](#whatis)
* [Getting Started](#start)
* [Planet Configuration Sample](#config)
* [About, License](#about)
* [Questions? Comments?](#questions)
</div>


## What's Pluto?   {#whatis}

A planet site generator in ruby that lets you build web pages from published web feeds.


## Getting Started    {#start}

Use the `pluto` command line tool and pass in one or more planet configuration files.
Example:

~~~
$ pluto build ruby.ini       or
$ pluto b ruby
~~~

This will

1) fetch all feeds listed in `ruby.ini` and 

2) store all entries in a local database, that is, `ruby.db` in your working folder and

3) generate a planet web page, that is, `ruby.html` using the [`blank` template pack](https://github.com/planet-templates/planet-blank) in your working folder using all feed entries from the local database.

Open up `ruby.html` to see your planet web page. Voila!


![](i/pluto.png)


### Bonus: Try some different templates/theme packs

- Blank - default templates; [more »](https://github.com/planet-templates/planet-blank)
- News - 'river of news' style templates; [more »](https://github.com/planet-templates/planet-news)
- Top -  Popurl-style templates; [more »](https://github.com/planet-templates/planet-top)
- Classic -  Planet Planet-Style templates; [more »](https://github.com/planet-templates/planet-classic)


## Planet Configuration Sample   {#config}

`ruby.ini`:

~~~
title = Planet Ruby

[rubylang]
  title = Ruby Lang News
  link  = http://www.ruby-lang.org/en/news
  feed  = http://www.ruby-lang.org/en/feeds/news.rss

[rubyonrails]
  title = Ruby on Rails News
  link  = http://weblog.rubyonrails.org
  feed  = http://weblog.rubyonrails.org/feed/atom.xml

[viennarb]
  title = Vienna.rb News
  link  = http://vienna-rb.at
  feed  = http://vienna-rb.at/atom.xml

~~~

For more samples, see
[`nytimes.ini`](https://github.com/feedreader/planets/blob/master/nytimes.ini),
[`js.ini`](https://github.com/feedreader/planet-web/blob/master/js.ini),
[`dart.ini`](https://github.com/feedreader/planet-web/blob/master/dart.ini),
[`haskell.ini`](https://github.com/feedreader/planets/blob/master/haskell.ini).


## Real World Usage - Live Demos

See the [Planetarium](https://github.com/feedreader/planets) for live planets.


## About, License   {#about}

Gerald Bauer and contributors designed and developed the `pluto` gem.
See the change log for contributions and credits.

License. The pluto scripts and templates are dedicated to the public domain.
Use it as you please with no restrictions whatsoever.

{% include questions.md %}
