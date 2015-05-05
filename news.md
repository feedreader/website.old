<!--
   to be done - cleanup and add frontmatter etc.
  -->
  
# NEWS

## Sinatra Planet Web App Powered by pluto gem - Planet Ruby, Planet vienna.rb Live Demos

Sept/25, 2013

  Added a Sinatra web app/template (pluto.live) [1] that lets you create 
  planet planet sites (that is, sites that get auto-build and auto-updated from web feed subscriptions). 

  See the Planet Ruby [2] or the Planet vienna.rb [3] for live demos.

  Cheers. Happy planet!

[1] https://github.com/feedreader/pluto.live
[2] http://plutolive.herokuapp.com
[3] viennarb.herokuapp.com


## Pluto Planet Generator Now Includes Web Admin Sinatra App - run PlutoAdmin::Server

Sept/25, 2013

 The pluto planet gem that lets you create planet sites 
 (that is, sites that get auto-build and auto-updated from web feed subscriptions) 
 now includes a web admin app that you can include in your planet. Example: 

   map '/db' { run PlutoAdmin::Server }

  See the Sinatra pluto.admin [1] web app in action, for example on Planet Ruby [2] or Planet vienna.rb [3]. 

  Cheers. Happy planet!

[1] https://github.com/feedreader/pluto.admin
[2] http://plutolive.herokuapp.com/db
[3] http://viennarb.herokuapp.com/db


## Pluto Planet Gem - New Styles / More Template Packs - Top, (River of) News, Cards, and More

Oct/19, 2013

The pluto planet generator gem that lets you build web pages from 
published web feeds now includes more template packs. You can see the 
blank (standard)[1] or top[2] or river of news[3] or card[4] template 
packs in action on Planet Vienna.rb. 

   Note: You can use the new template packs "offline"; install/update 
the template packs e.g. 

  $ pluto install blank    # includes std and cards 
  $ pluto install top 
  $ pluto install news 

  And use the --template/-t switch for new planet styles e.g. 

  $ pluto build ruby.ini --template top  or 
  $ pluto b ruby.ini -t top 

  Find out more at the project site @ github.com/feedreader   Cheers. 

[1] http://viennarb.herokuapp.com/?style=std 
[2] http://viennarb.herokuapp.com/?style=top 
[3] http://viennarb.herokuapp.com/?style=news 
[4] http://viennarb.herokuapp.com/?style=cards 

[4] http://viennarb.herokuapp.com/?style=ca 


## Using Web Feeds in Ruby (Mini-Facebook-like News Feed in 20 Lines of Ruby) and More

Nov/17, 2013

FYI: The slides from this week's Vienna.rb talk titled "Using Web 
Feeds to Build Planet Sites in Ruby." [1] Use left/right cursor keys 
(or space bar) to browse the slides. Or check the all-in-one-page 
markdown source [2]. 

 Build yourself a Mini-Facebook-like News Feed in 20 Lines of Ruby e.g. 

planet.rb: 
-------------- 

require 'open-uri' 
require 'feedutils' 
require 'erb' 

# step 1) read a list of web feeds 

FEED_URLS = [ 
  'http://vienna-rb.at/atom.xml', 
  'http://www.meetup.com/vienna-rb/events/rss/vienna.rb/', 
  'http://www.1stfloorgraphics.nl/blog/feed/', 
  'http://lab.an-ti.eu/atom.xml', 
  'http://abangratz.github.io/atom.xml' 
] 

items = [] 

FEED_URLS.each do |url| 
  feed = FeedUtils::Parser.parse( open( url ).read ) 
  items += feed.items 
end 

# step 2) mix up all postings in a new page 

FEED_ITEM_TEMPLATE = <<EOS 
<% items.each do |item| %> 
  <div class="item"> 
    <h2><a href="<%= item.url %>"><%= item.title %></a></h2> 
    <div><%= item.content %></div> 
  </div> 
<% end %> 
EOS 

puts ERB.new( FEED_ITEM_TEMPLATE ).result 

