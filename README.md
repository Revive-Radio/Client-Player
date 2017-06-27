![Logo](http://i.imgur.com/hOqH6iF.png)
# Client Player 101
Revision | 1.0.0
------------ | -------------
Author | Jeff

## SO YOU WANT TO ADD THE RADIO TO YOUR SITE BRAH?!
Have no fear! This guide will explain how to add this radio to your client.

### Head
Add this before the closing head (\head) tag 
```
<!-- Revive Radio's CSS -->
<link rel="stylesheet" type="text/css" href="http://reviveradio.uk/player/player.css"/>
<link rel="stylesheet" type="text/css" href="http://reviveradio.uk/player/venobox.css"/>
<link rel="stylesheet" type="text/css" href="http://reviveradio.uk/player/reset.css">
<link rel="stylesheet" type="text/css" href="http://reviveradio.uk/player/style.css">
<link rel="stylesheet" type="text/css" href="http://reviveradio.uk/player/tipped.css">
```

### Inside the Client
Inside the Div which belongs to the Client, add this:

```
<div class="playerbox">
  <div id="radioPlayer">
    <div id="playerdiv">
      <audio type="audio/mpeg" id="streamPlayer"></audio>
      <a onclick="javascript:toggleRadio();" href="#"><img id="toggler" src="img/play.png"></img></a>
      <input id="volume" min="0.0" max="1.0" step="0.01" type="range" ondrag=""/>
    </div>
    <!--JavaScript Code -->
    <script type="text/javascript">
    var stream = document.getElementById("streamPlayer");
    var toggler = document.getElementById("toggler");
    var volume = document.getElementById("volume");

	window.onload = function(){
		toggler.src = "http://reviveradio.uk/player/img/play.png";
		stream.volume = "0.5";
		toggleRadio();
	};
	
    function toggleRadio() {
        if (stream.paused) {
			if (stream.src != "http://titan.shoutca.st:8338/stream ") {	
				stream.src = "http://titan.shoutca.st:8338/stream ";
			}
			
            stream.play();
            toggler.src = "http://reviveradio.uk/player/img/pause.png";
        } else {
            stream.pause();
            toggler.src = "http://reviveradio.uk/player/img/play.png";
        }
    }

    volume.oninput = function() {
        if (stream.paused) {
			if (stream.src != "http://titan.shoutca.st:8338/stream ") {	
				stream.src = "http://titan.shoutca.st:8338/stream ";
			}
			
			stream.play();
            toggler.src = "http://reviveradio.uk/player/img/play.png";
        }

        stream.volume = volume.value;
    };
</script>
  </div>
  <div id="area_player">
     <div class="inforoom"><span id="cc_strinfo_title_kraig" class="cc_streaminfo"></span></div>
			<div class="playermusic"><marquee><span id="cc_strinfo_song_kraig" class="cc_streaminfo"></span></marquee></div>
			<div class="playerlisteners"><span id="cc_strinfo_listeners_kraig" class="cc_streaminfo"></span></div>
    </div>
</div>
```

## Footer Things
We need to add all the Javascript files, so add that before the end of the body tag!

```
<script src="http://reviveradio.uk/player/Js/JQuery.js"></script>
<script src="http://reviveradio.uk/player/js/JQuery-UI.js"></script>
<script src="http://reviveradio.uk/player/js/venobox.js"></script>
<script language="javascript" type="text/javascript" src="https://titan.shoutca.st/system/streaminfo.js"></script>
```
