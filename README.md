VideoInfo [![Build Status](https://secure.travis-ci.org/thibaudgg/video_info.png?branch=master)](http://travis-ci.org/thibaudgg/video_info)
=========

Small Ruby Gem to get video info from youtube and vimeo url.
Tested against Ruby 1.8.7, 1.9.2, REE and the latest versions of JRuby & Rubinius.

Install
--------

``` bash
  gem install video_info
```

Usage
-----

``` ruby
  video = VideoInfo.new("http://www.youtube.com/watch?v=OTbddxQFOCU&feature=g-all-xit")
  
  #video.video_id   		  => "OTbddxQFOCU"
  #video.provider 			  => "Youtube"
  #video.title 			      => "Félix Baumgartner a sauté de plus de 38.000 mètres"
  #video.description 		  => "Toute l'actualité sur http://www.bfmtv.com/ Le parachutiste autrichien Felix Baumgartner a sauté dimanche d'une altitude de 39.000 mètres dans le ciel du Nouveau-Mexique pour tenter de franchir le mur du son en chute libre. Une première."
  #video.duration 			  => "831"
  #video.publication 		  => "14 October 2012"
  #video.updated 			    => "16 October 2012"
  #video.category_title 	=> "News"
  #video.category_detail 	=> "News & Politics"
  #video.thumbs 			    => {
  #      			            :small => {
  #       			                :default 	=> "http://i.ytimg.com/vi/OTbddxQFOCU/default.jpg",
  #        			                :start 		=> "http://i.ytimg.com/vi/OTbddxQFOCU/1.jpg",
  #       			                :middle 	=> "http://i.ytimg.com/vi/OTbddxQFOCU/2.jpg",
  #       			                :end 		=> "http://i.ytimg.com/vi/OTbddxQFOCU/3.jpg"
  #       			            },
  #               					:medium 		=> "http://i.ytimg.com/vi/OTbddxQFOCU/mqdefault.jpg",
  #               					:large 			=> "http://i.ytimg.com/vi/OTbddxQFOCU/hqdefault.jpg"
  #                       }
  #video.author 			    => {
  #       				            :name		=> "BFMTV",
  #       				            :uri		=> "http://gdata.youtube.com/feeds/api/users/BFMTV",
  #       				            :id			=> "XwDLMDV86ldKoFVc_g8P0g"
  #       			        	}
  #video.average 			    => 4.9205164999999997
  #video.dislikes 			  => "40"
  #video.likes 			      => "1973"
  #video.raters 			    => 2013
  #video.favorite 			  => "0"
  #video.views 			      => "230931"
  #video.url 				      => {
  #       				            :default	=> "http://www.youtube.com/watch?v=OTbddxQFOCU",
  #       				            :embed		=> "http://www.youtube.com/embed/OTbddxQFOCU"
  #       				        }
  #video.embed 			      => "<iframe src=\"http://www.youtube.com/embed/OTbddxQFOCU\" frameborder=\"0\" allowfullscreen=\"allowfullscreen\"></iframe>"

  video = VideoInfo.new("http://vimeo.com/898029")

  # video.video_id         => "898029"
  # video.provider         => "Vimeo"
  # video.title            => "Cherry Bloom - King Of The Knife"
  # video.description      => "The first video from the upcoming album Secret Sounds, to download in-stores April 14. Checkout http://www.cherrybloom.net"
  # video.keywords         => "alternative, bloom, cherry, clip, drum, guitar, king, knife, of, Paris-Forum, rock, the, tremplin"
  # video.duration         => 175 (in seconds)
  # video.date             => Mon Apr 14 13:10:39 +0200 2008
  # video.width            => 640
  # video.height           => 360
  # video.thumbnail_small  => "http://ts.vimeo.com.s3.amazonaws.com/343/731/34373130_100.jpg"
  # video.thumbnail_large  => "http://ts.vimeo.com.s3.amazonaws.com/343/731/34373130_640.jpg"
  # video.embed_url        => "http://player.vimeo.com/video/898029"
  # video.embed_code       => "'<iframe src="http://player.vimeo.com/video/898029?title=0&amp;byline=0&amp;portrait=0&amp;autoplay=0" frameborder="0"></iframe>'"

  video = VideoInfo.new("http://badurl.com/898029")

  # video.valid? => false
```

Options
-------

``` ruby
  video = VideoInfo.new("http://www.youtube.com/watch?v=mZqGqE0D0n4", "User-Agent" => "My Youtube Mashup Robot/1.0")
  video = VideoInfo.new("http://www.youtube.com/watch?v=mZqGqE0D0n4", "Referer"    => "http://my-youtube-mashup.com/")
  video = VideoInfo.new("http://www.youtube.com/watch?v=mZqGqE0D0n4", "Referer"    => "http://my-youtube-mashup.com/",
                                                                      "User-Agent" => "My Youtube Mashup Robot/1.0")
```
You can also use **symbols** instead of strings (any non-word (`/[^a-z]/i`) character would be converted to hyphen).

``` ruby
  video = VideoInfo.new("http://www.youtube.com/watch?v=mZqGqE0D0n4", :referer    => "http://my-youtube-mashup.com/",
                                                                      :user_agent => "My Youtube Mashup Robot/1.0")
```

User-Agent when empty defaults to "VideoInfo/VERSION" - where version is current VideoInfo version, e.g. **"VideoInfo/0.2.7"**.

It supports all openURI header fields (options), for more information see: [openURI DOCS](http://www.ruby-doc.org/stdlib-1.9.3/libdoc/open-uri/rdoc/OpenURI.html)

You can also include an `iframe_attributes` hash to include arbitrary attributes in the iframe embed code:

``` ruby
VideoInfo.new("http://www.youtube.com/watch?v=mZqGqE0D0n4", :iframe_attributes => { :width => 800, :height => 600, "data-key" => "value" } ).embed_code
=> '<iframe src="http://www.youtube.com/embed/mZqGqE0D0n4" frameborder="0" allowfullscreen="allowfullscreen" width="800" height="600" data-key="value"></iframe>'
```

Author
------

[Thibaud Guillaume-Gentil](https://github.com/thibaudgg) ([@thibaudgg](http://twitter.com/thibaudgg))

Contributors
------------

[https://github.com/thibaudgg/video_info/contributors](https://github.com/thibaudgg/video_info/contributors)