Run the script: 

$ ruby planet.rb 


 or just use the ready-to-use Pluto feed reader gem command line tool 
[3] to make it one line 

 $ pluto build newsfeed 

  Cheers. Happy Planet. 

[1] http://slideshow-s9.github.io/webfeeds.html 
[2] https://github.com/slideshow-s9/slideshow-s9.github.io/blob/master/talks/webfeeds.md 
[3] http://feedreader.github.io 



## Pluto Planet Gem - New Styles / More Template Packs - Hacker, Digest

Nov/18, 2013

The pluto planet site generator gem that lets you build web pages 
from published web feeds now includes more template packs. 

  You can see the new hacker [1] pack (inspired by Hacker News) or the 
digest [2] pack (inspired by Alterslash) in action on Planet 
Vienna.rb. 

  Cheers. Happy planet. 

[1] http://viennarb.herokuapp.com/?style=hacker 
[2] http://viennarb.herokuapp.com/?style=digest


## Q&A

Every template pack lives in its own github repo (e.g. pluto.blank, pluto.news, pluto.hacker, etc.). To customize a template pack get a copy (fork/clone/unzip) and change as needed.   Use the -c/--config path to point the pluto command line tool to your template pack root  e.g.

    $ pluto --config ~/pluto list      # e.g.  list all template packs

    $ pluto --config ~/pluto  ruby.ini  --template blank     #  e.g. use customized blank template pack

    All the best. Cheers.


## New Site / GitHub Org - Planet Templates (e.g. classic, digest, top, etc.)

Dec/8, 2014

FYI:  I moved all template packs to a new GitHub org / site, that is, planet-templates.  Why?

   The idea is to keep the planet tools (machinery) separate from the design templates. Why?  The idea is that the template packs can get used by other planet planet tools - basically the templates are just HTML or XML templates and that you do NOT need to be a Ruby coder to use or contribute or change the templates.  

   If anythings breaks while moving, please report any errors or issues. Thanks. Happy planet. Cheers. 

[1] github.com/planet-templates


## pluto Update v1.1.0 - What's News? Modul-mania - pluto-models, pluto-update, pluto-tasks, etc.

Dec/13, 2014

uploaded a new pluto version, that is, v1.1.0. What's news? 

  The pluto gem is now split up into five gems. The lineup includes: 

  - pluto [1] (former all-in-one gem; now the command line tool - 
includes sqlit3, activrecord etc. ready-to-use) 
  - pluto-models [2]  - planet schema 'n' models 
  - pluto-update [3]  - planet subscription and feed fetcher 'n' updater 
  - pluto-merge  [4] - planet generator, that is, merge 'n' manage 
planet templates 
  - pluto-tasks  [5] - planet pluto rake tasks 

   Why? The idea is to make it easier to use what you need and make it 
easier to change. As a plus 
  the command line tool, that is, pluto now includes all dependencies 
on install (sqlite3, activerecord, etc.) and is read-to-use 
"out-of-the-box". 

   If anything breaks, let us know. Happy planet. Cheers. 

[1] rubygems.org/gems/pluto 
[2] rubygems.org/gems/pluto-models 
[3] rubygems.org/gems/pluto-update 
[4] rubygems.org/gems/pluto-merge 
[5] rubygems.org/gems/pluto-tasks 


## Planet Pluto Update - Adds npm Package Support e.g. $ npm install planet-top

Dec/13, 2014

updated the pluto planet machinery. What's news? 

  Now you can use npm [1] to install planet template packs. For 
example to install the planet-top pack type: 

  $ npm install planet-top 

   No magic here. The npm package manager will download and copy the 
package to your working folder in the node_modules/ folder. 

   That's it. Now the template pack is ready to use with pluto. To check type: 

  $ pluto ls 

   Will print something like: 

Installed template packs in search path 
    [1] */*.txt 
    [2] node_modules/*/*.txt 
  include: 
         top (node_modules/planet-top/top.txt) 
         ... 

  To use the new template pack add as usual the -t/--template option e.g. 

  $ pluto build football.ini --template top 

  Note: I've published most template packs on npm. Search for 
