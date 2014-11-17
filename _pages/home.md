---
permalink: /
layout:    default
blogfeed:  true
---

<style>
.babelfrog-demo {
  max-width: 400px;
  margin: 20px auto 10px;
  height: 240px;
  overflow: hidden;
  border: 8px solid #f0f0f0;
	border-radius: 15px;
}

.button-wrapper {
  width: 100%;
  margin: 30px 0;
  text-align: center;
}

.button, .button:hover {
  /*background-image: url('./img/icon19.png');*/
  background-image: url('http://upload.wikimedia.org/wikipedia/commons/8/87/Google_Chrome_icon_%282011%29.png');
  background-size: 19px;
  background-repeat: no-repeat;
  background-color: #6491b2;
  background-position: 10px center;
  padding: 10px 20px 10px 42px;
  border-radius: 8px;
  color: white;
  font-size: 18px;
  font-family: 'Lucida Grande', Helvetica, Arial, Sans-Serif;
  text-decoration: none;
}

h1 {
  font-weight: normal;
}

</style>


<script src="//ajax.googleapis.com/ajax/libs/jquery/1.11.1/jquery.min.js"></script>

<script type="text/javascript">
$(document).ready(function() {
  $('.cr-btn').click(function (e) {
    if(!$(this).hasClass('disabled')) {
      e.preventDefault();
      if(navigator.userAgent.toLowerCase().indexOf('chrome') > -1) {
        mixpanel.track("Start install");
        chrome.webstore.install("https://chrome.google.com/webstore/detail/jnhmkblbgggfgeebimebebnkhgnagnpj", function() {
          // success callback
          // $(".cr-btn").addClass("disabled").text('BabelFrog is already installed');

          var mixpanelTrack = new $.Deferred();
          var gaTrack = new $.Deferred();
          $.when(mixpanelTrack, gaTrack).done(function() {
            window.location.href = "/help?install=inline";
          });

          _gaq.push(['_trackEvent', 'Engagement', 'Install', 'Inline']);
          _gaq.push(function() {
            gaTrack.resolve();
          });

          mixpanel.track("Install successful", undefined, function() {
            mixpanelTrack.resolve();
          });
        });
      }
      else {
        alert("Sorry, your browser does not support installing the Chrome extension.");
      }
    }
  });
});
</script>

# Website translation that doesn't&nbsp;suck.

**BabelFrog** is a light-weight Chrome extension that helps you read foreign websites by translating the text you select, not the whole page.

<div class="babelfrog-demo"><img src="/img/babelfrog-demo-4.gif"/></div>

Start reading websites in the original language, instead of waiting for a butchered machine translation.

<div class="button-wrapper">
<a class="button cr-btn" href="https://chrome.google.com/webstore/detail/babelfrog/jnhmkblbgggfgeebimebebnkhgnagnpj">
Add BabelFrog to Chrome
</a>
</div>

Unlike similar extensions, BabelFrog isn't bloated with features. It won't slow down Chrome, or ask you for permission to steal data from every website you visit.

