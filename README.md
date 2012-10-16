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
  #video.updated 			  => "16 October 2012"
  #video.category_title 	  => "News"
  #video.category_detail 	  => "News & Politics"
  #video.thumbs 			  => {
  #      			            :small => {
  #       			                :default 	=> "http://i.ytimg.com/vi/OTbddxQFOCU/default.jpg",
  #        			                :start 		=> "http://i.ytimg.com/vi/OTbddxQFOCU/1.jpg",
  #       			                :middle 	=> "http://i.ytimg.com/vi/OTbddxQFOCU/2.jpg",
  #       			                :end 		=> "http://i.ytimg.com/vi/OTbddxQFOCU/3.jpg"
  #       			            },
  #               					:medium 		=> "http://i.ytimg.com/vi/OTbddxQFOCU/mqdefault.jpg",
  #               					:large 			=> "http://i.ytimg.com/vi/OTbddxQFOCU/hqdefault.jpg"
  #                       }
  #video.author 			  => {
  #       				            :name		=> "BFMTV",
  #       				            :uri		=> "http://gdata.youtube.com/feeds/api/users/BFMTV",
  #       				            :id			=> "XwDLMDV86ldKoFVc_g8P0g"
  #       			        	}
  #video.average 			  => 4.9205164999999997
  #video.dislikes 			  => "40"
  #video.likes 			      => "1973"
  #video.raters 			  => 2013
  #video.favorite 			  => "0"
  #video.views 			      => "230931"
  #video.url 				  => {
  #       				            :default	=> "http://www.youtube.com/watch?v=OTbddxQFOCU",
  #       				            :embed		=> "http://www.youtube.com/embed/OTbddxQFOCU"
  #       				        }
  #video.embed 			      => "<iframe src=\"http://www.youtube.com/embed/OTbddxQFOCU\" frameborder=\"0\" allowfullscreen=\"allowfullscreen\"></iframe>"
  #video.valid?               => true

  video = VideoInfo.new("http://vimeo.com/31067789")

  #video.video_id  		    => "31067789"
  #video.provider			=> "Vimeo"
  #video.title			    => "Legs Of Steel - Nothing Else Matters - OFFICIAL FREE FILM"
  #video.description		=> "PRE ORDER THE 2012 Movie here: http://itunes.apple.com/us/movie/hurt-so-good/id555519375<br />rn<br />rnCHECKOUT THE 2012 TRAILER FOR \"HURT SO GOOD\" - http://www.youtube.com/watch?feature=player_embedded&v=sA3uZ0a1G-0<br />rn<br />rnCRANK UP YOUR SPEAKERS AND HIT FULL SCREEN!!!<br />rn<br />rnLegs Of Steel is proud to present their 2011 ski film \"Nothing Else Matters\" in association with Red Bull Media House, Vu00f6lkl, Marker, Oakley, Fiat Freestyle Team, Leki, Atomic and Monashee Powder Snowcats.<br />rn<br />rnFilmed, Directed and Produced by Andre Nutini<br />rn<br />rnExecutive Producers: <br />rnBene Mayr <br />rnTobi Reindl<br />rnPaddy Graham<br />rnThomas Hlawitschka<br />rn<br />rnFeatured Athletes: Tobi Reindl, Bene Mayr, Paddy Graham, Thomas Hlawitschka, Sven Kueenle, Fabio Studer, Max Hill, Lucas and Tobi Mangold, Antti Ollila, Oscar Scherlin, Lolo Favre, Elvis Harsheim, Sebi Geiger, Nico Zacek, Tobi Tritscher and Toni Hu00f6llwart. <br />rn<br />rnwww.legsofsteel.eu  - Official Legs Of Steel SHOP - www.downdays.eu/shop/legsofsteel<br />rn<br />rnCheck out these bands:<br />rnwww.totorro.bandcamp.com<br />rnhttp://prettylightsmusic.com/"
  #video.duration			=> 1591
  #video.publication		=> "25 October 2011"
  #video.thumbs			    => {
  #				    		          :small	=> "http://b.vimeocdn.com/ts/211/506/211506965_100.jpg",
  #				    		          :medium	=> "http://b.vimeocdn.com/ts/211/506/211506965_200.jpg",
  #				    		          :large	=> "http://b.vimeocdn.com/ts/211/506/211506965_640.jpg"
  #						          }
  #video.author			    => {
  #				    		        :name 	=> "Legs of Steel",
  #				    		        :uri 	=> "http://vimeo.com/legsofsteel",
  #				    		        :id 	=> 4181164,
  #				    		        :thumbs => {
  #				        		        :small 		=> "http://b.vimeocdn.com/ps/141/064/1410640_30.jpg",
  #				        		        :medium 	=> "http://b.vimeocdn.com/ps/141/064/1410640_75.jpg",
  #				        		        :large 		=> "http://b.vimeocdn.com/ps/141/064/1410640_100.jpg"
  #			    			        }
  #						        }
  #video.likes			    => 1253
  #video.url				=> {
  #				    		        :default 	=> "http://www.vimeo.com/31067789",
  #				    		        :embed 		=> "http://player.vimeo.com/video/31067789"
  #						        }
  #video.embed			    => "<iframe src=\"http://player.vimeo.com/video/31067789\" frameborder=\"0\" allowfullscreen=\"allowfullscreen\"></iframe>"
  #video.valid?             => true


  video = VideoInfo.new("http://www.dailymotion.com/video/xubxtf_felix-baumgartner-red-bull-stratos-live-jump-replay_sport")
  
  #video.video_id  		    => "xubxtf"
  #video.provider			=> "Dailymotion"
  #video.title			    => "Felix Baumgartner Red Bull Stratos Live Jump (Replay)",
  #video.description		=> "Watch the Red Bull Stratos live jump in replay by  Felix Baumgartner from space<br />Red Bull Stratos : freefall from the edge of space",
  #video.duration			=> 615
  #video.publication		=> "14 October 2012"
  #video.updated			=> 1350251396
  #video.thumbs			    => {
  #    						    :small			=> "http://static2.dmcdn.net/static/video/325/549/50945523:jpeg_preview_small.jpg?20121014234956",
  #    						    :medium		=> "http://static2.dmcdn.net/static/video/325/549/50945523:jpeg_preview_medium.jpg?20121014234956",
  #    						    :large			=> "http://static2.dmcdn.net/static/video/325/549/50945523:jpeg_preview_large.jpg?20121014234956"
  #						    }
  #video.author			    => {
  #    						    :name			=> "koreus",
  #    						    :uri			=> "http://dailymotion.com/user/koreus"
  #						    }
  #video.average			=> 4.9000000000000004
  #video.raters			    => 18
  #video.views			    => 386054
  #video.url				=> {
  #    						:default		=> "http://www.dailymotion.com/video/xubxtf",
  #    						:embed			=> "http://www.dailymotion.com/embed/video/xubxtf"
  #						    }
  #video.embed 			    => "<iframe frameborder=\"0\" width=\"480\" height=\"270\" src=\"http://www.dailymotion.com/embed/video/xubxtf\"></iframe>"
  # video.valis?            => true
 
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

[https://github.com/dotgee/video_info/contributors](https://github.com/dotgee/video_info/contributors)