planet-templates, pluto or similar [2]. 

  Cheers. 

[1] docs.npmjs.com 
[2] www.npmjs.com/browse/keyword/planet-templates


## Planet Pluto Tools - Feed List Converter Added - From OPML to INI (e.g. opml.xml => planet.ini)

Dec/20, 2014

Added a little script that lets you auto-convert feed 
lists in the OPML XML format to the Planet Pluto configuration format. 

  To use the new script clone the pluto.tools repo [1] and run 

  $ ruby convert_opml.rb <opml_link_here>  e.g. 

  $ ruby convert_opml.rb http://blogs.openstreetmap.org/opml.xml 

  The script will download the opml.xml document and check *all* feeds listed. 

  E.g. 

<opml version="1.1"> 
  <head> 
    <title>Blogs.OpenStreetMap.org</title> 
    <dateModified>Sat, 20 Dec 2014 16:01:49 +0000</dateModified> 
    <ownerName>Shaun McDonald</ownerName> 
    <ownerEmail>o...@example.com</ownerEmail> 
   </head> 
   <body> 
     <outline type="rss" text=""OpenStreetMap.org User's Diaries"" 
xmlUrl="http://www.openstreetmap.org/diary/rss" title="OpenStreetMap 
diary entries"/> 
     <outline type="rss" text="Abigail Brady" 
xmlUrl="http://abigailb.livejournal.com/data/rss?tag=osm" 
title="Abi"/> 
     ... 

  becomes 

title  = Blogs.OpenStreetMap.org 
author = Shaun McDonald 
email  = o...@example.com 

[openstreetmaporgusersdiaries] 
  title = OpenStreetMap.org User's Diaries 
  feed  = http://www.openstreetmap.org/diary/rss 
  link  = http://www.openstreetmap.org/diary 

[abigailbrady] 
  title = Abigail Brady 
  feed  = http://abigailb.livejournal.com/data/rss?tag=osm 
  link  = http://abigailb.livejournal.com/ 

  and so on. 


  See the example output for openstreetmap.ini [2] or mozilla.ini [3] 
in the samples folder. 

   Cheers. Happy planet. 

[1] https://github.com/feedreader/pluto.tools 
[2] https://github.com/feedreader/pluto.tools/blob/master/samples/openstreetmap.ini 
[3] https://github.com/feedreader/pluto.tools/blob/master/samples/mozilla.ini 


## jekyll-planet gem - Add Articles, Blogs to Your Site via Web Feeds (and Planet Pluto)

Dec/21, 2014

put together a little jekyll-planet gem [1] that lets you 
generate Jekyll posts for your static site using the Planet Pluto 
machinery. Now you can add articles, blog posts, etc. syndicated via 
web feed to your (static) site in three steps: 

  Step 1: Use a Planet Pluto configuration e.g. planet.ini to build 
your local planet.db SQLite feed cache. 

   $ pluto update planet.ini 

Step 2: Generate planet posts for Jekyll (from the planet.db cache) 
using the jekyll-planet Ruby script. 

   $ ruby -r 'jekyll/planet' -e 'JekyllPlanet.main' 

  Step 3: Use Jekyll as usual to build your site. 

   $ jekyll build 

   That's it. Happy Planet. Cheers. 

PS: Interested in all things Jekyll?  I've started putting together 
Planet Jekyll [2] running on Heroku [3]. You're welcome to add any 
Jekyll-related feeds. 

[1] github.com/feedreader/jekyll-planet  - Ruby Gem 
[2] github.com/feedreader/planet-jekyll  - (Planet Jekyll Config e.g. 
jekyll.ini) 
[3] planetjekyll.herokuapp.com  - Live Planet Jekyll Site 


## Planet Ruby - All the News About Ruby, JRuby, Rubinius, Rails, etc. - New Feeds Welcome

Dec/26, 2014

setup (another) Planet Ruby [1] - a public news site (feed 
reader/aggregator) for Ruby. 

  The planet subscriptions (feed lists) are split into seven sections 
(sub planets), that is, 

  - Planet Ruby  - Blog Postings, Articles, etc. 
  - Planet Ruby News - Official Ruby, JRuby, Rubinius, Rubygems, Rails News 
  - Planet Ruby Events  - Meetups, Workshops, Conferences 
  - Planet Jekyll -  The Static Site Generator in Ruby 
  - Planet Ruby Gems  - Version Releases, Discussions 
  - Planet Ruby Podcasts  - Radio Shows 
  - Planet Ruby Meta   - Updates about Planet Ruby and Planet Pluto 

  The planet feed list is a plain text file on GitHub, that is, ruby.ini [2]. 
 You're welcome to add new feeds or suggest new (sub) planet sites. 
 Planet Ruby itself is powered by the pluto gem. [3] 
  Cheers. Happy Planet. 

[1] planetruby.herokuapp.com 
[2] github.com/feedreader/planet-ruby 
[3] rubygems.org/gems/pluto 


## Pluto Live Update - Welcomes Planet Open Data (includes ODI, OSM, OKFN, CKAN n Friends)

Mar/3, 2014

added a new planet to the pluto live demo. Welcome Planet 
Open Data!  News sources include: 

  - Open Data Institue (ODI) News 
  - Open Street Map (OSM) News 
  - Open Knowledge Foundation (OKFN) News 
  - Wikidata News 
  - Open Wine & Winery Database (wine.db) n Friends 
  - Open Sports Database n Friends (sport.db, football.db, etc.) 
  - DBpedia News 
  - Stack Exchange Open Data Questions 
  - And many more 

  See plutolive.herokuapp.com/opendata?style=top 

   Cheers. 


## New Planet Template Packs - Forty and Paper ++ Added (Static) Theme/Template Gallery

Jan/3, 2015

Added two new planet template/theme packs, that is, 

  - Forty [1] - inspired by Twitter - the name forty is a reference to 
the one hundred forty short message limit 
  - Paper [2] - inspired by white paper ;-) 

   You can see some examples in the new (static) theme/template gallery. [3][4] 

 Happy Planet. Happy New Year. Cheers. Prosit 2015. 

[1] github.com/planet-templates/planet-forty 
[2] github.com/planet-templates/planet-paper 
[3] feedreader.github.io/gallery/opendata.forty.html 
[4] feedreader.github.io/gallery/opendata.paper.html 


## New Page - Planet Template Gallery - Incl. Live Demos (Cards, Digest, Hacker, etc.)

Jan/7, 2015

Added a new gallery page [1] that lists all planet 
template/theme packs with live demos. Template/theme packs include: 

  - Blank, Cards, Digest, Hacker, Forty, News, Paper, Top 

  Happy planet. Cheers. 

[1] planet-templates.github.io/gallery 


## New Web Feed Libraries - feedparser and feedfilter gems

Jan/8, 2015

uploaded two new feed tool gems, that is, feedparser [1] 
and feedfilter [2]. 

  What's feedparser? 

  The feedparser gem is (yet) another gem that tries to "normalize" 
web feeds in RSS 2.0 and Atom flavors offering two "normalized" Ruby 
classes, that is, Feed and Item  (plus the mapping in builders, that 
is, RssFeedBuilder and AtomFeedBuilder). 


  What's feedfilter? 

  The feedfilter gem collects filters for feeds e.g. using strip_ads 
lets you strip feedflare ads or feedburner bags and so on using 
(builtin) text patterns (regexes) e.g. 

   %r{ 
     <div[^>]*? 
        class=("|')feedflare\1 
        [^>]*?> 
          .*? 
     <\/div> 
       }mix 


  Both gems get used by the planet pluto machinery that runs, for 
example, Planet Ruby [3]. 

   Cheers. 

[1] github.com/feedreader/feed.parser 
[2] github.com/feedreader/feed.filter 
[3] planetruby.herokuapp.com 
