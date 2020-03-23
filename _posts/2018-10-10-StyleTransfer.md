---
title: "Perceptron"
date: 2015-07-25
tags: [data science, style transfer, computer vision]
header:
  image: "/images/perceptron/header_perceptron.jpeg"
excerpt: "Data Science, Style Transfer, Computer Vision"
---

<!DOCTYPE html>
<html>
<head><meta charset="utf-8" />

<title>artisticpoca</title>

<script src="https://cdnjs.cloudflare.com/ajax/libs/require.js/2.1.10/require.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/2.0.3/jquery.min.js"></script>



<style type="text/css">
    /*!
*
* Twitter Bootstrap
*
*/
/*!
 * Bootstrap v3.3.7 (http://getbootstrap.com)
 * Copyright 2011-2016 Twitter, Inc.
 * Licensed under MIT (https://github.com/twbs/bootstrap/blob/master/LICENSE)
 */
/*! normalize.css v3.0.3 | MIT License | github.com/necolas/normalize.css */
html {
  font-family: sans-serif;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
}
body {
  margin: 0;
}
article,
aside,
details,
figcaption,
figure,
footer,
header,
hgroup,
main,
menu,
nav,
section,
summary {
  display: block;
}
audio,
canvas,
progress,
video {
  display: inline-block;
  vertical-align: baseline;
}
audio:not([controls]) {
  display: none;
  height: 0;
}
[hidden],
template {
  display: none;
}
a {
  background-color: transparent;
}
a:active,
a:hover {
  outline: 0;
}
abbr[title] {
  border-bottom: 1px dotted;
}
b,
strong {
  font-weight: bold;
}
dfn {
  font-style: italic;
}
h1 {
  font-size: 2em;
  margin: 0.67em 0;
}
mark {
  background: #ff0;
  color: #000;
}
small {
  font-size: 80%;
}
sub,
sup {
  font-size: 75%;
  line-height: 0;
  position: relative;
  vertical-align: baseline;
}
sup {
  top: -0.5em;
}
sub {
  bottom: -0.25em;
}
img {
  border: 0;
}
svg:not(:root) {
  overflow: hidden;
}
figure {
  margin: 1em 40px;
}
hr {
  box-sizing: content-box;
  height: 0;
}
pre {
  overflow: auto;
}
code,
kbd,
pre,
samp {
  font-family: monospace, monospace;
  font-size: 1em;
}
button,
input,
optgroup,
select,
textarea {
  color: inherit;
  font: inherit;
  margin: 0;
}
button {
  overflow: visible;
}
button,
select {
  text-transform: none;
}
button,
html input[type="button"],
input[type="reset"],
input[type="submit"] {
  -webkit-appearance: button;
  cursor: pointer;
}
button[disabled],
html input[disabled] {
  cursor: default;
}
button::-moz-focus-inner,
input::-moz-focus-inner {
  border: 0;
  padding: 0;
}
input {
  line-height: normal;
}
input[type="checkbox"],
input[type="radio"] {
  box-sizing: border-box;
  padding: 0;
}
input[type="number"]::-webkit-inner-spin-button,
input[type="number"]::-webkit-outer-spin-button {
  height: auto;
}
input[type="search"] {
  -webkit-appearance: textfield;
  box-sizing: content-box;
}
input[type="search"]::-webkit-search-cancel-button,
input[type="search"]::-webkit-search-decoration {
  -webkit-appearance: none;
}
fieldset {
  border: 1px solid #c0c0c0;
  margin: 0 2px;
  padding: 0.35em 0.625em 0.75em;
}
legend {
  border: 0;
  padding: 0;
}
textarea {
  overflow: auto;
}
optgroup {
  font-weight: bold;
}
table {
  border-collapse: collapse;
  border-spacing: 0;
}
td,
th {
  padding: 0;
}
/*! Source: https://github.com/h5bp/html5-boilerplate/blob/master/src/css/main.css */
@media print {
  *,
  *:before,
  *:after {
    background: transparent !important;
    box-shadow: none !important;
    text-shadow: none !important;
  }
  a,
  a:visited {
    text-decoration: underline;
  }
  a[href]:after {
    content: " (" attr(href) ")";
  }
  abbr[title]:after {
    content: " (" attr(title) ")";
  }
  a[href^="#"]:after,
  a[href^="javascript:"]:after {
    content: "";
  }
  pre,
  blockquote {
    border: 1px solid #999;
    page-break-inside: avoid;
  }
  thead {
    display: table-header-group;
  }
  tr,
  img {
    page-break-inside: avoid;
  }
  img {
    max-width: 100% !important;
  }
  p,
  h2,
  h3 {
    orphans: 3;
    widows: 3;
  }
  h2,
  h3 {
    page-break-after: avoid;
  }
  .navbar {
    display: none;
  }
  .btn > .caret,
  .dropup > .btn > .caret {
    border-top-color: #000 !important;
  }
  .label {
    border: 1px solid #000;
  }
  .table {
    border-collapse: collapse !important;
  }
  .table td,
  .table th {
    background-color: #fff !important;
  }
  .table-bordered th,
  .table-bordered td {
    border: 1px solid #ddd !important;
  }
}
@font-face {
  font-family: 'Glyphicons Halflings';
  src: url('../components/bootstrap/fonts/glyphicons-halflings-regular.eot');
  src: url('../components/bootstrap/fonts/glyphicons-halflings-regular.eot?#iefix') format('embedded-opentype'), url('../components/bootstrap/fonts/glyphicons-halflings-regular.woff2') format('woff2'), url('../components/bootstrap/fonts/glyphicons-halflings-regular.woff') format('woff'), url('../components/bootstrap/fonts/glyphicons-halflings-regular.ttf') format('truetype'), url('../components/bootstrap/fonts/glyphicons-halflings-regular.svg#glyphicons_halflingsregular') format('svg');
}
.glyphicon {
  position: relative;
  top: 1px;
  display: inline-block;
  font-family: 'Glyphicons Halflings';
  font-style: normal;
  font-weight: normal;
  line-height: 1;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
.glyphicon-asterisk:before {
  content: "\002a";
}
.glyphicon-plus:before {
  content: "\002b";
}
.glyphicon-euro:before,
.glyphicon-eur:before {
  content: "\20ac";
}
.glyphicon-minus:before {
  content: "\2212";
}
.glyphicon-cloud:before {
  content: "\2601";
}
.glyphicon-envelope:before {
  content: "\2709";
}
.glyphicon-pencil:before {
  content: "\270f";
}
.glyphicon-glass:before {
  content: "\e001";
}
.glyphicon-music:before {
  content: "\e002";
}
.glyphicon-search:before {
  content: "\e003";
}
.glyphicon-heart:before {
  content: "\e005";
}
.glyphicon-star:before {
  content: "\e006";
}
.glyphicon-star-empty:before {
  content: "\e007";
}
.glyphicon-user:before {
  content: "\e008";
}
.glyphicon-film:before {
  content: "\e009";
}
.glyphicon-th-large:before {
  content: "\e010";
}
.glyphicon-th:before {
  content: "\e011";
}
.glyphicon-th-list:before {
  content: "\e012";
}
.glyphicon-ok:before {
  content: "\e013";
}
.glyphicon-remove:before {
  content: "\e014";
}
.glyphicon-zoom-in:before {
  content: "\e015";
}
.glyphicon-zoom-out:before {
  content: "\e016";
}
.glyphicon-off:before {
  content: "\e017";
}
.glyphicon-signal:before {
  content: "\e018";
}
.glyphicon-cog:before {
  content: "\e019";
}
.glyphicon-trash:before {
  content: "\e020";
}
.glyphicon-home:before {
  content: "\e021";
}
.glyphicon-file:before {
  content: "\e022";
}
.glyphicon-time:before {
  content: "\e023";
}
.glyphicon-road:before {
  content: "\e024";
}
.glyphicon-download-alt:before {
  content: "\e025";
}
.glyphicon-download:before {
  content: "\e026";
}
.glyphicon-upload:before {
  content: "\e027";
}
.glyphicon-inbox:before {
  content: "\e028";
}
.glyphicon-play-circle:before {
  content: "\e029";
}
.glyphicon-repeat:before {
  content: "\e030";
}
.glyphicon-refresh:before {
  content: "\e031";
}
.glyphicon-list-alt:before {
  content: "\e032";
}
.glyphicon-lock:before {
  content: "\e033";
}
.glyphicon-flag:before {
  content: "\e034";
}
.glyphicon-headphones:before {
  content: "\e035";
}
.glyphicon-volume-off:before {
  content: "\e036";
}
.glyphicon-volume-down:before {
  content: "\e037";
}
.glyphicon-volume-up:before {
  content: "\e038";
}
.glyphicon-qrcode:before {
  content: "\e039";
}
.glyphicon-barcode:before {
  content: "\e040";
}
.glyphicon-tag:before {
  content: "\e041";
}
.glyphicon-tags:before {
  content: "\e042";
}
.glyphicon-book:before {
  content: "\e043";
}
.glyphicon-bookmark:before {
  content: "\e044";
}
.glyphicon-print:before {
  content: "\e045";
}
.glyphicon-camera:before {
  content: "\e046";
}
.glyphicon-font:before {
  content: "\e047";
}
.glyphicon-bold:before {
  content: "\e048";
}
.glyphicon-italic:before {
  content: "\e049";
}
.glyphicon-text-height:before {
  content: "\e050";
}
.glyphicon-text-width:before {
  content: "\e051";
}
.glyphicon-align-left:before {
  content: "\e052";
}
.glyphicon-align-center:before {
  content: "\e053";
}
.glyphicon-align-right:before {
  content: "\e054";
}
.glyphicon-align-justify:before {
  content: "\e055";
}
.glyphicon-list:before {
  content: "\e056";
}
.glyphicon-indent-left:before {
  content: "\e057";
}
.glyphicon-indent-right:before {
  content: "\e058";
}
.glyphicon-facetime-video:before {
  content: "\e059";
}
.glyphicon-picture:before {
  content: "\e060";
}
.glyphicon-map-marker:before {
  content: "\e062";
}
.glyphicon-adjust:before {
  content: "\e063";
}
.glyphicon-tint:before {
  content: "\e064";
}
.glyphicon-edit:before {
  content: "\e065";
}
.glyphicon-share:before {
  content: "\e066";
}
.glyphicon-check:before {
  content: "\e067";
}
.glyphicon-move:before {
  content: "\e068";
}
.glyphicon-step-backward:before {
  content: "\e069";
}
.glyphicon-fast-backward:before {
  content: "\e070";
}
.glyphicon-backward:before {
  content: "\e071";
}
.glyphicon-play:before {
  content: "\e072";
}
.glyphicon-pause:before {
  content: "\e073";
}
.glyphicon-stop:before {
  content: "\e074";
}
.glyphicon-forward:before {
  content: "\e075";
}
.glyphicon-fast-forward:before {
  content: "\e076";
}
.glyphicon-step-forward:before {
  content: "\e077";
}
.glyphicon-eject:before {
  content: "\e078";
}
.glyphicon-chevron-left:before {
  content: "\e079";
}
.glyphicon-chevron-right:before {
  content: "\e080";
}
.glyphicon-plus-sign:before {
  content: "\e081";
}
.glyphicon-minus-sign:before {
  content: "\e082";
}
.glyphicon-remove-sign:before {
  content: "\e083";
}
.glyphicon-ok-sign:before {
  content: "\e084";
}
.glyphicon-question-sign:before {
  content: "\e085";
}
.glyphicon-info-sign:before {
  content: "\e086";
}
.glyphicon-screenshot:before {
  content: "\e087";
}
.glyphicon-remove-circle:before {
  content: "\e088";
}
.glyphicon-ok-circle:before {
  content: "\e089";
}
.glyphicon-ban-circle:before {
  content: "\e090";
}
.glyphicon-arrow-left:before {
  content: "\e091";
}
.glyphicon-arrow-right:before {
  content: "\e092";
}
.glyphicon-arrow-up:before {
  content: "\e093";
}
.glyphicon-arrow-down:before {
  content: "\e094";
}
.glyphicon-share-alt:before {
  content: "\e095";
}
.glyphicon-resize-full:before {
  content: "\e096";
}
.glyphicon-resize-small:before {
  content: "\e097";
}
.glyphicon-exclamation-sign:before {
  content: "\e101";
}
.glyphicon-gift:before {
  content: "\e102";
}
.glyphicon-leaf:before {
  content: "\e103";
}
.glyphicon-fire:before {
  content: "\e104";
}
.glyphicon-eye-open:before {
  content: "\e105";
}
.glyphicon-eye-close:before {
  content: "\e106";
}
.glyphicon-warning-sign:before {
  content: "\e107";
}
.glyphicon-plane:before {
  content: "\e108";
}
.glyphicon-calendar:before {
  content: "\e109";
}
.glyphicon-random:before {
  content: "\e110";
}
.glyphicon-comment:before {
  content: "\e111";
}
.glyphicon-magnet:before {
  content: "\e112";
}
.glyphicon-chevron-up:before {
  content: "\e113";
}
.glyphicon-chevron-down:before {
  content: "\e114";
}
.glyphicon-retweet:before {
  content: "\e115";
}
.glyphicon-shopping-cart:before {
  content: "\e116";
}
.glyphicon-folder-close:before {
  content: "\e117";
}
.glyphicon-folder-open:before {
  content: "\e118";
}
.glyphicon-resize-vertical:before {
  content: "\e119";
}
.glyphicon-resize-horizontal:before {
  content: "\e120";
}
.glyphicon-hdd:before {
  content: "\e121";
}
.glyphicon-bullhorn:before {
  content: "\e122";
}
.glyphicon-bell:before {
  content: "\e123";
}
.glyphicon-certificate:before {
  content: "\e124";
}
.glyphicon-thumbs-up:before {
  content: "\e125";
}
.glyphicon-thumbs-down:before {
  content: "\e126";
}
.glyphicon-hand-right:before {
  content: "\e127";
}
.glyphicon-hand-left:before {
  content: "\e128";
}
.glyphicon-hand-up:before {
  content: "\e129";
}
.glyphicon-hand-down:before {
  content: "\e130";
}
.glyphicon-circle-arrow-right:before {
  content: "\e131";
}
.glyphicon-circle-arrow-left:before {
  content: "\e132";
}
.glyphicon-circle-arrow-up:before {
  content: "\e133";
}
.glyphicon-circle-arrow-down:before {
  content: "\e134";
}
.glyphicon-globe:before {
  content: "\e135";
}
.glyphicon-wrench:before {
  content: "\e136";
}
.glyphicon-tasks:before {
  content: "\e137";
}
.glyphicon-filter:before {
  content: "\e138";
}
.glyphicon-briefcase:before {
  content: "\e139";
}
.glyphicon-fullscreen:before {
  content: "\e140";
}
.glyphicon-dashboard:before {
  content: "\e141";
}
.glyphicon-paperclip:before {
  content: "\e142";
}
.glyphicon-heart-empty:before {
  content: "\e143";
}
.glyphicon-link:before {
  content: "\e144";
}
.glyphicon-phone:before {
  content: "\e145";
}
.glyphicon-pushpin:before {
  content: "\e146";
}
.glyphicon-usd:before {
  content: "\e148";
}
.glyphicon-gbp:before {
  content: "\e149";
}
.glyphicon-sort:before {
  content: "\e150";
}
.glyphicon-sort-by-alphabet:before {
  content: "\e151";
}
.glyphicon-sort-by-alphabet-alt:before {
  content: "\e152";
}
.glyphicon-sort-by-order:before {
  content: "\e153";
}
.glyphicon-sort-by-order-alt:before {
  content: "\e154";
}
.glyphicon-sort-by-attributes:before {
  content: "\e155";
}
.glyphicon-sort-by-attributes-alt:before {
  content: "\e156";
}
.glyphicon-unchecked:before {
  content: "\e157";
}
.glyphicon-expand:before {
  content: "\e158";
}
.glyphicon-collapse-down:before {
  content: "\e159";
}
.glyphicon-collapse-up:before {
  content: "\e160";
}
.glyphicon-log-in:before {
  content: "\e161";
}
.glyphicon-flash:before {
  content: "\e162";
}
.glyphicon-log-out:before {
  content: "\e163";
}
.glyphicon-new-window:before {
  content: "\e164";
}
.glyphicon-record:before {
  content: "\e165";
}
.glyphicon-save:before {
  content: "\e166";
}
.glyphicon-open:before {
  content: "\e167";
}
.glyphicon-saved:before {
  content: "\e168";
}
.glyphicon-import:before {
  content: "\e169";
}
.glyphicon-export:before {
  content: "\e170";
}
.glyphicon-send:before {
  content: "\e171";
}
.glyphicon-floppy-disk:before {
  content: "\e172";
}
.glyphicon-floppy-saved:before {
  content: "\e173";
}
.glyphicon-floppy-remove:before {
  content: "\e174";
}
.glyphicon-floppy-save:before {
  content: "\e175";
}
.glyphicon-floppy-open:before {
  content: "\e176";
}
.glyphicon-credit-card:before {
  content: "\e177";
}
.glyphicon-transfer:before {
  content: "\e178";
}
.glyphicon-cutlery:before {
  content: "\e179";
}
.glyphicon-header:before {
  content: "\e180";
}
.glyphicon-compressed:before {
  content: "\e181";
}
.glyphicon-earphone:before {
  content: "\e182";
}
.glyphicon-phone-alt:before {
  content: "\e183";
}
.glyphicon-tower:before {
  content: "\e184";
}
.glyphicon-stats:before {
  content: "\e185";
}
.glyphicon-sd-video:before {
  content: "\e186";
}
.glyphicon-hd-video:before {
  content: "\e187";
}
.glyphicon-subtitles:before {
  content: "\e188";
}
.glyphicon-sound-stereo:before {
  content: "\e189";
}
.glyphicon-sound-dolby:before {
  content: "\e190";
}
.glyphicon-sound-5-1:before {
  content: "\e191";
}
.glyphicon-sound-6-1:before {
  content: "\e192";
}
.glyphicon-sound-7-1:before {
  content: "\e193";
}
.glyphicon-copyright-mark:before {
  content: "\e194";
}
.glyphicon-registration-mark:before {
  content: "\e195";
}
.glyphicon-cloud-download:before {
  content: "\e197";
}
.glyphicon-cloud-upload:before {
  content: "\e198";
}
.glyphicon-tree-conifer:before {
  content: "\e199";
}
.glyphicon-tree-deciduous:before {
  content: "\e200";
}
.glyphicon-cd:before {
  content: "\e201";
}
.glyphicon-save-file:before {
  content: "\e202";
}
.glyphicon-open-file:before {
  content: "\e203";
}
.glyphicon-level-up:before {
  content: "\e204";
}
.glyphicon-copy:before {
  content: "\e205";
}
.glyphicon-paste:before {
  content: "\e206";
}
.glyphicon-alert:before {
  content: "\e209";
}
.glyphicon-equalizer:before {
  content: "\e210";
}
.glyphicon-king:before {
  content: "\e211";
}
.glyphicon-queen:before {
  content: "\e212";
}
.glyphicon-pawn:before {
  content: "\e213";
}
.glyphicon-bishop:before {
  content: "\e214";
}
.glyphicon-knight:before {
  content: "\e215";
}
.glyphicon-baby-formula:before {
  content: "\e216";
}
.glyphicon-tent:before {
  content: "\26fa";
}
.glyphicon-blackboard:before {
  content: "\e218";
}
.glyphicon-bed:before {
  content: "\e219";
}
.glyphicon-apple:before {
  content: "\f8ff";
}
.glyphicon-erase:before {
  content: "\e221";
}
.glyphicon-hourglass:before {
  content: "\231b";
}
.glyphicon-lamp:before {
  content: "\e223";
}
.glyphicon-duplicate:before {
  content: "\e224";
}
.glyphicon-piggy-bank:before {
  content: "\e225";
}
.glyphicon-scissors:before {
  content: "\e226";
}
.glyphicon-bitcoin:before {
  content: "\e227";
}
.glyphicon-btc:before {
  content: "\e227";
}
.glyphicon-xbt:before {
  content: "\e227";
}
.glyphicon-yen:before {
  content: "\00a5";
}
.glyphicon-jpy:before {
  content: "\00a5";
}
.glyphicon-ruble:before {
  content: "\20bd";
}
.glyphicon-rub:before {
  content: "\20bd";
}
.glyphicon-scale:before {
  content: "\e230";
}
.glyphicon-ice-lolly:before {
  content: "\e231";
}
.glyphicon-ice-lolly-tasted:before {
  content: "\e232";
}
.glyphicon-education:before {
  content: "\e233";
}
.glyphicon-option-horizontal:before {
  content: "\e234";
}
.glyphicon-option-vertical:before {
  content: "\e235";
}
.glyphicon-menu-hamburger:before {
  content: "\e236";
}
.glyphicon-modal-window:before {
  content: "\e237";
}
.glyphicon-oil:before {
  content: "\e238";
}
.glyphicon-grain:before {
  content: "\e239";
}
.glyphicon-sunglasses:before {
  content: "\e240";
}
.glyphicon-text-size:before {
  content: "\e241";
}
.glyphicon-text-color:before {
  content: "\e242";
}
.glyphicon-text-background:before {
  content: "\e243";
}
.glyphicon-object-align-top:before {
  content: "\e244";
}
.glyphicon-object-align-bottom:before {
  content: "\e245";
}
.glyphicon-object-align-horizontal:before {
  content: "\e246";
}
.glyphicon-object-align-left:before {
  content: "\e247";
}
.glyphicon-object-align-vertical:before {
  content: "\e248";
}
.glyphicon-object-align-right:before {
  content: "\e249";
}
.glyphicon-triangle-right:before {
  content: "\e250";
}
.glyphicon-triangle-left:before {
  content: "\e251";
}
.glyphicon-triangle-bottom:before {
  content: "\e252";
}
.glyphicon-triangle-top:before {
  content: "\e253";
}
.glyphicon-console:before {
  content: "\e254";
}
.glyphicon-superscript:before {
  content: "\e255";
}
.glyphicon-subscript:before {
  content: "\e256";
}
.glyphicon-menu-left:before {
  content: "\e257";
}
.glyphicon-menu-right:before {
  content: "\e258";
}
.glyphicon-menu-down:before {
  content: "\e259";
}
.glyphicon-menu-up:before {
  content: "\e260";
}
* {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}
*:before,
*:after {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}
html {
  font-size: 10px;
  -webkit-tap-highlight-color: rgba(0, 0, 0, 0);
}
body {
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
  font-size: 13px;
  line-height: 1.42857143;
  color: #000;
  background-color: #fff;
}
input,
button,
select,
textarea {
  font-family: inherit;
  font-size: inherit;
  line-height: inherit;
}
a {
  color: #337ab7;
  text-decoration: none;
}
a:hover,
a:focus {
  color: #23527c;
  text-decoration: underline;
}
a:focus {
  outline: 5px auto -webkit-focus-ring-color;
  outline-offset: -2px;
}
figure {
  margin: 0;
}
img {
  vertical-align: middle;
}
.img-responsive,
.thumbnail > img,
.thumbnail a > img,
.carousel-inner > .item > img,
.carousel-inner > .item > a > img {
  display: block;
  max-width: 100%;
  height: auto;
}
.img-rounded {
  border-radius: 3px;
}
.img-thumbnail {
  padding: 4px;
  line-height: 1.42857143;
  background-color: #fff;
  border: 1px solid #ddd;
  border-radius: 2px;
  -webkit-transition: all 0.2s ease-in-out;
  -o-transition: all 0.2s ease-in-out;
  transition: all 0.2s ease-in-out;
  display: inline-block;
  max-width: 100%;
  height: auto;
}
.img-circle {
  border-radius: 50%;
}
hr {
  margin-top: 18px;
  margin-bottom: 18px;
  border: 0;
  border-top: 1px solid #eeeeee;
}
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  margin: -1px;
  padding: 0;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  border: 0;
}
.sr-only-focusable:active,
.sr-only-focusable:focus {
  position: static;
  width: auto;
  height: auto;
  margin: 0;
  overflow: visible;
  clip: auto;
}
[role="button"] {
  cursor: pointer;
}
h1,
h2,
h3,
h4,
h5,
h6,
.h1,
.h2,
.h3,
.h4,
.h5,
.h6 {
  font-family: inherit;
  font-weight: 500;
  line-height: 1.1;
  color: inherit;
}
h1 small,
h2 small,
h3 small,
h4 small,
h5 small,
h6 small,
.h1 small,
.h2 small,
.h3 small,
.h4 small,
.h5 small,
.h6 small,
h1 .small,
h2 .small,
h3 .small,
h4 .small,
h5 .small,
h6 .small,
.h1 .small,
.h2 .small,
.h3 .small,
.h4 .small,
.h5 .small,
.h6 .small {
  font-weight: normal;
  line-height: 1;
  color: #777777;
}
h1,
.h1,
h2,
.h2,
h3,
.h3 {
  margin-top: 18px;
  margin-bottom: 9px;
}
h1 small,
.h1 small,
h2 small,
.h2 small,
h3 small,
.h3 small,
h1 .small,
.h1 .small,
h2 .small,
.h2 .small,
h3 .small,
.h3 .small {
  font-size: 65%;
}
h4,
.h4,
h5,
.h5,
h6,
.h6 {
  margin-top: 9px;
  margin-bottom: 9px;
}
h4 small,
.h4 small,
h5 small,
.h5 small,
h6 small,
.h6 small,
h4 .small,
.h4 .small,
h5 .small,
.h5 .small,
h6 .small,
.h6 .small {
  font-size: 75%;
}
h1,
.h1 {
  font-size: 33px;
}
h2,
.h2 {
  font-size: 27px;
}
h3,
.h3 {
  font-size: 23px;
}
h4,
.h4 {
  font-size: 17px;
}
h5,
.h5 {
  font-size: 13px;
}
h6,
.h6 {
  font-size: 12px;
}
p {
  margin: 0 0 9px;
}
.lead {
  margin-bottom: 18px;
  font-size: 14px;
  font-weight: 300;
  line-height: 1.4;
}
@media (min-width: 768px) {
  .lead {
    font-size: 19.5px;
  }
}
small,
.small {
  font-size: 92%;
}
mark,
.mark {
  background-color: #fcf8e3;
  padding: .2em;
}
.text-left {
  text-align: left;
}
.text-right {
  text-align: right;
}
.text-center {
  text-align: center;
}
.text-justify {
  text-align: justify;
}
.text-nowrap {
  white-space: nowrap;
}
.text-lowercase {
  text-transform: lowercase;
}
.text-uppercase {
  text-transform: uppercase;
}
.text-capitalize {
  text-transform: capitalize;
}
.text-muted {
  color: #777777;
}
.text-primary {
  color: #337ab7;
}
a.text-primary:hover,
a.text-primary:focus {
  color: #286090;
}
.text-success {
  color: #3c763d;
}
a.text-success:hover,
a.text-success:focus {
  color: #2b542c;
}
.text-info {
  color: #31708f;
}
a.text-info:hover,
a.text-info:focus {
  color: #245269;
}
.text-warning {
  color: #8a6d3b;
}
a.text-warning:hover,
a.text-warning:focus {
  color: #66512c;
}
.text-danger {
  color: #a94442;
}
a.text-danger:hover,
a.text-danger:focus {
  color: #843534;
}
.bg-primary {
  color: #fff;
  background-color: #337ab7;
}
a.bg-primary:hover,
a.bg-primary:focus {
  background-color: #286090;
}
.bg-success {
  background-color: #dff0d8;
}
a.bg-success:hover,
a.bg-success:focus {
  background-color: #c1e2b3;
}
.bg-info {
  background-color: #d9edf7;
}
a.bg-info:hover,
a.bg-info:focus {
  background-color: #afd9ee;
}
.bg-warning {
  background-color: #fcf8e3;
}
a.bg-warning:hover,
a.bg-warning:focus {
  background-color: #f7ecb5;
}
.bg-danger {
  background-color: #f2dede;
}
a.bg-danger:hover,
a.bg-danger:focus {
  background-color: #e4b9b9;
}
.page-header {
  padding-bottom: 8px;
  margin: 36px 0 18px;
  border-bottom: 1px solid #eeeeee;
}
ul,
ol {
  margin-top: 0;
  margin-bottom: 9px;
}
ul ul,
ol ul,
ul ol,
ol ol {
  margin-bottom: 0;
}
.list-unstyled {
  padding-left: 0;
  list-style: none;
}
.list-inline {
  padding-left: 0;
  list-style: none;
  margin-left: -5px;
}
.list-inline > li {
  display: inline-block;
  padding-left: 5px;
  padding-right: 5px;
}
dl {
  margin-top: 0;
  margin-bottom: 18px;
}
dt,
dd {
  line-height: 1.42857143;
}
dt {
  font-weight: bold;
}
dd {
  margin-left: 0;
}
@media (min-width: 541px) {
  .dl-horizontal dt {
    float: left;
    width: 160px;
    clear: left;
    text-align: right;
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
  }
  .dl-horizontal dd {
    margin-left: 180px;
  }
}
abbr[title],
abbr[data-original-title] {
  cursor: help;
  border-bottom: 1px dotted #777777;
}
.initialism {
  font-size: 90%;
  text-transform: uppercase;
}
blockquote {
  padding: 9px 18px;
  margin: 0 0 18px;
  font-size: inherit;
  border-left: 5px solid #eeeeee;
}
blockquote p:last-child,
blockquote ul:last-child,
blockquote ol:last-child {
  margin-bottom: 0;
}
blockquote footer,
blockquote small,
blockquote .small {
  display: block;
  font-size: 80%;
  line-height: 1.42857143;
  color: #777777;
}
blockquote footer:before,
blockquote small:before,
blockquote .small:before {
  content: '\2014 \00A0';
}
.blockquote-reverse,
blockquote.pull-right {
  padding-right: 15px;
  padding-left: 0;
  border-right: 5px solid #eeeeee;
  border-left: 0;
  text-align: right;
}
.blockquote-reverse footer:before,
blockquote.pull-right footer:before,
.blockquote-reverse small:before,
blockquote.pull-right small:before,
.blockquote-reverse .small:before,
blockquote.pull-right .small:before {
  content: '';
}
.blockquote-reverse footer:after,
blockquote.pull-right footer:after,
.blockquote-reverse small:after,
blockquote.pull-right small:after,
.blockquote-reverse .small:after,
blockquote.pull-right .small:after {
  content: '\00A0 \2014';
}
address {
  margin-bottom: 18px;
  font-style: normal;
  line-height: 1.42857143;
}
code,
kbd,
pre,
samp {
  font-family: monospace;
}
code {
  padding: 2px 4px;
  font-size: 90%;
  color: #c7254e;
  background-color: #f9f2f4;
  border-radius: 2px;
}
kbd {
  padding: 2px 4px;
  font-size: 90%;
  color: #888;
  background-color: transparent;
  border-radius: 1px;
  box-shadow: inset 0 -1px 0 rgba(0, 0, 0, 0.25);
}
kbd kbd {
  padding: 0;
  font-size: 100%;
  font-weight: bold;
  box-shadow: none;
}
pre {
  display: block;
  padding: 8.5px;
  margin: 0 0 9px;
  font-size: 12px;
  line-height: 1.42857143;
  word-break: break-all;
  word-wrap: break-word;
  color: #333333;
  background-color: #f5f5f5;
  border: 1px solid #ccc;
  border-radius: 2px;
}
pre code {
  padding: 0;
  font-size: inherit;
  color: inherit;
  white-space: pre-wrap;
  background-color: transparent;
  border-radius: 0;
}
.pre-scrollable {
  max-height: 340px;
  overflow-y: scroll;
}
.container {
  margin-right: auto;
  margin-left: auto;
  padding-left: 0px;
  padding-right: 0px;
}
@media (min-width: 768px) {
  .container {
    width: 768px;
  }
}
@media (min-width: 992px) {
  .container {
    width: 940px;
  }
}
@media (min-width: 1200px) {
  .container {
    width: 1140px;
  }
}
.container-fluid {
  margin-right: auto;
  margin-left: auto;
  padding-left: 0px;
  padding-right: 0px;
}
.row {
  margin-left: 0px;
  margin-right: 0px;
}
.col-xs-1, .col-sm-1, .col-md-1, .col-lg-1, .col-xs-2, .col-sm-2, .col-md-2, .col-lg-2, .col-xs-3, .col-sm-3, .col-md-3, .col-lg-3, .col-xs-4, .col-sm-4, .col-md-4, .col-lg-4, .col-xs-5, .col-sm-5, .col-md-5, .col-lg-5, .col-xs-6, .col-sm-6, .col-md-6, .col-lg-6, .col-xs-7, .col-sm-7, .col-md-7, .col-lg-7, .col-xs-8, .col-sm-8, .col-md-8, .col-lg-8, .col-xs-9, .col-sm-9, .col-md-9, .col-lg-9, .col-xs-10, .col-sm-10, .col-md-10, .col-lg-10, .col-xs-11, .col-sm-11, .col-md-11, .col-lg-11, .col-xs-12, .col-sm-12, .col-md-12, .col-lg-12 {
  position: relative;
  min-height: 1px;
  padding-left: 0px;
  padding-right: 0px;
}
.col-xs-1, .col-xs-2, .col-xs-3, .col-xs-4, .col-xs-5, .col-xs-6, .col-xs-7, .col-xs-8, .col-xs-9, .col-xs-10, .col-xs-11, .col-xs-12 {
  float: left;
}
.col-xs-12 {
  width: 100%;
}
.col-xs-11 {
  width: 91.66666667%;
}
.col-xs-10 {
  width: 83.33333333%;
}
.col-xs-9 {
  width: 75%;
}
.col-xs-8 {
  width: 66.66666667%;
}
.col-xs-7 {
  width: 58.33333333%;
}
.col-xs-6 {
  width: 50%;
}
.col-xs-5 {
  width: 41.66666667%;
}
.col-xs-4 {
  width: 33.33333333%;
}
.col-xs-3 {
  width: 25%;
}
.col-xs-2 {
  width: 16.66666667%;
}
.col-xs-1 {
  width: 8.33333333%;
}
.col-xs-pull-12 {
  right: 100%;
}
.col-xs-pull-11 {
  right: 91.66666667%;
}
.col-xs-pull-10 {
  right: 83.33333333%;
}
.col-xs-pull-9 {
  right: 75%;
}
.col-xs-pull-8 {
  right: 66.66666667%;
}
.col-xs-pull-7 {
  right: 58.33333333%;
}
.col-xs-pull-6 {
  right: 50%;
}
.col-xs-pull-5 {
  right: 41.66666667%;
}
.col-xs-pull-4 {
  right: 33.33333333%;
}
.col-xs-pull-3 {
  right: 25%;
}
.col-xs-pull-2 {
  right: 16.66666667%;
}
.col-xs-pull-1 {
  right: 8.33333333%;
}
.col-xs-pull-0 {
  right: auto;
}
.col-xs-push-12 {
  left: 100%;
}
.col-xs-push-11 {
  left: 91.66666667%;
}
.col-xs-push-10 {
  left: 83.33333333%;
}
.col-xs-push-9 {
  left: 75%;
}
.col-xs-push-8 {
  left: 66.66666667%;
}
.col-xs-push-7 {
  left: 58.33333333%;
}
.col-xs-push-6 {
  left: 50%;
}
.col-xs-push-5 {
  left: 41.66666667%;
}
.col-xs-push-4 {
  left: 33.33333333%;
}
.col-xs-push-3 {
  left: 25%;
}
.col-xs-push-2 {
  left: 16.66666667%;
}
.col-xs-push-1 {
  left: 8.33333333%;
}
.col-xs-push-0 {
  left: auto;
}
.col-xs-offset-12 {
  margin-left: 100%;
}
.col-xs-offset-11 {
  margin-left: 91.66666667%;
}
.col-xs-offset-10 {
  margin-left: 83.33333333%;
}
.col-xs-offset-9 {
  margin-left: 75%;
}
.col-xs-offset-8 {
  margin-left: 66.66666667%;
}
.col-xs-offset-7 {
  margin-left: 58.33333333%;
}
.col-xs-offset-6 {
  margin-left: 50%;
}
.col-xs-offset-5 {
  margin-left: 41.66666667%;
}
.col-xs-offset-4 {
  margin-left: 33.33333333%;
}
.col-xs-offset-3 {
  margin-left: 25%;
}
.col-xs-offset-2 {
  margin-left: 16.66666667%;
}
.col-xs-offset-1 {
  margin-left: 8.33333333%;
}
.col-xs-offset-0 {
  margin-left: 0%;
}
@media (min-width: 768px) {
  .col-sm-1, .col-sm-2, .col-sm-3, .col-sm-4, .col-sm-5, .col-sm-6, .col-sm-7, .col-sm-8, .col-sm-9, .col-sm-10, .col-sm-11, .col-sm-12 {
    float: left;
  }
  .col-sm-12 {
    width: 100%;
  }
  .col-sm-11 {
    width: 91.66666667%;
  }
  .col-sm-10 {
    width: 83.33333333%;
  }
  .col-sm-9 {
    width: 75%;
  }
  .col-sm-8 {
    width: 66.66666667%;
  }
  .col-sm-7 {
    width: 58.33333333%;
  }
  .col-sm-6 {
    width: 50%;
  }
  .col-sm-5 {
    width: 41.66666667%;
  }
  .col-sm-4 {
    width: 33.33333333%;
  }
  .col-sm-3 {
    width: 25%;
  }
  .col-sm-2 {
    width: 16.66666667%;
  }
  .col-sm-1 {
    width: 8.33333333%;
  }
  .col-sm-pull-12 {
    right: 100%;
  }
  .col-sm-pull-11 {
    right: 91.66666667%;
  }
  .col-sm-pull-10 {
    right: 83.33333333%;
  }
  .col-sm-pull-9 {
    right: 75%;
  }
  .col-sm-pull-8 {
    right: 66.66666667%;
  }
  .col-sm-pull-7 {
    right: 58.33333333%;
  }
  .col-sm-pull-6 {
    right: 50%;
  }
  .col-sm-pull-5 {
    right: 41.66666667%;
  }
  .col-sm-pull-4 {
    right: 33.33333333%;
  }
  .col-sm-pull-3 {
    right: 25%;
  }
  .col-sm-pull-2 {
    right: 16.66666667%;
  }
  .col-sm-pull-1 {
    right: 8.33333333%;
  }
  .col-sm-pull-0 {
    right: auto;
  }
  .col-sm-push-12 {
    left: 100%;
  }
  .col-sm-push-11 {
    left: 91.66666667%;
  }
  .col-sm-push-10 {
    left: 83.33333333%;
  }
  .col-sm-push-9 {
    left: 75%;
  }
  .col-sm-push-8 {
    left: 66.66666667%;
  }
  .col-sm-push-7 {
    left: 58.33333333%;
  }
  .col-sm-push-6 {
    left: 50%;
  }
  .col-sm-push-5 {
    left: 41.66666667%;
  }
  .col-sm-push-4 {
    left: 33.33333333%;
  }
  .col-sm-push-3 {
    left: 25%;
  }
  .col-sm-push-2 {
    left: 16.66666667%;
  }
  .col-sm-push-1 {
    left: 8.33333333%;
  }
  .col-sm-push-0 {
    left: auto;
  }
  .col-sm-offset-12 {
    margin-left: 100%;
  }
  .col-sm-offset-11 {
    margin-left: 91.66666667%;
  }
  .col-sm-offset-10 {
    margin-left: 83.33333333%;
  }
  .col-sm-offset-9 {
    margin-left: 75%;
  }
  .col-sm-offset-8 {
    margin-left: 66.66666667%;
  }
  .col-sm-offset-7 {
    margin-left: 58.33333333%;
  }
  .col-sm-offset-6 {
    margin-left: 50%;
  }
  .col-sm-offset-5 {
    margin-left: 41.66666667%;
  }
  .col-sm-offset-4 {
    margin-left: 33.33333333%;
  }
  .col-sm-offset-3 {
    margin-left: 25%;
  }
  .col-sm-offset-2 {
    margin-left: 16.66666667%;
  }
  .col-sm-offset-1 {
    margin-left: 8.33333333%;
  }
  .col-sm-offset-0 {
    margin-left: 0%;
  }
}
@media (min-width: 992px) {
  .col-md-1, .col-md-2, .col-md-3, .col-md-4, .col-md-5, .col-md-6, .col-md-7, .col-md-8, .col-md-9, .col-md-10, .col-md-11, .col-md-12 {
    float: left;
  }
  .col-md-12 {
    width: 100%;
  }
  .col-md-11 {
    width: 91.66666667%;
  }
  .col-md-10 {
    width: 83.33333333%;
  }
  .col-md-9 {
    width: 75%;
  }
  .col-md-8 {
    width: 66.66666667%;
  }
  .col-md-7 {
    width: 58.33333333%;
  }
  .col-md-6 {
    width: 50%;
  }
  .col-md-5 {
    width: 41.66666667%;
  }
  .col-md-4 {
    width: 33.33333333%;
  }
  .col-md-3 {
    width: 25%;
  }
  .col-md-2 {
    width: 16.66666667%;
  }
  .col-md-1 {
    width: 8.33333333%;
  }
  .col-md-pull-12 {
    right: 100%;
  }
  .col-md-pull-11 {
    right: 91.66666667%;
  }
  .col-md-pull-10 {
    right: 83.33333333%;
  }
  .col-md-pull-9 {
    right: 75%;
  }
  .col-md-pull-8 {
    right: 66.66666667%;
  }
  .col-md-pull-7 {
    right: 58.33333333%;
  }
  .col-md-pull-6 {
    right: 50%;
  }
  .col-md-pull-5 {
    right: 41.66666667%;
  }
  .col-md-pull-4 {
    right: 33.33333333%;
  }
  .col-md-pull-3 {
    right: 25%;
  }
  .col-md-pull-2 {
    right: 16.66666667%;
  }
  .col-md-pull-1 {
    right: 8.33333333%;
  }
  .col-md-pull-0 {
    right: auto;
  }
  .col-md-push-12 {
    left: 100%;
  }
  .col-md-push-11 {
    left: 91.66666667%;
  }
  .col-md-push-10 {
    left: 83.33333333%;
  }
  .col-md-push-9 {
    left: 75%;
  }
  .col-md-push-8 {
    left: 66.66666667%;
  }
  .col-md-push-7 {
    left: 58.33333333%;
  }
  .col-md-push-6 {
    left: 50%;
  }
  .col-md-push-5 {
    left: 41.66666667%;
  }
  .col-md-push-4 {
    left: 33.33333333%;
  }
  .col-md-push-3 {
    left: 25%;
  }
  .col-md-push-2 {
    left: 16.66666667%;
  }
  .col-md-push-1 {
    left: 8.33333333%;
  }
  .col-md-push-0 {
    left: auto;
  }
  .col-md-offset-12 {
    margin-left: 100%;
  }
  .col-md-offset-11 {
    margin-left: 91.66666667%;
  }
  .col-md-offset-10 {
    margin-left: 83.33333333%;
  }
  .col-md-offset-9 {
    margin-left: 75%;
  }
  .col-md-offset-8 {
    margin-left: 66.66666667%;
  }
  .col-md-offset-7 {
    margin-left: 58.33333333%;
  }
  .col-md-offset-6 {
    margin-left: 50%;
  }
  .col-md-offset-5 {
    margin-left: 41.66666667%;
  }
  .col-md-offset-4 {
    margin-left: 33.33333333%;
  }
  .col-md-offset-3 {
    margin-left: 25%;
  }
  .col-md-offset-2 {
    margin-left: 16.66666667%;
  }
  .col-md-offset-1 {
    margin-left: 8.33333333%;
  }
  .col-md-offset-0 {
    margin-left: 0%;
  }
}
@media (min-width: 1200px) {
  .col-lg-1, .col-lg-2, .col-lg-3, .col-lg-4, .col-lg-5, .col-lg-6, .col-lg-7, .col-lg-8, .col-lg-9, .col-lg-10, .col-lg-11, .col-lg-12 {
    float: left;
  }
  .col-lg-12 {
    width: 100%;
  }
  .col-lg-11 {
    width: 91.66666667%;
  }
  .col-lg-10 {
    width: 83.33333333%;
  }
  .col-lg-9 {
    width: 75%;
  }
  .col-lg-8 {
    width: 66.66666667%;
  }
  .col-lg-7 {
    width: 58.33333333%;
  }
  .col-lg-6 {
    width: 50%;
  }
  .col-lg-5 {
    width: 41.66666667%;
  }
  .col-lg-4 {
    width: 33.33333333%;
  }
  .col-lg-3 {
    width: 25%;
  }
  .col-lg-2 {
    width: 16.66666667%;
  }
  .col-lg-1 {
    width: 8.33333333%;
  }
  .col-lg-pull-12 {
    right: 100%;
  }
  .col-lg-pull-11 {
    right: 91.66666667%;
  }
  .col-lg-pull-10 {
    right: 83.33333333%;
  }
  .col-lg-pull-9 {
    right: 75%;
  }
  .col-lg-pull-8 {
    right: 66.66666667%;
  }
  .col-lg-pull-7 {
    right: 58.33333333%;
  }
  .col-lg-pull-6 {
    right: 50%;
  }
  .col-lg-pull-5 {
    right: 41.66666667%;
  }
  .col-lg-pull-4 {
    right: 33.33333333%;
  }
  .col-lg-pull-3 {
    right: 25%;
  }
  .col-lg-pull-2 {
    right: 16.66666667%;
  }
  .col-lg-pull-1 {
    right: 8.33333333%;
  }
  .col-lg-pull-0 {
    right: auto;
  }
  .col-lg-push-12 {
    left: 100%;
  }
  .col-lg-push-11 {
    left: 91.66666667%;
  }
  .col-lg-push-10 {
    left: 83.33333333%;
  }
  .col-lg-push-9 {
    left: 75%;
  }
  .col-lg-push-8 {
    left: 66.66666667%;
  }
  .col-lg-push-7 {
    left: 58.33333333%;
  }
  .col-lg-push-6 {
    left: 50%;
  }
  .col-lg-push-5 {
    left: 41.66666667%;
  }
  .col-lg-push-4 {
    left: 33.33333333%;
  }
  .col-lg-push-3 {
    left: 25%;
  }
  .col-lg-push-2 {
    left: 16.66666667%;
  }
  .col-lg-push-1 {
    left: 8.33333333%;
  }
  .col-lg-push-0 {
    left: auto;
  }
  .col-lg-offset-12 {
    margin-left: 100%;
  }
  .col-lg-offset-11 {
    margin-left: 91.66666667%;
  }
  .col-lg-offset-10 {
    margin-left: 83.33333333%;
  }
  .col-lg-offset-9 {
    margin-left: 75%;
  }
  .col-lg-offset-8 {
    margin-left: 66.66666667%;
  }
  .col-lg-offset-7 {
    margin-left: 58.33333333%;
  }
  .col-lg-offset-6 {
    margin-left: 50%;
  }
  .col-lg-offset-5 {
    margin-left: 41.66666667%;
  }
  .col-lg-offset-4 {
    margin-left: 33.33333333%;
  }
  .col-lg-offset-3 {
    margin-left: 25%;
  }
  .col-lg-offset-2 {
    margin-left: 16.66666667%;
  }
  .col-lg-offset-1 {
    margin-left: 8.33333333%;
  }
  .col-lg-offset-0 {
    margin-left: 0%;
  }
}
table {
  background-color: transparent;
}
caption {
  padding-top: 8px;
  padding-bottom: 8px;
  color: #777777;
  text-align: left;
}
th {
  text-align: left;
}
.table {
  width: 100%;
  max-width: 100%;
  margin-bottom: 18px;
}
.table > thead > tr > th,
.table > tbody > tr > th,
.table > tfoot > tr > th,
.table > thead > tr > td,
.table > tbody > tr > td,
.table > tfoot > tr > td {
  padding: 8px;
  line-height: 1.42857143;
  vertical-align: top;
  border-top: 1px solid #ddd;
}
.table > thead > tr > th {
  vertical-align: bottom;
  border-bottom: 2px solid #ddd;
}
.table > caption + thead > tr:first-child > th,
.table > colgroup + thead > tr:first-child > th,
.table > thead:first-child > tr:first-child > th,
.table > caption + thead > tr:first-child > td,
.table > colgroup + thead > tr:first-child > td,
.table > thead:first-child > tr:first-child > td {
  border-top: 0;
}
.table > tbody + tbody {
  border-top: 2px solid #ddd;
}
.table .table {
  background-color: #fff;
}
.table-condensed > thead > tr > th,
.table-condensed > tbody > tr > th,
.table-condensed > tfoot > tr > th,
.table-condensed > thead > tr > td,
.table-condensed > tbody > tr > td,
.table-condensed > tfoot > tr > td {
  padding: 5px;
}
.table-bordered {
  border: 1px solid #ddd;
}
.table-bordered > thead > tr > th,
.table-bordered > tbody > tr > th,
.table-bordered > tfoot > tr > th,
.table-bordered > thead > tr > td,
.table-bordered > tbody > tr > td,
.table-bordered > tfoot > tr > td {
  border: 1px solid #ddd;
}
.table-bordered > thead > tr > th,
.table-bordered > thead > tr > td {
  border-bottom-width: 2px;
}
.table-striped > tbody > tr:nth-of-type(odd) {
  background-color: #f9f9f9;
}
.table-hover > tbody > tr:hover {
  background-color: #f5f5f5;
}
table col[class*="col-"] {
  position: static;
  float: none;
  display: table-column;
}
table td[class*="col-"],
table th[class*="col-"] {
  position: static;
  float: none;
  display: table-cell;
}
.table > thead > tr > td.active,
.table > tbody > tr > td.active,
.table > tfoot > tr > td.active,
.table > thead > tr > th.active,
.table > tbody > tr > th.active,
.table > tfoot > tr > th.active,
.table > thead > tr.active > td,
.table > tbody > tr.active > td,
.table > tfoot > tr.active > td,
.table > thead > tr.active > th,
.table > tbody > tr.active > th,
.table > tfoot > tr.active > th {
  background-color: #f5f5f5;
}
.table-hover > tbody > tr > td.active:hover,
.table-hover > tbody > tr > th.active:hover,
.table-hover > tbody > tr.active:hover > td,
.table-hover > tbody > tr:hover > .active,
.table-hover > tbody > tr.active:hover > th {
  background-color: #e8e8e8;
}
.table > thead > tr > td.success,
.table > tbody > tr > td.success,
.table > tfoot > tr > td.success,
.table > thead > tr > th.success,
.table > tbody > tr > th.success,
.table > tfoot > tr > th.success,
.table > thead > tr.success > td,
.table > tbody > tr.success > td,
.table > tfoot > tr.success > td,
.table > thead > tr.success > th,
.table > tbody > tr.success > th,
.table > tfoot > tr.success > th {
  background-color: #dff0d8;
}
.table-hover > tbody > tr > td.success:hover,
.table-hover > tbody > tr > th.success:hover,
.table-hover > tbody > tr.success:hover > td,
.table-hover > tbody > tr:hover > .success,
.table-hover > tbody > tr.success:hover > th {
  background-color: #d0e9c6;
}
.table > thead > tr > td.info,
.table > tbody > tr > td.info,
.table > tfoot > tr > td.info,
.table > thead > tr > th.info,
.table > tbody > tr > th.info,
.table > tfoot > tr > th.info,
.table > thead > tr.info > td,
.table > tbody > tr.info > td,
.table > tfoot > tr.info > td,
.table > thead > tr.info > th,
.table > tbody > tr.info > th,
.table > tfoot > tr.info > th {
  background-color: #d9edf7;
}
.table-hover > tbody > tr > td.info:hover,
.table-hover > tbody > tr > th.info:hover,
.table-hover > tbody > tr.info:hover > td,
.table-hover > tbody > tr:hover > .info,
.table-hover > tbody > tr.info:hover > th {
  background-color: #c4e3f3;
}
.table > thead > tr > td.warning,
.table > tbody > tr > td.warning,
.table > tfoot > tr > td.warning,
.table > thead > tr > th.warning,
.table > tbody > tr > th.warning,
.table > tfoot > tr > th.warning,
.table > thead > tr.warning > td,
.table > tbody > tr.warning > td,
.table > tfoot > tr.warning > td,
.table > thead > tr.warning > th,
.table > tbody > tr.warning > th,
.table > tfoot > tr.warning > th {
  background-color: #fcf8e3;
}
.table-hover > tbody > tr > td.warning:hover,
.table-hover > tbody > tr > th.warning:hover,
.table-hover > tbody > tr.warning:hover > td,
.table-hover > tbody > tr:hover > .warning,
.table-hover > tbody > tr.warning:hover > th {
  background-color: #faf2cc;
}
.table > thead > tr > td.danger,
.table > tbody > tr > td.danger,
.table > tfoot > tr > td.danger,
.table > thead > tr > th.danger,
.table > tbody > tr > th.danger,
.table > tfoot > tr > th.danger,
.table > thead > tr.danger > td,
.table > tbody > tr.danger > td,
.table > tfoot > tr.danger > td,
.table > thead > tr.danger > th,
.table > tbody > tr.danger > th,
.table > tfoot > tr.danger > th {
  background-color: #f2dede;
}
.table-hover > tbody > tr > td.danger:hover,
.table-hover > tbody > tr > th.danger:hover,
.table-hover > tbody > tr.danger:hover > td,
.table-hover > tbody > tr:hover > .danger,
.table-hover > tbody > tr.danger:hover > th {
  background-color: #ebcccc;
}
.table-responsive {
  overflow-x: auto;
  min-height: 0.01%;
}
@media screen and (max-width: 767px) {
  .table-responsive {
    width: 100%;
    margin-bottom: 13.5px;
    overflow-y: hidden;
    -ms-overflow-style: -ms-autohiding-scrollbar;
    border: 1px solid #ddd;
  }
  .table-responsive > .table {
    margin-bottom: 0;
  }
  .table-responsive > .table > thead > tr > th,
  .table-responsive > .table > tbody > tr > th,
  .table-responsive > .table > tfoot > tr > th,
  .table-responsive > .table > thead > tr > td,
  .table-responsive > .table > tbody > tr > td,
  .table-responsive > .table > tfoot > tr > td {
    white-space: nowrap;
  }
  .table-responsive > .table-bordered {
    border: 0;
  }
  .table-responsive > .table-bordered > thead > tr > th:first-child,
  .table-responsive > .table-bordered > tbody > tr > th:first-child,
  .table-responsive > .table-bordered > tfoot > tr > th:first-child,
  .table-responsive > .table-bordered > thead > tr > td:first-child,
  .table-responsive > .table-bordered > tbody > tr > td:first-child,
  .table-responsive > .table-bordered > tfoot > tr > td:first-child {
    border-left: 0;
  }
  .table-responsive > .table-bordered > thead > tr > th:last-child,
  .table-responsive > .table-bordered > tbody > tr > th:last-child,
  .table-responsive > .table-bordered > tfoot > tr > th:last-child,
  .table-responsive > .table-bordered > thead > tr > td:last-child,
  .table-responsive > .table-bordered > tbody > tr > td:last-child,
  .table-responsive > .table-bordered > tfoot > tr > td:last-child {
    border-right: 0;
  }
  .table-responsive > .table-bordered > tbody > tr:last-child > th,
  .table-responsive > .table-bordered > tfoot > tr:last-child > th,
  .table-responsive > .table-bordered > tbody > tr:last-child > td,
  .table-responsive > .table-bordered > tfoot > tr:last-child > td {
    border-bottom: 0;
  }
}
fieldset {
  padding: 0;
  margin: 0;
  border: 0;
  min-width: 0;
}
legend {
  display: block;
  width: 100%;
  padding: 0;
  margin-bottom: 18px;
  font-size: 19.5px;
  line-height: inherit;
  color: #333333;
  border: 0;
  border-bottom: 1px solid #e5e5e5;
}
label {
  display: inline-block;
  max-width: 100%;
  margin-bottom: 5px;
  font-weight: bold;
}
input[type="search"] {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}
input[type="radio"],
input[type="checkbox"] {
  margin: 4px 0 0;
  margin-top: 1px \9;
  line-height: normal;
}
input[type="file"] {
  display: block;
}
input[type="range"] {
  display: block;
  width: 100%;
}
select[multiple],
select[size] {
  height: auto;
}
input[type="file"]:focus,
input[type="radio"]:focus,
input[type="checkbox"]:focus {
  outline: 5px auto -webkit-focus-ring-color;
  outline-offset: -2px;
}
output {
  display: block;
  padding-top: 7px;
  font-size: 13px;
  line-height: 1.42857143;
  color: #555555;
}
.form-control {
  display: block;
  width: 100%;
  height: 32px;
  padding: 6px 12px;
  font-size: 13px;
  line-height: 1.42857143;
  color: #555555;
  background-color: #fff;
  background-image: none;
  border: 1px solid #ccc;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  -webkit-transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  -o-transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
}
.form-control:focus {
  border-color: #66afe9;
  outline: 0;
  -webkit-box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, 0.6);
  box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, 0.6);
}
.form-control::-moz-placeholder {
  color: #999;
  opacity: 1;
}
.form-control:-ms-input-placeholder {
  color: #999;
}
.form-control::-webkit-input-placeholder {
  color: #999;
}
.form-control::-ms-expand {
  border: 0;
  background-color: transparent;
}
.form-control[disabled],
.form-control[readonly],
fieldset[disabled] .form-control {
  background-color: #eeeeee;
  opacity: 1;
}
.form-control[disabled],
fieldset[disabled] .form-control {
  cursor: not-allowed;
}
textarea.form-control {
  height: auto;
}
input[type="search"] {
  -webkit-appearance: none;
}
@media screen and (-webkit-min-device-pixel-ratio: 0) {
  input[type="date"].form-control,
  input[type="time"].form-control,
  input[type="datetime-local"].form-control,
  input[type="month"].form-control {
    line-height: 32px;
  }
  input[type="date"].input-sm,
  input[type="time"].input-sm,
  input[type="datetime-local"].input-sm,
  input[type="month"].input-sm,
  .input-group-sm input[type="date"],
  .input-group-sm input[type="time"],
  .input-group-sm input[type="datetime-local"],
  .input-group-sm input[type="month"] {
    line-height: 30px;
  }
  input[type="date"].input-lg,
  input[type="time"].input-lg,
  input[type="datetime-local"].input-lg,
  input[type="month"].input-lg,
  .input-group-lg input[type="date"],
  .input-group-lg input[type="time"],
  .input-group-lg input[type="datetime-local"],
  .input-group-lg input[type="month"] {
    line-height: 45px;
  }
}
.form-group {
  margin-bottom: 15px;
}
.radio,
.checkbox {
  position: relative;
  display: block;
  margin-top: 10px;
  margin-bottom: 10px;
}
.radio label,
.checkbox label {
  min-height: 18px;
  padding-left: 20px;
  margin-bottom: 0;
  font-weight: normal;
  cursor: pointer;
}
.radio input[type="radio"],
.radio-inline input[type="radio"],
.checkbox input[type="checkbox"],
.checkbox-inline input[type="checkbox"] {
  position: absolute;
  margin-left: -20px;
  margin-top: 4px \9;
}
.radio + .radio,
.checkbox + .checkbox {
  margin-top: -5px;
}
.radio-inline,
.checkbox-inline {
  position: relative;
  display: inline-block;
  padding-left: 20px;
  margin-bottom: 0;
  vertical-align: middle;
  font-weight: normal;
  cursor: pointer;
}
.radio-inline + .radio-inline,
.checkbox-inline + .checkbox-inline {
  margin-top: 0;
  margin-left: 10px;
}
input[type="radio"][disabled],
input[type="checkbox"][disabled],
input[type="radio"].disabled,
input[type="checkbox"].disabled,
fieldset[disabled] input[type="radio"],
fieldset[disabled] input[type="checkbox"] {
  cursor: not-allowed;
}
.radio-inline.disabled,
.checkbox-inline.disabled,
fieldset[disabled] .radio-inline,
fieldset[disabled] .checkbox-inline {
  cursor: not-allowed;
}
.radio.disabled label,
.checkbox.disabled label,
fieldset[disabled] .radio label,
fieldset[disabled] .checkbox label {
  cursor: not-allowed;
}
.form-control-static {
  padding-top: 7px;
  padding-bottom: 7px;
  margin-bottom: 0;
  min-height: 31px;
}
.form-control-static.input-lg,
.form-control-static.input-sm {
  padding-left: 0;
  padding-right: 0;
}
.input-sm {
  height: 30px;
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
}
select.input-sm {
  height: 30px;
  line-height: 30px;
}
textarea.input-sm,
select[multiple].input-sm {
  height: auto;
}
.form-group-sm .form-control {
  height: 30px;
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
}
.form-group-sm select.form-control {
  height: 30px;
  line-height: 30px;
}
.form-group-sm textarea.form-control,
.form-group-sm select[multiple].form-control {
  height: auto;
}
.form-group-sm .form-control-static {
  height: 30px;
  min-height: 30px;
  padding: 6px 10px;
  font-size: 12px;
  line-height: 1.5;
}
.input-lg {
  height: 45px;
  padding: 10px 16px;
  font-size: 17px;
  line-height: 1.3333333;
  border-radius: 3px;
}
select.input-lg {
  height: 45px;
  line-height: 45px;
}
textarea.input-lg,
select[multiple].input-lg {
  height: auto;
}
.form-group-lg .form-control {
  height: 45px;
  padding: 10px 16px;
  font-size: 17px;
  line-height: 1.3333333;
  border-radius: 3px;
}
.form-group-lg select.form-control {
  height: 45px;
  line-height: 45px;
}
.form-group-lg textarea.form-control,
.form-group-lg select[multiple].form-control {
  height: auto;
}
.form-group-lg .form-control-static {
  height: 45px;
  min-height: 35px;
  padding: 11px 16px;
  font-size: 17px;
  line-height: 1.3333333;
}
.has-feedback {
  position: relative;
}
.has-feedback .form-control {
  padding-right: 40px;
}
.form-control-feedback {
  position: absolute;
  top: 0;
  right: 0;
  z-index: 2;
  display: block;
  width: 32px;
  height: 32px;
  line-height: 32px;
  text-align: center;
  pointer-events: none;
}
.input-lg + .form-control-feedback,
.input-group-lg + .form-control-feedback,
.form-group-lg .form-control + .form-control-feedback {
  width: 45px;
  height: 45px;
  line-height: 45px;
}
.input-sm + .form-control-feedback,
.input-group-sm + .form-control-feedback,
.form-group-sm .form-control + .form-control-feedback {
  width: 30px;
  height: 30px;
  line-height: 30px;
}
.has-success .help-block,
.has-success .control-label,
.has-success .radio,
.has-success .checkbox,
.has-success .radio-inline,
.has-success .checkbox-inline,
.has-success.radio label,
.has-success.checkbox label,
.has-success.radio-inline label,
.has-success.checkbox-inline label {
  color: #3c763d;
}
.has-success .form-control {
  border-color: #3c763d;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
}
.has-success .form-control:focus {
  border-color: #2b542c;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #67b168;
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #67b168;
}
.has-success .input-group-addon {
  color: #3c763d;
  border-color: #3c763d;
  background-color: #dff0d8;
}
.has-success .form-control-feedback {
  color: #3c763d;
}
.has-warning .help-block,
.has-warning .control-label,
.has-warning .radio,
.has-warning .checkbox,
.has-warning .radio-inline,
.has-warning .checkbox-inline,
.has-warning.radio label,
.has-warning.checkbox label,
.has-warning.radio-inline label,
.has-warning.checkbox-inline label {
  color: #8a6d3b;
}
.has-warning .form-control {
  border-color: #8a6d3b;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
}
.has-warning .form-control:focus {
  border-color: #66512c;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #c0a16b;
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #c0a16b;
}
.has-warning .input-group-addon {
  color: #8a6d3b;
  border-color: #8a6d3b;
  background-color: #fcf8e3;
}
.has-warning .form-control-feedback {
  color: #8a6d3b;
}
.has-error .help-block,
.has-error .control-label,
.has-error .radio,
.has-error .checkbox,
.has-error .radio-inline,
.has-error .checkbox-inline,
.has-error.radio label,
.has-error.checkbox label,
.has-error.radio-inline label,
.has-error.checkbox-inline label {
  color: #a94442;
}
.has-error .form-control {
  border-color: #a94442;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
}
.has-error .form-control:focus {
  border-color: #843534;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #ce8483;
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #ce8483;
}
.has-error .input-group-addon {
  color: #a94442;
  border-color: #a94442;
  background-color: #f2dede;
}
.has-error .form-control-feedback {
  color: #a94442;
}
.has-feedback label ~ .form-control-feedback {
  top: 23px;
}
.has-feedback label.sr-only ~ .form-control-feedback {
  top: 0;
}
.help-block {
  display: block;
  margin-top: 5px;
  margin-bottom: 10px;
  color: #404040;
}
@media (min-width: 768px) {
  .form-inline .form-group {
    display: inline-block;
    margin-bottom: 0;
    vertical-align: middle;
  }
  .form-inline .form-control {
    display: inline-block;
    width: auto;
    vertical-align: middle;
  }
  .form-inline .form-control-static {
    display: inline-block;
  }
  .form-inline .input-group {
    display: inline-table;
    vertical-align: middle;
  }
  .form-inline .input-group .input-group-addon,
  .form-inline .input-group .input-group-btn,
  .form-inline .input-group .form-control {
    width: auto;
  }
  .form-inline .input-group > .form-control {
    width: 100%;
  }
  .form-inline .control-label {
    margin-bottom: 0;
    vertical-align: middle;
  }
  .form-inline .radio,
  .form-inline .checkbox {
    display: inline-block;
    margin-top: 0;
    margin-bottom: 0;
    vertical-align: middle;
  }
  .form-inline .radio label,
  .form-inline .checkbox label {
    padding-left: 0;
  }
  .form-inline .radio input[type="radio"],
  .form-inline .checkbox input[type="checkbox"] {
    position: relative;
    margin-left: 0;
  }
  .form-inline .has-feedback .form-control-feedback {
    top: 0;
  }
}
.form-horizontal .radio,
.form-horizontal .checkbox,
.form-horizontal .radio-inline,
.form-horizontal .checkbox-inline {
  margin-top: 0;
  margin-bottom: 0;
  padding-top: 7px;
}
.form-horizontal .radio,
.form-horizontal .checkbox {
  min-height: 25px;
}
.form-horizontal .form-group {
  margin-left: 0px;
  margin-right: 0px;
}
@media (min-width: 768px) {
  .form-horizontal .control-label {
    text-align: right;
    margin-bottom: 0;
    padding-top: 7px;
  }
}
.form-horizontal .has-feedback .form-control-feedback {
  right: 0px;
}
@media (min-width: 768px) {
  .form-horizontal .form-group-lg .control-label {
    padding-top: 11px;
    font-size: 17px;
  }
}
@media (min-width: 768px) {
  .form-horizontal .form-group-sm .control-label {
    padding-top: 6px;
    font-size: 12px;
  }
}
.btn {
  display: inline-block;
  margin-bottom: 0;
  font-weight: normal;
  text-align: center;
  vertical-align: middle;
  touch-action: manipulation;
  cursor: pointer;
  background-image: none;
  border: 1px solid transparent;
  white-space: nowrap;
  padding: 6px 12px;
  font-size: 13px;
  line-height: 1.42857143;
  border-radius: 2px;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}
.btn:focus,
.btn:active:focus,
.btn.active:focus,
.btn.focus,
.btn:active.focus,
.btn.active.focus {
  outline: 5px auto -webkit-focus-ring-color;
  outline-offset: -2px;
}
.btn:hover,
.btn:focus,
.btn.focus {
  color: #333;
  text-decoration: none;
}
.btn:active,
.btn.active {
  outline: 0;
  background-image: none;
  -webkit-box-shadow: inset 0 3px 5px rgba(0, 0, 0, 0.125);
  box-shadow: inset 0 3px 5px rgba(0, 0, 0, 0.125);
}
.btn.disabled,
.btn[disabled],
fieldset[disabled] .btn {
  cursor: not-allowed;
  opacity: 0.65;
  filter: alpha(opacity=65);
  -webkit-box-shadow: none;
  box-shadow: none;
}
a.btn.disabled,
fieldset[disabled] a.btn {
  pointer-events: none;
}
.btn-default {
  color: #333;
  background-color: #fff;
  border-color: #ccc;
}
.btn-default:focus,
.btn-default.focus {
  color: #333;
  background-color: #e6e6e6;
  border-color: #8c8c8c;
}
.btn-default:hover {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
.btn-default:active,
.btn-default.active,
.open > .dropdown-toggle.btn-default {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
.btn-default:active:hover,
.btn-default.active:hover,
.open > .dropdown-toggle.btn-default:hover,
.btn-default:active:focus,
.btn-default.active:focus,
.open > .dropdown-toggle.btn-default:focus,
.btn-default:active.focus,
.btn-default.active.focus,
.open > .dropdown-toggle.btn-default.focus {
  color: #333;
  background-color: #d4d4d4;
  border-color: #8c8c8c;
}
.btn-default:active,
.btn-default.active,
.open > .dropdown-toggle.btn-default {
  background-image: none;
}
.btn-default.disabled:hover,
.btn-default[disabled]:hover,
fieldset[disabled] .btn-default:hover,
.btn-default.disabled:focus,
.btn-default[disabled]:focus,
fieldset[disabled] .btn-default:focus,
.btn-default.disabled.focus,
.btn-default[disabled].focus,
fieldset[disabled] .btn-default.focus {
  background-color: #fff;
  border-color: #ccc;
}
.btn-default .badge {
  color: #fff;
  background-color: #333;
}
.btn-primary {
  color: #fff;
  background-color: #337ab7;
  border-color: #2e6da4;
}
.btn-primary:focus,
.btn-primary.focus {
  color: #fff;
  background-color: #286090;
  border-color: #122b40;
}
.btn-primary:hover {
  color: #fff;
  background-color: #286090;
  border-color: #204d74;
}
.btn-primary:active,
.btn-primary.active,
.open > .dropdown-toggle.btn-primary {
  color: #fff;
  background-color: #286090;
  border-color: #204d74;
}
.btn-primary:active:hover,
.btn-primary.active:hover,
.open > .dropdown-toggle.btn-primary:hover,
.btn-primary:active:focus,
.btn-primary.active:focus,
.open > .dropdown-toggle.btn-primary:focus,
.btn-primary:active.focus,
.btn-primary.active.focus,
.open > .dropdown-toggle.btn-primary.focus {
  color: #fff;
  background-color: #204d74;
  border-color: #122b40;
}
.btn-primary:active,
.btn-primary.active,
.open > .dropdown-toggle.btn-primary {
  background-image: none;
}
.btn-primary.disabled:hover,
.btn-primary[disabled]:hover,
fieldset[disabled] .btn-primary:hover,
.btn-primary.disabled:focus,
.btn-primary[disabled]:focus,
fieldset[disabled] .btn-primary:focus,
.btn-primary.disabled.focus,
.btn-primary[disabled].focus,
fieldset[disabled] .btn-primary.focus {
  background-color: #337ab7;
  border-color: #2e6da4;
}
.btn-primary .badge {
  color: #337ab7;
  background-color: #fff;
}
.btn-success {
  color: #fff;
  background-color: #5cb85c;
  border-color: #4cae4c;
}
.btn-success:focus,
.btn-success.focus {
  color: #fff;
  background-color: #449d44;
  border-color: #255625;
}
.btn-success:hover {
  color: #fff;
  background-color: #449d44;
  border-color: #398439;
}
.btn-success:active,
.btn-success.active,
.open > .dropdown-toggle.btn-success {
  color: #fff;
  background-color: #449d44;
  border-color: #398439;
}
.btn-success:active:hover,
.btn-success.active:hover,
.open > .dropdown-toggle.btn-success:hover,
.btn-success:active:focus,
.btn-success.active:focus,
.open > .dropdown-toggle.btn-success:focus,
.btn-success:active.focus,
.btn-success.active.focus,
.open > .dropdown-toggle.btn-success.focus {
  color: #fff;
  background-color: #398439;
  border-color: #255625;
}
.btn-success:active,
.btn-success.active,
.open > .dropdown-toggle.btn-success {
  background-image: none;
}
.btn-success.disabled:hover,
.btn-success[disabled]:hover,
fieldset[disabled] .btn-success:hover,
.btn-success.disabled:focus,
.btn-success[disabled]:focus,
fieldset[disabled] .btn-success:focus,
.btn-success.disabled.focus,
.btn-success[disabled].focus,
fieldset[disabled] .btn-success.focus {
  background-color: #5cb85c;
  border-color: #4cae4c;
}
.btn-success .badge {
  color: #5cb85c;
  background-color: #fff;
}
.btn-info {
  color: #fff;
  background-color: #5bc0de;
  border-color: #46b8da;
}
.btn-info:focus,
.btn-info.focus {
  color: #fff;
  background-color: #31b0d5;
  border-color: #1b6d85;
}
.btn-info:hover {
  color: #fff;
  background-color: #31b0d5;
  border-color: #269abc;
}
.btn-info:active,
.btn-info.active,
.open > .dropdown-toggle.btn-info {
  color: #fff;
  background-color: #31b0d5;
  border-color: #269abc;
}
.btn-info:active:hover,
.btn-info.active:hover,
.open > .dropdown-toggle.btn-info:hover,
.btn-info:active:focus,
.btn-info.active:focus,
.open > .dropdown-toggle.btn-info:focus,
.btn-info:active.focus,
.btn-info.active.focus,
.open > .dropdown-toggle.btn-info.focus {
  color: #fff;
  background-color: #269abc;
  border-color: #1b6d85;
}
.btn-info:active,
.btn-info.active,
.open > .dropdown-toggle.btn-info {
  background-image: none;
}
.btn-info.disabled:hover,
.btn-info[disabled]:hover,
fieldset[disabled] .btn-info:hover,
.btn-info.disabled:focus,
.btn-info[disabled]:focus,
fieldset[disabled] .btn-info:focus,
.btn-info.disabled.focus,
.btn-info[disabled].focus,
fieldset[disabled] .btn-info.focus {
  background-color: #5bc0de;
  border-color: #46b8da;
}
.btn-info .badge {
  color: #5bc0de;
  background-color: #fff;
}
.btn-warning {
  color: #fff;
  background-color: #f0ad4e;
  border-color: #eea236;
}
.btn-warning:focus,
.btn-warning.focus {
  color: #fff;
  background-color: #ec971f;
  border-color: #985f0d;
}
.btn-warning:hover {
  color: #fff;
  background-color: #ec971f;
  border-color: #d58512;
}
.btn-warning:active,
.btn-warning.active,
.open > .dropdown-toggle.btn-warning {
  color: #fff;
  background-color: #ec971f;
  border-color: #d58512;
}
.btn-warning:active:hover,
.btn-warning.active:hover,
.open > .dropdown-toggle.btn-warning:hover,
.btn-warning:active:focus,
.btn-warning.active:focus,
.open > .dropdown-toggle.btn-warning:focus,
.btn-warning:active.focus,
.btn-warning.active.focus,
.open > .dropdown-toggle.btn-warning.focus {
  color: #fff;
  background-color: #d58512;
  border-color: #985f0d;
}
.btn-warning:active,
.btn-warning.active,
.open > .dropdown-toggle.btn-warning {
  background-image: none;
}
.btn-warning.disabled:hover,
.btn-warning[disabled]:hover,
fieldset[disabled] .btn-warning:hover,
.btn-warning.disabled:focus,
.btn-warning[disabled]:focus,
fieldset[disabled] .btn-warning:focus,
.btn-warning.disabled.focus,
.btn-warning[disabled].focus,
fieldset[disabled] .btn-warning.focus {
  background-color: #f0ad4e;
  border-color: #eea236;
}
.btn-warning .badge {
  color: #f0ad4e;
  background-color: #fff;
}
.btn-danger {
  color: #fff;
  background-color: #d9534f;
  border-color: #d43f3a;
}
.btn-danger:focus,
.btn-danger.focus {
  color: #fff;
  background-color: #c9302c;
  border-color: #761c19;
}
.btn-danger:hover {
  color: #fff;
  background-color: #c9302c;
  border-color: #ac2925;
}
.btn-danger:active,
.btn-danger.active,
.open > .dropdown-toggle.btn-danger {
  color: #fff;
  background-color: #c9302c;
  border-color: #ac2925;
}
.btn-danger:active:hover,
.btn-danger.active:hover,
.open > .dropdown-toggle.btn-danger:hover,
.btn-danger:active:focus,
.btn-danger.active:focus,
.open > .dropdown-toggle.btn-danger:focus,
.btn-danger:active.focus,
.btn-danger.active.focus,
.open > .dropdown-toggle.btn-danger.focus {
  color: #fff;
  background-color: #ac2925;
  border-color: #761c19;
}
.btn-danger:active,
.btn-danger.active,
.open > .dropdown-toggle.btn-danger {
  background-image: none;
}
.btn-danger.disabled:hover,
.btn-danger[disabled]:hover,
fieldset[disabled] .btn-danger:hover,
.btn-danger.disabled:focus,
.btn-danger[disabled]:focus,
fieldset[disabled] .btn-danger:focus,
.btn-danger.disabled.focus,
.btn-danger[disabled].focus,
fieldset[disabled] .btn-danger.focus {
  background-color: #d9534f;
  border-color: #d43f3a;
}
.btn-danger .badge {
  color: #d9534f;
  background-color: #fff;
}
.btn-link {
  color: #337ab7;
  font-weight: normal;
  border-radius: 0;
}
.btn-link,
.btn-link:active,
.btn-link.active,
.btn-link[disabled],
fieldset[disabled] .btn-link {
  background-color: transparent;
  -webkit-box-shadow: none;
  box-shadow: none;
}
.btn-link,
.btn-link:hover,
.btn-link:focus,
.btn-link:active {
  border-color: transparent;
}
.btn-link:hover,
.btn-link:focus {
  color: #23527c;
  text-decoration: underline;
  background-color: transparent;
}
.btn-link[disabled]:hover,
fieldset[disabled] .btn-link:hover,
.btn-link[disabled]:focus,
fieldset[disabled] .btn-link:focus {
  color: #777777;
  text-decoration: none;
}
.btn-lg,
.btn-group-lg > .btn {
  padding: 10px 16px;
  font-size: 17px;
  line-height: 1.3333333;
  border-radius: 3px;
}
.btn-sm,
.btn-group-sm > .btn {
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
}
.btn-xs,
.btn-group-xs > .btn {
  padding: 1px 5px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
}
.btn-block {
  display: block;
  width: 100%;
}
.btn-block + .btn-block {
  margin-top: 5px;
}
input[type="submit"].btn-block,
input[type="reset"].btn-block,
input[type="button"].btn-block {
  width: 100%;
}
.fade {
  opacity: 0;
  -webkit-transition: opacity 0.15s linear;
  -o-transition: opacity 0.15s linear;
  transition: opacity 0.15s linear;
}
.fade.in {
  opacity: 1;
}
.collapse {
  display: none;
}
.collapse.in {
  display: block;
}
tr.collapse.in {
  display: table-row;
}
tbody.collapse.in {
  display: table-row-group;
}
.collapsing {
  position: relative;
  height: 0;
  overflow: hidden;
  -webkit-transition-property: height, visibility;
  transition-property: height, visibility;
  -webkit-transition-duration: 0.35s;
  transition-duration: 0.35s;
  -webkit-transition-timing-function: ease;
  transition-timing-function: ease;
}
.caret {
  display: inline-block;
  width: 0;
  height: 0;
  margin-left: 2px;
  vertical-align: middle;
  border-top: 4px dashed;
  border-top: 4px solid \9;
  border-right: 4px solid transparent;
  border-left: 4px solid transparent;
}
.dropup,
.dropdown {
  position: relative;
}
.dropdown-toggle:focus {
  outline: 0;
}
.dropdown-menu {
  position: absolute;
  top: 100%;
  left: 0;
  z-index: 1000;
  display: none;
  float: left;
  min-width: 160px;
  padding: 5px 0;
  margin: 2px 0 0;
  list-style: none;
  font-size: 13px;
  text-align: left;
  background-color: #fff;
  border: 1px solid #ccc;
  border: 1px solid rgba(0, 0, 0, 0.15);
  border-radius: 2px;
  -webkit-box-shadow: 0 6px 12px rgba(0, 0, 0, 0.175);
  box-shadow: 0 6px 12px rgba(0, 0, 0, 0.175);
  background-clip: padding-box;
}
.dropdown-menu.pull-right {
  right: 0;
  left: auto;
}
.dropdown-menu .divider {
  height: 1px;
  margin: 8px 0;
  overflow: hidden;
  background-color: #e5e5e5;
}
.dropdown-menu > li > a {
  display: block;
  padding: 3px 20px;
  clear: both;
  font-weight: normal;
  line-height: 1.42857143;
  color: #333333;
  white-space: nowrap;
}
.dropdown-menu > li > a:hover,
.dropdown-menu > li > a:focus {
  text-decoration: none;
  color: #262626;
  background-color: #f5f5f5;
}
.dropdown-menu > .active > a,
.dropdown-menu > .active > a:hover,
.dropdown-menu > .active > a:focus {
  color: #fff;
  text-decoration: none;
  outline: 0;
  background-color: #337ab7;
}
.dropdown-menu > .disabled > a,
.dropdown-menu > .disabled > a:hover,
.dropdown-menu > .disabled > a:focus {
  color: #777777;
}
.dropdown-menu > .disabled > a:hover,
.dropdown-menu > .disabled > a:focus {
  text-decoration: none;
  background-color: transparent;
  background-image: none;
  filter: progid:DXImageTransform.Microsoft.gradient(enabled = false);
  cursor: not-allowed;
}
.open > .dropdown-menu {
  display: block;
}
.open > a {
  outline: 0;
}
.dropdown-menu-right {
  left: auto;
  right: 0;
}
.dropdown-menu-left {
  left: 0;
  right: auto;
}
.dropdown-header {
  display: block;
  padding: 3px 20px;
  font-size: 12px;
  line-height: 1.42857143;
  color: #777777;
  white-space: nowrap;
}
.dropdown-backdrop {
  position: fixed;
  left: 0;
  right: 0;
  bottom: 0;
  top: 0;
  z-index: 990;
}
.pull-right > .dropdown-menu {
  right: 0;
  left: auto;
}
.dropup .caret,
.navbar-fixed-bottom .dropdown .caret {
  border-top: 0;
  border-bottom: 4px dashed;
  border-bottom: 4px solid \9;
  content: "";
}
.dropup .dropdown-menu,
.navbar-fixed-bottom .dropdown .dropdown-menu {
  top: auto;
  bottom: 100%;
  margin-bottom: 2px;
}
@media (min-width: 541px) {
  .navbar-right .dropdown-menu {
    left: auto;
    right: 0;
  }
  .navbar-right .dropdown-menu-left {
    left: 0;
    right: auto;
  }
}
.btn-group,
.btn-group-vertical {
  position: relative;
  display: inline-block;
  vertical-align: middle;
}
.btn-group > .btn,
.btn-group-vertical > .btn {
  position: relative;
  float: left;
}
.btn-group > .btn:hover,
.btn-group-vertical > .btn:hover,
.btn-group > .btn:focus,
.btn-group-vertical > .btn:focus,
.btn-group > .btn:active,
.btn-group-vertical > .btn:active,
.btn-group > .btn.active,
.btn-group-vertical > .btn.active {
  z-index: 2;
}
.btn-group .btn + .btn,
.btn-group .btn + .btn-group,
.btn-group .btn-group + .btn,
.btn-group .btn-group + .btn-group {
  margin-left: -1px;
}
.btn-toolbar {
  margin-left: -5px;
}
.btn-toolbar .btn,
.btn-toolbar .btn-group,
.btn-toolbar .input-group {
  float: left;
}
.btn-toolbar > .btn,
.btn-toolbar > .btn-group,
.btn-toolbar > .input-group {
  margin-left: 5px;
}
.btn-group > .btn:not(:first-child):not(:last-child):not(.dropdown-toggle) {
  border-radius: 0;
}
.btn-group > .btn:first-child {
  margin-left: 0;
}
.btn-group > .btn:first-child:not(:last-child):not(.dropdown-toggle) {
  border-bottom-right-radius: 0;
  border-top-right-radius: 0;
}
.btn-group > .btn:last-child:not(:first-child),
.btn-group > .dropdown-toggle:not(:first-child) {
  border-bottom-left-radius: 0;
  border-top-left-radius: 0;
}
.btn-group > .btn-group {
  float: left;
}
.btn-group > .btn-group:not(:first-child):not(:last-child) > .btn {
  border-radius: 0;
}
.btn-group > .btn-group:first-child:not(:last-child) > .btn:last-child,
.btn-group > .btn-group:first-child:not(:last-child) > .dropdown-toggle {
  border-bottom-right-radius: 0;
  border-top-right-radius: 0;
}
.btn-group > .btn-group:last-child:not(:first-child) > .btn:first-child {
  border-bottom-left-radius: 0;
  border-top-left-radius: 0;
}
.btn-group .dropdown-toggle:active,
.btn-group.open .dropdown-toggle {
  outline: 0;
}
.btn-group > .btn + .dropdown-toggle {
  padding-left: 8px;
  padding-right: 8px;
}
.btn-group > .btn-lg + .dropdown-toggle {
  padding-left: 12px;
  padding-right: 12px;
}
.btn-group.open .dropdown-toggle {
  -webkit-box-shadow: inset 0 3px 5px rgba(0, 0, 0, 0.125);
  box-shadow: inset 0 3px 5px rgba(0, 0, 0, 0.125);
}
.btn-group.open .dropdown-toggle.btn-link {
  -webkit-box-shadow: none;
  box-shadow: none;
}
.btn .caret {
  margin-left: 0;
}
.btn-lg .caret {
  border-width: 5px 5px 0;
  border-bottom-width: 0;
}
.dropup .btn-lg .caret {
  border-width: 0 5px 5px;
}
.btn-group-vertical > .btn,
.btn-group-vertical > .btn-group,
.btn-group-vertical > .btn-group > .btn {
  display: block;
  float: none;
  width: 100%;
  max-width: 100%;
}
.btn-group-vertical > .btn-group > .btn {
  float: none;
}
.btn-group-vertical > .btn + .btn,
.btn-group-vertical > .btn + .btn-group,
.btn-group-vertical > .btn-group + .btn,
.btn-group-vertical > .btn-group + .btn-group {
  margin-top: -1px;
  margin-left: 0;
}
.btn-group-vertical > .btn:not(:first-child):not(:last-child) {
  border-radius: 0;
}
.btn-group-vertical > .btn:first-child:not(:last-child) {
  border-top-right-radius: 2px;
  border-top-left-radius: 2px;
  border-bottom-right-radius: 0;
  border-bottom-left-radius: 0;
}
.btn-group-vertical > .btn:last-child:not(:first-child) {
  border-top-right-radius: 0;
  border-top-left-radius: 0;
  border-bottom-right-radius: 2px;
  border-bottom-left-radius: 2px;
}
.btn-group-vertical > .btn-group:not(:first-child):not(:last-child) > .btn {
  border-radius: 0;
}
.btn-group-vertical > .btn-group:first-child:not(:last-child) > .btn:last-child,
.btn-group-vertical > .btn-group:first-child:not(:last-child) > .dropdown-toggle {
  border-bottom-right-radius: 0;
  border-bottom-left-radius: 0;
}
.btn-group-vertical > .btn-group:last-child:not(:first-child) > .btn:first-child {
  border-top-right-radius: 0;
  border-top-left-radius: 0;
}
.btn-group-justified {
  display: table;
  width: 100%;
  table-layout: fixed;
  border-collapse: separate;
}
.btn-group-justified > .btn,
.btn-group-justified > .btn-group {
  float: none;
  display: table-cell;
  width: 1%;
}
.btn-group-justified > .btn-group .btn {
  width: 100%;
}
.btn-group-justified > .btn-group .dropdown-menu {
  left: auto;
}
[data-toggle="buttons"] > .btn input[type="radio"],
[data-toggle="buttons"] > .btn-group > .btn input[type="radio"],
[data-toggle="buttons"] > .btn input[type="checkbox"],
[data-toggle="buttons"] > .btn-group > .btn input[type="checkbox"] {
  position: absolute;
  clip: rect(0, 0, 0, 0);
  pointer-events: none;
}
.input-group {
  position: relative;
  display: table;
  border-collapse: separate;
}
.input-group[class*="col-"] {
  float: none;
  padding-left: 0;
  padding-right: 0;
}
.input-group .form-control {
  position: relative;
  z-index: 2;
  float: left;
  width: 100%;
  margin-bottom: 0;
}
.input-group .form-control:focus {
  z-index: 3;
}
.input-group-lg > .form-control,
.input-group-lg > .input-group-addon,
.input-group-lg > .input-group-btn > .btn {
  height: 45px;
  padding: 10px 16px;
  font-size: 17px;
  line-height: 1.3333333;
  border-radius: 3px;
}
select.input-group-lg > .form-control,
select.input-group-lg > .input-group-addon,
select.input-group-lg > .input-group-btn > .btn {
  height: 45px;
  line-height: 45px;
}
textarea.input-group-lg > .form-control,
textarea.input-group-lg > .input-group-addon,
textarea.input-group-lg > .input-group-btn > .btn,
select[multiple].input-group-lg > .form-control,
select[multiple].input-group-lg > .input-group-addon,
select[multiple].input-group-lg > .input-group-btn > .btn {
  height: auto;
}
.input-group-sm > .form-control,
.input-group-sm > .input-group-addon,
.input-group-sm > .input-group-btn > .btn {
  height: 30px;
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
}
select.input-group-sm > .form-control,
select.input-group-sm > .input-group-addon,
select.input-group-sm > .input-group-btn > .btn {
  height: 30px;
  line-height: 30px;
}
textarea.input-group-sm > .form-control,
textarea.input-group-sm > .input-group-addon,
textarea.input-group-sm > .input-group-btn > .btn,
select[multiple].input-group-sm > .form-control,
select[multiple].input-group-sm > .input-group-addon,
select[multiple].input-group-sm > .input-group-btn > .btn {
  height: auto;
}
.input-group-addon,
.input-group-btn,
.input-group .form-control {
  display: table-cell;
}
.input-group-addon:not(:first-child):not(:last-child),
.input-group-btn:not(:first-child):not(:last-child),
.input-group .form-control:not(:first-child):not(:last-child) {
  border-radius: 0;
}
.input-group-addon,
.input-group-btn {
  width: 1%;
  white-space: nowrap;
  vertical-align: middle;
}
.input-group-addon {
  padding: 6px 12px;
  font-size: 13px;
  font-weight: normal;
  line-height: 1;
  color: #555555;
  text-align: center;
  background-color: #eeeeee;
  border: 1px solid #ccc;
  border-radius: 2px;
}
.input-group-addon.input-sm {
  padding: 5px 10px;
  font-size: 12px;
  border-radius: 1px;
}
.input-group-addon.input-lg {
  padding: 10px 16px;
  font-size: 17px;
  border-radius: 3px;
}
.input-group-addon input[type="radio"],
.input-group-addon input[type="checkbox"] {
  margin-top: 0;
}
.input-group .form-control:first-child,
.input-group-addon:first-child,
.input-group-btn:first-child > .btn,
.input-group-btn:first-child > .btn-group > .btn,
.input-group-btn:first-child > .dropdown-toggle,
.input-group-btn:last-child > .btn:not(:last-child):not(.dropdown-toggle),
.input-group-btn:last-child > .btn-group:not(:last-child) > .btn {
  border-bottom-right-radius: 0;
  border-top-right-radius: 0;
}
.input-group-addon:first-child {
  border-right: 0;
}
.input-group .form-control:last-child,
.input-group-addon:last-child,
.input-group-btn:last-child > .btn,
.input-group-btn:last-child > .btn-group > .btn,
.input-group-btn:last-child > .dropdown-toggle,
.input-group-btn:first-child > .btn:not(:first-child),
.input-group-btn:first-child > .btn-group:not(:first-child) > .btn {
  border-bottom-left-radius: 0;
  border-top-left-radius: 0;
}
.input-group-addon:last-child {
  border-left: 0;
}
.input-group-btn {
  position: relative;
  font-size: 0;
  white-space: nowrap;
}
.input-group-btn > .btn {
  position: relative;
}
.input-group-btn > .btn + .btn {
  margin-left: -1px;
}
.input-group-btn > .btn:hover,
.input-group-btn > .btn:focus,
.input-group-btn > .btn:active {
  z-index: 2;
}
.input-group-btn:first-child > .btn,
.input-group-btn:first-child > .btn-group {
  margin-right: -1px;
}
.input-group-btn:last-child > .btn,
.input-group-btn:last-child > .btn-group {
  z-index: 2;
  margin-left: -1px;
}
.nav {
  margin-bottom: 0;
  padding-left: 0;
  list-style: none;
}
.nav > li {
  position: relative;
  display: block;
}
.nav > li > a {
  position: relative;
  display: block;
  padding: 10px 15px;
}
.nav > li > a:hover,
.nav > li > a:focus {
  text-decoration: none;
  background-color: #eeeeee;
}
.nav > li.disabled > a {
  color: #777777;
}
.nav > li.disabled > a:hover,
.nav > li.disabled > a:focus {
  color: #777777;
  text-decoration: none;
  background-color: transparent;
  cursor: not-allowed;
}
.nav .open > a,
.nav .open > a:hover,
.nav .open > a:focus {
  background-color: #eeeeee;
  border-color: #337ab7;
}
.nav .nav-divider {
  height: 1px;
  margin: 8px 0;
  overflow: hidden;
  background-color: #e5e5e5;
}
.nav > li > a > img {
  max-width: none;
}
.nav-tabs {
  border-bottom: 1px solid #ddd;
}
.nav-tabs > li {
  float: left;
  margin-bottom: -1px;
}
.nav-tabs > li > a {
  margin-right: 2px;
  line-height: 1.42857143;
  border: 1px solid transparent;
  border-radius: 2px 2px 0 0;
}
.nav-tabs > li > a:hover {
  border-color: #eeeeee #eeeeee #ddd;
}
.nav-tabs > li.active > a,
.nav-tabs > li.active > a:hover,
.nav-tabs > li.active > a:focus {
  color: #555555;
  background-color: #fff;
  border: 1px solid #ddd;
  border-bottom-color: transparent;
  cursor: default;
}
.nav-tabs.nav-justified {
  width: 100%;
  border-bottom: 0;
}
.nav-tabs.nav-justified > li {
  float: none;
}
.nav-tabs.nav-justified > li > a {
  text-align: center;
  margin-bottom: 5px;
}
.nav-tabs.nav-justified > .dropdown .dropdown-menu {
  top: auto;
  left: auto;
}
@media (min-width: 768px) {
  .nav-tabs.nav-justified > li {
    display: table-cell;
    width: 1%;
  }
  .nav-tabs.nav-justified > li > a {
    margin-bottom: 0;
  }
}
.nav-tabs.nav-justified > li > a {
  margin-right: 0;
  border-radius: 2px;
}
.nav-tabs.nav-justified > .active > a,
.nav-tabs.nav-justified > .active > a:hover,
.nav-tabs.nav-justified > .active > a:focus {
  border: 1px solid #ddd;
}
@media (min-width: 768px) {
  .nav-tabs.nav-justified > li > a {
    border-bottom: 1px solid #ddd;
    border-radius: 2px 2px 0 0;
  }
  .nav-tabs.nav-justified > .active > a,
  .nav-tabs.nav-justified > .active > a:hover,
  .nav-tabs.nav-justified > .active > a:focus {
    border-bottom-color: #fff;
  }
}
.nav-pills > li {
  float: left;
}
.nav-pills > li > a {
  border-radius: 2px;
}
.nav-pills > li + li {
  margin-left: 2px;
}
.nav-pills > li.active > a,
.nav-pills > li.active > a:hover,
.nav-pills > li.active > a:focus {
  color: #fff;
  background-color: #337ab7;
}
.nav-stacked > li {
  float: none;
}
.nav-stacked > li + li {
  margin-top: 2px;
  margin-left: 0;
}
.nav-justified {
  width: 100%;
}
.nav-justified > li {
  float: none;
}
.nav-justified > li > a {
  text-align: center;
  margin-bottom: 5px;
}
.nav-justified > .dropdown .dropdown-menu {
  top: auto;
  left: auto;
}
@media (min-width: 768px) {
  .nav-justified > li {
    display: table-cell;
    width: 1%;
  }
  .nav-justified > li > a {
    margin-bottom: 0;
  }
}
.nav-tabs-justified {
  border-bottom: 0;
}
.nav-tabs-justified > li > a {
  margin-right: 0;
  border-radius: 2px;
}
.nav-tabs-justified > .active > a,
.nav-tabs-justified > .active > a:hover,
.nav-tabs-justified > .active > a:focus {
  border: 1px solid #ddd;
}
@media (min-width: 768px) {
  .nav-tabs-justified > li > a {
    border-bottom: 1px solid #ddd;
    border-radius: 2px 2px 0 0;
  }
  .nav-tabs-justified > .active > a,
  .nav-tabs-justified > .active > a:hover,
  .nav-tabs-justified > .active > a:focus {
    border-bottom-color: #fff;
  }
}
.tab-content > .tab-pane {
  display: none;
}
.tab-content > .active {
  display: block;
}
.nav-tabs .dropdown-menu {
  margin-top: -1px;
  border-top-right-radius: 0;
  border-top-left-radius: 0;
}
.navbar {
  position: relative;
  min-height: 30px;
  margin-bottom: 18px;
  border: 1px solid transparent;
}
@media (min-width: 541px) {
  .navbar {
    border-radius: 2px;
  }
}
@media (min-width: 541px) {
  .navbar-header {
    float: left;
  }
}
.navbar-collapse {
  overflow-x: visible;
  padding-right: 0px;
  padding-left: 0px;
  border-top: 1px solid transparent;
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.1);
  -webkit-overflow-scrolling: touch;
}
.navbar-collapse.in {
  overflow-y: auto;
}
@media (min-width: 541px) {
  .navbar-collapse {
    width: auto;
    border-top: 0;
    box-shadow: none;
  }
  .navbar-collapse.collapse {
    display: block !important;
    height: auto !important;
    padding-bottom: 0;
    overflow: visible !important;
  }
  .navbar-collapse.in {
    overflow-y: visible;
  }
  .navbar-fixed-top .navbar-collapse,
  .navbar-static-top .navbar-collapse,
  .navbar-fixed-bottom .navbar-collapse {
    padding-left: 0;
    padding-right: 0;
  }
}
.navbar-fixed-top .navbar-collapse,
.navbar-fixed-bottom .navbar-collapse {
  max-height: 340px;
}
@media (max-device-width: 540px) and (orientation: landscape) {
  .navbar-fixed-top .navbar-collapse,
  .navbar-fixed-bottom .navbar-collapse {
    max-height: 200px;
  }
}
.container > .navbar-header,
.container-fluid > .navbar-header,
.container > .navbar-collapse,
.container-fluid > .navbar-collapse {
  margin-right: 0px;
  margin-left: 0px;
}
@media (min-width: 541px) {
  .container > .navbar-header,
  .container-fluid > .navbar-header,
  .container > .navbar-collapse,
  .container-fluid > .navbar-collapse {
    margin-right: 0;
    margin-left: 0;
  }
}
.navbar-static-top {
  z-index: 1000;
  border-width: 0 0 1px;
}
@media (min-width: 541px) {
  .navbar-static-top {
    border-radius: 0;
  }
}
.navbar-fixed-top,
.navbar-fixed-bottom {
  position: fixed;
  right: 0;
  left: 0;
  z-index: 1030;
}
@media (min-width: 541px) {
  .navbar-fixed-top,
  .navbar-fixed-bottom {
    border-radius: 0;
  }
}
.navbar-fixed-top {
  top: 0;
  border-width: 0 0 1px;
}
.navbar-fixed-bottom {
  bottom: 0;
  margin-bottom: 0;
  border-width: 1px 0 0;
}
.navbar-brand {
  float: left;
  padding: 6px 0px;
  font-size: 17px;
  line-height: 18px;
  height: 30px;
}
.navbar-brand:hover,
.navbar-brand:focus {
  text-decoration: none;
}
.navbar-brand > img {
  display: block;
}
@media (min-width: 541px) {
  .navbar > .container .navbar-brand,
  .navbar > .container-fluid .navbar-brand {
    margin-left: 0px;
  }
}
.navbar-toggle {
  position: relative;
  float: right;
  margin-right: 0px;
  padding: 9px 10px;
  margin-top: -2px;
  margin-bottom: -2px;
  background-color: transparent;
  background-image: none;
  border: 1px solid transparent;
  border-radius: 2px;
}
.navbar-toggle:focus {
  outline: 0;
}
.navbar-toggle .icon-bar {
  display: block;
  width: 22px;
  height: 2px;
  border-radius: 1px;
}
.navbar-toggle .icon-bar + .icon-bar {
  margin-top: 4px;
}
@media (min-width: 541px) {
  .navbar-toggle {
    display: none;
  }
}
.navbar-nav {
  margin: 3px 0px;
}
.navbar-nav > li > a {
  padding-top: 10px;
  padding-bottom: 10px;
  line-height: 18px;
}
@media (max-width: 540px) {
  .navbar-nav .open .dropdown-menu {
    position: static;
    float: none;
    width: auto;
    margin-top: 0;
    background-color: transparent;
    border: 0;
    box-shadow: none;
  }
  .navbar-nav .open .dropdown-menu > li > a,
  .navbar-nav .open .dropdown-menu .dropdown-header {
    padding: 5px 15px 5px 25px;
  }
  .navbar-nav .open .dropdown-menu > li > a {
    line-height: 18px;
  }
  .navbar-nav .open .dropdown-menu > li > a:hover,
  .navbar-nav .open .dropdown-menu > li > a:focus {
    background-image: none;
  }
}
@media (min-width: 541px) {
  .navbar-nav {
    float: left;
    margin: 0;
  }
  .navbar-nav > li {
    float: left;
  }
  .navbar-nav > li > a {
    padding-top: 6px;
    padding-bottom: 6px;
  }
}
.navbar-form {
  margin-left: 0px;
  margin-right: 0px;
  padding: 10px 0px;
  border-top: 1px solid transparent;
  border-bottom: 1px solid transparent;
  -webkit-box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.1), 0 1px 0 rgba(255, 255, 255, 0.1);
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.1), 0 1px 0 rgba(255, 255, 255, 0.1);
  margin-top: -1px;
  margin-bottom: -1px;
}
@media (min-width: 768px) {
  .navbar-form .form-group {
    display: inline-block;
    margin-bottom: 0;
    vertical-align: middle;
  }
  .navbar-form .form-control {
    display: inline-block;
    width: auto;
    vertical-align: middle;
  }
  .navbar-form .form-control-static {
    display: inline-block;
  }
  .navbar-form .input-group {
    display: inline-table;
    vertical-align: middle;
  }
  .navbar-form .input-group .input-group-addon,
  .navbar-form .input-group .input-group-btn,
  .navbar-form .input-group .form-control {
    width: auto;
  }
  .navbar-form .input-group > .form-control {
    width: 100%;
  }
  .navbar-form .control-label {
    margin-bottom: 0;
    vertical-align: middle;
  }
  .navbar-form .radio,
  .navbar-form .checkbox {
    display: inline-block;
    margin-top: 0;
    margin-bottom: 0;
    vertical-align: middle;
  }
  .navbar-form .radio label,
  .navbar-form .checkbox label {
    padding-left: 0;
  }
  .navbar-form .radio input[type="radio"],
  .navbar-form .checkbox input[type="checkbox"] {
    position: relative;
    margin-left: 0;
  }
  .navbar-form .has-feedback .form-control-feedback {
    top: 0;
  }
}
@media (max-width: 540px) {
  .navbar-form .form-group {
    margin-bottom: 5px;
  }
  .navbar-form .form-group:last-child {
    margin-bottom: 0;
  }
}
@media (min-width: 541px) {
  .navbar-form {
    width: auto;
    border: 0;
    margin-left: 0;
    margin-right: 0;
    padding-top: 0;
    padding-bottom: 0;
    -webkit-box-shadow: none;
    box-shadow: none;
  }
}
.navbar-nav > li > .dropdown-menu {
  margin-top: 0;
  border-top-right-radius: 0;
  border-top-left-radius: 0;
}
.navbar-fixed-bottom .navbar-nav > li > .dropdown-menu {
  margin-bottom: 0;
  border-top-right-radius: 2px;
  border-top-left-radius: 2px;
  border-bottom-right-radius: 0;
  border-bottom-left-radius: 0;
}
.navbar-btn {
  margin-top: -1px;
  margin-bottom: -1px;
}
.navbar-btn.btn-sm {
  margin-top: 0px;
  margin-bottom: 0px;
}
.navbar-btn.btn-xs {
  margin-top: 4px;
  margin-bottom: 4px;
}
.navbar-text {
  margin-top: 6px;
  margin-bottom: 6px;
}
@media (min-width: 541px) {
  .navbar-text {
    float: left;
    margin-left: 0px;
    margin-right: 0px;
  }
}
@media (min-width: 541px) {
  .navbar-left {
    float: left !important;
    float: left;
  }
  .navbar-right {
    float: right !important;
    float: right;
    margin-right: 0px;
  }
  .navbar-right ~ .navbar-right {
    margin-right: 0;
  }
}
.navbar-default {
  background-color: #f8f8f8;
  border-color: #e7e7e7;
}
.navbar-default .navbar-brand {
  color: #777;
}
.navbar-default .navbar-brand:hover,
.navbar-default .navbar-brand:focus {
  color: #5e5e5e;
  background-color: transparent;
}
.navbar-default .navbar-text {
  color: #777;
}
.navbar-default .navbar-nav > li > a {
  color: #777;
}
.navbar-default .navbar-nav > li > a:hover,
.navbar-default .navbar-nav > li > a:focus {
  color: #333;
  background-color: transparent;
}
.navbar-default .navbar-nav > .active > a,
.navbar-default .navbar-nav > .active > a:hover,
.navbar-default .navbar-nav > .active > a:focus {
  color: #555;
  background-color: #e7e7e7;
}
.navbar-default .navbar-nav > .disabled > a,
.navbar-default .navbar-nav > .disabled > a:hover,
.navbar-default .navbar-nav > .disabled > a:focus {
  color: #ccc;
  background-color: transparent;
}
.navbar-default .navbar-toggle {
  border-color: #ddd;
}
.navbar-default .navbar-toggle:hover,
.navbar-default .navbar-toggle:focus {
  background-color: #ddd;
}
.navbar-default .navbar-toggle .icon-bar {
  background-color: #888;
}
.navbar-default .navbar-collapse,
.navbar-default .navbar-form {
  border-color: #e7e7e7;
}
.navbar-default .navbar-nav > .open > a,
.navbar-default .navbar-nav > .open > a:hover,
.navbar-default .navbar-nav > .open > a:focus {
  background-color: #e7e7e7;
  color: #555;
}
@media (max-width: 540px) {
  .navbar-default .navbar-nav .open .dropdown-menu > li > a {
    color: #777;
  }
  .navbar-default .navbar-nav .open .dropdown-menu > li > a:hover,
  .navbar-default .navbar-nav .open .dropdown-menu > li > a:focus {
    color: #333;
    background-color: transparent;
  }
  .navbar-default .navbar-nav .open .dropdown-menu > .active > a,
  .navbar-default .navbar-nav .open .dropdown-menu > .active > a:hover,
  .navbar-default .navbar-nav .open .dropdown-menu > .active > a:focus {
    color: #555;
    background-color: #e7e7e7;
  }
  .navbar-default .navbar-nav .open .dropdown-menu > .disabled > a,
  .navbar-default .navbar-nav .open .dropdown-menu > .disabled > a:hover,
  .navbar-default .navbar-nav .open .dropdown-menu > .disabled > a:focus {
    color: #ccc;
    background-color: transparent;
  }
}
.navbar-default .navbar-link {
  color: #777;
}
.navbar-default .navbar-link:hover {
  color: #333;
}
.navbar-default .btn-link {
  color: #777;
}
.navbar-default .btn-link:hover,
.navbar-default .btn-link:focus {
  color: #333;
}
.navbar-default .btn-link[disabled]:hover,
fieldset[disabled] .navbar-default .btn-link:hover,
.navbar-default .btn-link[disabled]:focus,
fieldset[disabled] .navbar-default .btn-link:focus {
  color: #ccc;
}
.navbar-inverse {
  background-color: #222;
  border-color: #080808;
}
.navbar-inverse .navbar-brand {
  color: #9d9d9d;
}
.navbar-inverse .navbar-brand:hover,
.navbar-inverse .navbar-brand:focus {
  color: #fff;
  background-color: transparent;
}
.navbar-inverse .navbar-text {
  color: #9d9d9d;
}
.navbar-inverse .navbar-nav > li > a {
  color: #9d9d9d;
}
.navbar-inverse .navbar-nav > li > a:hover,
.navbar-inverse .navbar-nav > li > a:focus {
  color: #fff;
  background-color: transparent;
}
.navbar-inverse .navbar-nav > .active > a,
.navbar-inverse .navbar-nav > .active > a:hover,
.navbar-inverse .navbar-nav > .active > a:focus {
  color: #fff;
  background-color: #080808;
}
.navbar-inverse .navbar-nav > .disabled > a,
.navbar-inverse .navbar-nav > .disabled > a:hover,
.navbar-inverse .navbar-nav > .disabled > a:focus {
  color: #444;
  background-color: transparent;
}
.navbar-inverse .navbar-toggle {
  border-color: #333;
}
.navbar-inverse .navbar-toggle:hover,
.navbar-inverse .navbar-toggle:focus {
  background-color: #333;
}
.navbar-inverse .navbar-toggle .icon-bar {
  background-color: #fff;
}
.navbar-inverse .navbar-collapse,
.navbar-inverse .navbar-form {
  border-color: #101010;
}
.navbar-inverse .navbar-nav > .open > a,
.navbar-inverse .navbar-nav > .open > a:hover,
.navbar-inverse .navbar-nav > .open > a:focus {
  background-color: #080808;
  color: #fff;
}
@media (max-width: 540px) {
  .navbar-inverse .navbar-nav .open .dropdown-menu > .dropdown-header {
    border-color: #080808;
  }
  .navbar-inverse .navbar-nav .open .dropdown-menu .divider {
    background-color: #080808;
  }
  .navbar-inverse .navbar-nav .open .dropdown-menu > li > a {
    color: #9d9d9d;
  }
  .navbar-inverse .navbar-nav .open .dropdown-menu > li > a:hover,
  .navbar-inverse .navbar-nav .open .dropdown-menu > li > a:focus {
    color: #fff;
    background-color: transparent;
  }
  .navbar-inverse .navbar-nav .open .dropdown-menu > .active > a,
  .navbar-inverse .navbar-nav .open .dropdown-menu > .active > a:hover,
  .navbar-inverse .navbar-nav .open .dropdown-menu > .active > a:focus {
    color: #fff;
    background-color: #080808;
  }
  .navbar-inverse .navbar-nav .open .dropdown-menu > .disabled > a,
  .navbar-inverse .navbar-nav .open .dropdown-menu > .disabled > a:hover,
  .navbar-inverse .navbar-nav .open .dropdown-menu > .disabled > a:focus {
    color: #444;
    background-color: transparent;
  }
}
.navbar-inverse .navbar-link {
  color: #9d9d9d;
}
.navbar-inverse .navbar-link:hover {
  color: #fff;
}
.navbar-inverse .btn-link {
  color: #9d9d9d;
}
.navbar-inverse .btn-link:hover,
.navbar-inverse .btn-link:focus {
  color: #fff;
}
.navbar-inverse .btn-link[disabled]:hover,
fieldset[disabled] .navbar-inverse .btn-link:hover,
.navbar-inverse .btn-link[disabled]:focus,
fieldset[disabled] .navbar-inverse .btn-link:focus {
  color: #444;
}
.breadcrumb {
  padding: 8px 15px;
  margin-bottom: 18px;
  list-style: none;
  background-color: #f5f5f5;
  border-radius: 2px;
}
.breadcrumb > li {
  display: inline-block;
}
.breadcrumb > li + li:before {
  content: "/\00a0";
  padding: 0 5px;
  color: #5e5e5e;
}
.breadcrumb > .active {
  color: #777777;
}
.pagination {
  display: inline-block;
  padding-left: 0;
  margin: 18px 0;
  border-radius: 2px;
}
.pagination > li {
  display: inline;
}
.pagination > li > a,
.pagination > li > span {
  position: relative;
  float: left;
  padding: 6px 12px;
  line-height: 1.42857143;
  text-decoration: none;
  color: #337ab7;
  background-color: #fff;
  border: 1px solid #ddd;
  margin-left: -1px;
}
.pagination > li:first-child > a,
.pagination > li:first-child > span {
  margin-left: 0;
  border-bottom-left-radius: 2px;
  border-top-left-radius: 2px;
}
.pagination > li:last-child > a,
.pagination > li:last-child > span {
  border-bottom-right-radius: 2px;
  border-top-right-radius: 2px;
}
.pagination > li > a:hover,
.pagination > li > span:hover,
.pagination > li > a:focus,
.pagination > li > span:focus {
  z-index: 2;
  color: #23527c;
  background-color: #eeeeee;
  border-color: #ddd;
}
.pagination > .active > a,
.pagination > .active > span,
.pagination > .active > a:hover,
.pagination > .active > span:hover,
.pagination > .active > a:focus,
.pagination > .active > span:focus {
  z-index: 3;
  color: #fff;
  background-color: #337ab7;
  border-color: #337ab7;
  cursor: default;
}
.pagination > .disabled > span,
.pagination > .disabled > span:hover,
.pagination > .disabled > span:focus,
.pagination > .disabled > a,
.pagination > .disabled > a:hover,
.pagination > .disabled > a:focus {
  color: #777777;
  background-color: #fff;
  border-color: #ddd;
  cursor: not-allowed;
}
.pagination-lg > li > a,
.pagination-lg > li > span {
  padding: 10px 16px;
  font-size: 17px;
  line-height: 1.3333333;
}
.pagination-lg > li:first-child > a,
.pagination-lg > li:first-child > span {
  border-bottom-left-radius: 3px;
  border-top-left-radius: 3px;
}
.pagination-lg > li:last-child > a,
.pagination-lg > li:last-child > span {
  border-bottom-right-radius: 3px;
  border-top-right-radius: 3px;
}
.pagination-sm > li > a,
.pagination-sm > li > span {
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
}
.pagination-sm > li:first-child > a,
.pagination-sm > li:first-child > span {
  border-bottom-left-radius: 1px;
  border-top-left-radius: 1px;
}
.pagination-sm > li:last-child > a,
.pagination-sm > li:last-child > span {
  border-bottom-right-radius: 1px;
  border-top-right-radius: 1px;
}
.pager {
  padding-left: 0;
  margin: 18px 0;
  list-style: none;
  text-align: center;
}
.pager li {
  display: inline;
}
.pager li > a,
.pager li > span {
  display: inline-block;
  padding: 5px 14px;
  background-color: #fff;
  border: 1px solid #ddd;
  border-radius: 15px;
}
.pager li > a:hover,
.pager li > a:focus {
  text-decoration: none;
  background-color: #eeeeee;
}
.pager .next > a,
.pager .next > span {
  float: right;
}
.pager .previous > a,
.pager .previous > span {
  float: left;
}
.pager .disabled > a,
.pager .disabled > a:hover,
.pager .disabled > a:focus,
.pager .disabled > span {
  color: #777777;
  background-color: #fff;
  cursor: not-allowed;
}
.label {
  display: inline;
  padding: .2em .6em .3em;
  font-size: 75%;
  font-weight: bold;
  line-height: 1;
  color: #fff;
  text-align: center;
  white-space: nowrap;
  vertical-align: baseline;
  border-radius: .25em;
}
a.label:hover,
a.label:focus {
  color: #fff;
  text-decoration: none;
  cursor: pointer;
}
.label:empty {
  display: none;
}
.btn .label {
  position: relative;
  top: -1px;
}
.label-default {
  background-color: #777777;
}
.label-default[href]:hover,
.label-default[href]:focus {
  background-color: #5e5e5e;
}
.label-primary {
  background-color: #337ab7;
}
.label-primary[href]:hover,
.label-primary[href]:focus {
  background-color: #286090;
}
.label-success {
  background-color: #5cb85c;
}
.label-success[href]:hover,
.label-success[href]:focus {
  background-color: #449d44;
}
.label-info {
  background-color: #5bc0de;
}
.label-info[href]:hover,
.label-info[href]:focus {
  background-color: #31b0d5;
}
.label-warning {
  background-color: #f0ad4e;
}
.label-warning[href]:hover,
.label-warning[href]:focus {
  background-color: #ec971f;
}
.label-danger {
  background-color: #d9534f;
}
.label-danger[href]:hover,
.label-danger[href]:focus {
  background-color: #c9302c;
}
.badge {
  display: inline-block;
  min-width: 10px;
  padding: 3px 7px;
  font-size: 12px;
  font-weight: bold;
  color: #fff;
  line-height: 1;
  vertical-align: middle;
  white-space: nowrap;
  text-align: center;
  background-color: #777777;
  border-radius: 10px;
}
.badge:empty {
  display: none;
}
.btn .badge {
  position: relative;
  top: -1px;
}
.btn-xs .badge,
.btn-group-xs > .btn .badge {
  top: 0;
  padding: 1px 5px;
}
a.badge:hover,
a.badge:focus {
  color: #fff;
  text-decoration: none;
  cursor: pointer;
}
.list-group-item.active > .badge,
.nav-pills > .active > a > .badge {
  color: #337ab7;
  background-color: #fff;
}
.list-group-item > .badge {
  float: right;
}
.list-group-item > .badge + .badge {
  margin-right: 5px;
}
.nav-pills > li > a > .badge {
  margin-left: 3px;
}
.jumbotron {
  padding-top: 30px;
  padding-bottom: 30px;
  margin-bottom: 30px;
  color: inherit;
  background-color: #eeeeee;
}
.jumbotron h1,
.jumbotron .h1 {
  color: inherit;
}
.jumbotron p {
  margin-bottom: 15px;
  font-size: 20px;
  font-weight: 200;
}
.jumbotron > hr {
  border-top-color: #d5d5d5;
}
.container .jumbotron,
.container-fluid .jumbotron {
  border-radius: 3px;
  padding-left: 0px;
  padding-right: 0px;
}
.jumbotron .container {
  max-width: 100%;
}
@media screen and (min-width: 768px) {
  .jumbotron {
    padding-top: 48px;
    padding-bottom: 48px;
  }
  .container .jumbotron,
  .container-fluid .jumbotron {
    padding-left: 60px;
    padding-right: 60px;
  }
  .jumbotron h1,
  .jumbotron .h1 {
    font-size: 59px;
  }
}
.thumbnail {
  display: block;
  padding: 4px;
  margin-bottom: 18px;
  line-height: 1.42857143;
  background-color: #fff;
  border: 1px solid #ddd;
  border-radius: 2px;
  -webkit-transition: border 0.2s ease-in-out;
  -o-transition: border 0.2s ease-in-out;
  transition: border 0.2s ease-in-out;
}
.thumbnail > img,
.thumbnail a > img {
  margin-left: auto;
  margin-right: auto;
}
a.thumbnail:hover,
a.thumbnail:focus,
a.thumbnail.active {
  border-color: #337ab7;
}
.thumbnail .caption {
  padding: 9px;
  color: #000;
}
.alert {
  padding: 15px;
  margin-bottom: 18px;
  border: 1px solid transparent;
  border-radius: 2px;
}
.alert h4 {
  margin-top: 0;
  color: inherit;
}
.alert .alert-link {
  font-weight: bold;
}
.alert > p,
.alert > ul {
  margin-bottom: 0;
}
.alert > p + p {
  margin-top: 5px;
}
.alert-dismissable,
.alert-dismissible {
  padding-right: 35px;
}
.alert-dismissable .close,
.alert-dismissible .close {
  position: relative;
  top: -2px;
  right: -21px;
  color: inherit;
}
.alert-success {
  background-color: #dff0d8;
  border-color: #d6e9c6;
  color: #3c763d;
}
.alert-success hr {
  border-top-color: #c9e2b3;
}
.alert-success .alert-link {
  color: #2b542c;
}
.alert-info {
  background-color: #d9edf7;
  border-color: #bce8f1;
  color: #31708f;
}
.alert-info hr {
  border-top-color: #a6e1ec;
}
.alert-info .alert-link {
  color: #245269;
}
.alert-warning {
  background-color: #fcf8e3;
  border-color: #faebcc;
  color: #8a6d3b;
}
.alert-warning hr {
  border-top-color: #f7e1b5;
}
.alert-warning .alert-link {
  color: #66512c;
}
.alert-danger {
  background-color: #f2dede;
  border-color: #ebccd1;
  color: #a94442;
}
.alert-danger hr {
  border-top-color: #e4b9c0;
}
.alert-danger .alert-link {
  color: #843534;
}
@-webkit-keyframes progress-bar-stripes {
  from {
    background-position: 40px 0;
  }
  to {
    background-position: 0 0;
  }
}
@keyframes progress-bar-stripes {
  from {
    background-position: 40px 0;
  }
  to {
    background-position: 0 0;
  }
}
.progress {
  overflow: hidden;
  height: 18px;
  margin-bottom: 18px;
  background-color: #f5f5f5;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 1px 2px rgba(0, 0, 0, 0.1);
  box-shadow: inset 0 1px 2px rgba(0, 0, 0, 0.1);
}
.progress-bar {
  float: left;
  width: 0%;
  height: 100%;
  font-size: 12px;
  line-height: 18px;
  color: #fff;
  text-align: center;
  background-color: #337ab7;
  -webkit-box-shadow: inset 0 -1px 0 rgba(0, 0, 0, 0.15);
  box-shadow: inset 0 -1px 0 rgba(0, 0, 0, 0.15);
  -webkit-transition: width 0.6s ease;
  -o-transition: width 0.6s ease;
  transition: width 0.6s ease;
}
.progress-striped .progress-bar,
.progress-bar-striped {
  background-image: -webkit-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: -o-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-size: 40px 40px;
}
.progress.active .progress-bar,
.progress-bar.active {
  -webkit-animation: progress-bar-stripes 2s linear infinite;
  -o-animation: progress-bar-stripes 2s linear infinite;
  animation: progress-bar-stripes 2s linear infinite;
}
.progress-bar-success {
  background-color: #5cb85c;
}
.progress-striped .progress-bar-success {
  background-image: -webkit-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: -o-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
}
.progress-bar-info {
  background-color: #5bc0de;
}
.progress-striped .progress-bar-info {
  background-image: -webkit-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: -o-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
}
.progress-bar-warning {
  background-color: #f0ad4e;
}
.progress-striped .progress-bar-warning {
  background-image: -webkit-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: -o-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
}
.progress-bar-danger {
  background-color: #d9534f;
}
.progress-striped .progress-bar-danger {
  background-image: -webkit-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: -o-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
}
.media {
  margin-top: 15px;
}
.media:first-child {
  margin-top: 0;
}
.media,
.media-body {
  zoom: 1;
  overflow: hidden;
}
.media-body {
  width: 10000px;
}
.media-object {
  display: block;
}
.media-object.img-thumbnail {
  max-width: none;
}
.media-right,
.media > .pull-right {
  padding-left: 10px;
}
.media-left,
.media > .pull-left {
  padding-right: 10px;
}
.media-left,
.media-right,
.media-body {
  display: table-cell;
  vertical-align: top;
}
.media-middle {
  vertical-align: middle;
}
.media-bottom {
  vertical-align: bottom;
}
.media-heading {
  margin-top: 0;
  margin-bottom: 5px;
}
.media-list {
  padding-left: 0;
  list-style: none;
}
.list-group {
  margin-bottom: 20px;
  padding-left: 0;
}
.list-group-item {
  position: relative;
  display: block;
  padding: 10px 15px;
  margin-bottom: -1px;
  background-color: #fff;
  border: 1px solid #ddd;
}
.list-group-item:first-child {
  border-top-right-radius: 2px;
  border-top-left-radius: 2px;
}
.list-group-item:last-child {
  margin-bottom: 0;
  border-bottom-right-radius: 2px;
  border-bottom-left-radius: 2px;
}
a.list-group-item,
button.list-group-item {
  color: #555;
}
a.list-group-item .list-group-item-heading,
button.list-group-item .list-group-item-heading {
  color: #333;
}
a.list-group-item:hover,
button.list-group-item:hover,
a.list-group-item:focus,
button.list-group-item:focus {
  text-decoration: none;
  color: #555;
  background-color: #f5f5f5;
}
button.list-group-item {
  width: 100%;
  text-align: left;
}
.list-group-item.disabled,
.list-group-item.disabled:hover,
.list-group-item.disabled:focus {
  background-color: #eeeeee;
  color: #777777;
  cursor: not-allowed;
}
.list-group-item.disabled .list-group-item-heading,
.list-group-item.disabled:hover .list-group-item-heading,
.list-group-item.disabled:focus .list-group-item-heading {
  color: inherit;
}
.list-group-item.disabled .list-group-item-text,
.list-group-item.disabled:hover .list-group-item-text,
.list-group-item.disabled:focus .list-group-item-text {
  color: #777777;
}
.list-group-item.active,
.list-group-item.active:hover,
.list-group-item.active:focus {
  z-index: 2;
  color: #fff;
  background-color: #337ab7;
  border-color: #337ab7;
}
.list-group-item.active .list-group-item-heading,
.list-group-item.active:hover .list-group-item-heading,
.list-group-item.active:focus .list-group-item-heading,
.list-group-item.active .list-group-item-heading > small,
.list-group-item.active:hover .list-group-item-heading > small,
.list-group-item.active:focus .list-group-item-heading > small,
.list-group-item.active .list-group-item-heading > .small,
.list-group-item.active:hover .list-group-item-heading > .small,
.list-group-item.active:focus .list-group-item-heading > .small {
  color: inherit;
}
.list-group-item.active .list-group-item-text,
.list-group-item.active:hover .list-group-item-text,
.list-group-item.active:focus .list-group-item-text {
  color: #c7ddef;
}
.list-group-item-success {
  color: #3c763d;
  background-color: #dff0d8;
}
a.list-group-item-success,
button.list-group-item-success {
  color: #3c763d;
}
a.list-group-item-success .list-group-item-heading,
button.list-group-item-success .list-group-item-heading {
  color: inherit;
}
a.list-group-item-success:hover,
button.list-group-item-success:hover,
a.list-group-item-success:focus,
button.list-group-item-success:focus {
  color: #3c763d;
  background-color: #d0e9c6;
}
a.list-group-item-success.active,
button.list-group-item-success.active,
a.list-group-item-success.active:hover,
button.list-group-item-success.active:hover,
a.list-group-item-success.active:focus,
button.list-group-item-success.active:focus {
  color: #fff;
  background-color: #3c763d;
  border-color: #3c763d;
}
.list-group-item-info {
  color: #31708f;
  background-color: #d9edf7;
}
a.list-group-item-info,
button.list-group-item-info {
  color: #31708f;
}
a.list-group-item-info .list-group-item-heading,
button.list-group-item-info .list-group-item-heading {
  color: inherit;
}
a.list-group-item-info:hover,
button.list-group-item-info:hover,
a.list-group-item-info:focus,
button.list-group-item-info:focus {
  color: #31708f;
  background-color: #c4e3f3;
}
a.list-group-item-info.active,
button.list-group-item-info.active,
a.list-group-item-info.active:hover,
button.list-group-item-info.active:hover,
a.list-group-item-info.active:focus,
button.list-group-item-info.active:focus {
  color: #fff;
  background-color: #31708f;
  border-color: #31708f;
}
.list-group-item-warning {
  color: #8a6d3b;
  background-color: #fcf8e3;
}
a.list-group-item-warning,
button.list-group-item-warning {
  color: #8a6d3b;
}
a.list-group-item-warning .list-group-item-heading,
button.list-group-item-warning .list-group-item-heading {
  color: inherit;
}
a.list-group-item-warning:hover,
button.list-group-item-warning:hover,
a.list-group-item-warning:focus,
button.list-group-item-warning:focus {
  color: #8a6d3b;
  background-color: #faf2cc;
}
a.list-group-item-warning.active,
button.list-group-item-warning.active,
a.list-group-item-warning.active:hover,
button.list-group-item-warning.active:hover,
a.list-group-item-warning.active:focus,
button.list-group-item-warning.active:focus {
  color: #fff;
  background-color: #8a6d3b;
  border-color: #8a6d3b;
}
.list-group-item-danger {
  color: #a94442;
  background-color: #f2dede;
}
a.list-group-item-danger,
button.list-group-item-danger {
  color: #a94442;
}
a.list-group-item-danger .list-group-item-heading,
button.list-group-item-danger .list-group-item-heading {
  color: inherit;
}
a.list-group-item-danger:hover,
button.list-group-item-danger:hover,
a.list-group-item-danger:focus,
button.list-group-item-danger:focus {
  color: #a94442;
  background-color: #ebcccc;
}
a.list-group-item-danger.active,
button.list-group-item-danger.active,
a.list-group-item-danger.active:hover,
button.list-group-item-danger.active:hover,
a.list-group-item-danger.active:focus,
button.list-group-item-danger.active:focus {
  color: #fff;
  background-color: #a94442;
  border-color: #a94442;
}
.list-group-item-heading {
  margin-top: 0;
  margin-bottom: 5px;
}
.list-group-item-text {
  margin-bottom: 0;
  line-height: 1.3;
}
.panel {
  margin-bottom: 18px;
  background-color: #fff;
  border: 1px solid transparent;
  border-radius: 2px;
  -webkit-box-shadow: 0 1px 1px rgba(0, 0, 0, 0.05);
  box-shadow: 0 1px 1px rgba(0, 0, 0, 0.05);
}
.panel-body {
  padding: 15px;
}
.panel-heading {
  padding: 10px 15px;
  border-bottom: 1px solid transparent;
  border-top-right-radius: 1px;
  border-top-left-radius: 1px;
}
.panel-heading > .dropdown .dropdown-toggle {
  color: inherit;
}
.panel-title {
  margin-top: 0;
  margin-bottom: 0;
  font-size: 15px;
  color: inherit;
}
.panel-title > a,
.panel-title > small,
.panel-title > .small,
.panel-title > small > a,
.panel-title > .small > a {
  color: inherit;
}
.panel-footer {
  padding: 10px 15px;
  background-color: #f5f5f5;
  border-top: 1px solid #ddd;
  border-bottom-right-radius: 1px;
  border-bottom-left-radius: 1px;
}
.panel > .list-group,
.panel > .panel-collapse > .list-group {
  margin-bottom: 0;
}
.panel > .list-group .list-group-item,
.panel > .panel-collapse > .list-group .list-group-item {
  border-width: 1px 0;
  border-radius: 0;
}
.panel > .list-group:first-child .list-group-item:first-child,
.panel > .panel-collapse > .list-group:first-child .list-group-item:first-child {
  border-top: 0;
  border-top-right-radius: 1px;
  border-top-left-radius: 1px;
}
.panel > .list-group:last-child .list-group-item:last-child,
.panel > .panel-collapse > .list-group:last-child .list-group-item:last-child {
  border-bottom: 0;
  border-bottom-right-radius: 1px;
  border-bottom-left-radius: 1px;
}
.panel > .panel-heading + .panel-collapse > .list-group .list-group-item:first-child {
  border-top-right-radius: 0;
  border-top-left-radius: 0;
}
.panel-heading + .list-group .list-group-item:first-child {
  border-top-width: 0;
}
.list-group + .panel-footer {
  border-top-width: 0;
}
.panel > .table,
.panel > .table-responsive > .table,
.panel > .panel-collapse > .table {
  margin-bottom: 0;
}
.panel > .table caption,
.panel > .table-responsive > .table caption,
.panel > .panel-collapse > .table caption {
  padding-left: 15px;
  padding-right: 15px;
}
.panel > .table:first-child,
.panel > .table-responsive:first-child > .table:first-child {
  border-top-right-radius: 1px;
  border-top-left-radius: 1px;
}
.panel > .table:first-child > thead:first-child > tr:first-child,
.panel > .table-responsive:first-child > .table:first-child > thead:first-child > tr:first-child,
.panel > .table:first-child > tbody:first-child > tr:first-child,
.panel > .table-responsive:first-child > .table:first-child > tbody:first-child > tr:first-child {
  border-top-left-radius: 1px;
  border-top-right-radius: 1px;
}
.panel > .table:first-child > thead:first-child > tr:first-child td:first-child,
.panel > .table-responsive:first-child > .table:first-child > thead:first-child > tr:first-child td:first-child,
.panel > .table:first-child > tbody:first-child > tr:first-child td:first-child,
.panel > .table-responsive:first-child > .table:first-child > tbody:first-child > tr:first-child td:first-child,
.panel > .table:first-child > thead:first-child > tr:first-child th:first-child,
.panel > .table-responsive:first-child > .table:first-child > thead:first-child > tr:first-child th:first-child,
.panel > .table:first-child > tbody:first-child > tr:first-child th:first-child,
.panel > .table-responsive:first-child > .table:first-child > tbody:first-child > tr:first-child th:first-child {
  border-top-left-radius: 1px;
}
.panel > .table:first-child > thead:first-child > tr:first-child td:last-child,
.panel > .table-responsive:first-child > .table:first-child > thead:first-child > tr:first-child td:last-child,
.panel > .table:first-child > tbody:first-child > tr:first-child td:last-child,
.panel > .table-responsive:first-child > .table:first-child > tbody:first-child > tr:first-child td:last-child,
.panel > .table:first-child > thead:first-child > tr:first-child th:last-child,
.panel > .table-responsive:first-child > .table:first-child > thead:first-child > tr:first-child th:last-child,
.panel > .table:first-child > tbody:first-child > tr:first-child th:last-child,
.panel > .table-responsive:first-child > .table:first-child > tbody:first-child > tr:first-child th:last-child {
  border-top-right-radius: 1px;
}
.panel > .table:last-child,
.panel > .table-responsive:last-child > .table:last-child {
  border-bottom-right-radius: 1px;
  border-bottom-left-radius: 1px;
}
.panel > .table:last-child > tbody:last-child > tr:last-child,
.panel > .table-responsive:last-child > .table:last-child > tbody:last-child > tr:last-child,
.panel > .table:last-child > tfoot:last-child > tr:last-child,
.panel > .table-responsive:last-child > .table:last-child > tfoot:last-child > tr:last-child {
  border-bottom-left-radius: 1px;
  border-bottom-right-radius: 1px;
}
.panel > .table:last-child > tbody:last-child > tr:last-child td:first-child,
.panel > .table-responsive:last-child > .table:last-child > tbody:last-child > tr:last-child td:first-child,
.panel > .table:last-child > tfoot:last-child > tr:last-child td:first-child,
.panel > .table-responsive:last-child > .table:last-child > tfoot:last-child > tr:last-child td:first-child,
.panel > .table:last-child > tbody:last-child > tr:last-child th:first-child,
.panel > .table-responsive:last-child > .table:last-child > tbody:last-child > tr:last-child th:first-child,
.panel > .table:last-child > tfoot:last-child > tr:last-child th:first-child,
.panel > .table-responsive:last-child > .table:last-child > tfoot:last-child > tr:last-child th:first-child {
  border-bottom-left-radius: 1px;
}
.panel > .table:last-child > tbody:last-child > tr:last-child td:last-child,
.panel > .table-responsive:last-child > .table:last-child > tbody:last-child > tr:last-child td:last-child,
.panel > .table:last-child > tfoot:last-child > tr:last-child td:last-child,
.panel > .table-responsive:last-child > .table:last-child > tfoot:last-child > tr:last-child td:last-child,
.panel > .table:last-child > tbody:last-child > tr:last-child th:last-child,
.panel > .table-responsive:last-child > .table:last-child > tbody:last-child > tr:last-child th:last-child,
.panel > .table:last-child > tfoot:last-child > tr:last-child th:last-child,
.panel > .table-responsive:last-child > .table:last-child > tfoot:last-child > tr:last-child th:last-child {
  border-bottom-right-radius: 1px;
}
.panel > .panel-body + .table,
.panel > .panel-body + .table-responsive,
.panel > .table + .panel-body,
.panel > .table-responsive + .panel-body {
  border-top: 1px solid #ddd;
}
.panel > .table > tbody:first-child > tr:first-child th,
.panel > .table > tbody:first-child > tr:first-child td {
  border-top: 0;
}
.panel > .table-bordered,
.panel > .table-responsive > .table-bordered {
  border: 0;
}
.panel > .table-bordered > thead > tr > th:first-child,
.panel > .table-responsive > .table-bordered > thead > tr > th:first-child,
.panel > .table-bordered > tbody > tr > th:first-child,
.panel > .table-responsive > .table-bordered > tbody > tr > th:first-child,
.panel > .table-bordered > tfoot > tr > th:first-child,
.panel > .table-responsive > .table-bordered > tfoot > tr > th:first-child,
.panel > .table-bordered > thead > tr > td:first-child,
.panel > .table-responsive > .table-bordered > thead > tr > td:first-child,
.panel > .table-bordered > tbody > tr > td:first-child,
.panel > .table-responsive > .table-bordered > tbody > tr > td:first-child,
.panel > .table-bordered > tfoot > tr > td:first-child,
.panel > .table-responsive > .table-bordered > tfoot > tr > td:first-child {
  border-left: 0;
}
.panel > .table-bordered > thead > tr > th:last-child,
.panel > .table-responsive > .table-bordered > thead > tr > th:last-child,
.panel > .table-bordered > tbody > tr > th:last-child,
.panel > .table-responsive > .table-bordered > tbody > tr > th:last-child,
.panel > .table-bordered > tfoot > tr > th:last-child,
.panel > .table-responsive > .table-bordered > tfoot > tr > th:last-child,
.panel > .table-bordered > thead > tr > td:last-child,
.panel > .table-responsive > .table-bordered > thead > tr > td:last-child,
.panel > .table-bordered > tbody > tr > td:last-child,
.panel > .table-responsive > .table-bordered > tbody > tr > td:last-child,
.panel > .table-bordered > tfoot > tr > td:last-child,
.panel > .table-responsive > .table-bordered > tfoot > tr > td:last-child {
  border-right: 0;
}
.panel > .table-bordered > thead > tr:first-child > td,
.panel > .table-responsive > .table-bordered > thead > tr:first-child > td,
.panel > .table-bordered > tbody > tr:first-child > td,
.panel > .table-responsive > .table-bordered > tbody > tr:first-child > td,
.panel > .table-bordered > thead > tr:first-child > th,
.panel > .table-responsive > .table-bordered > thead > tr:first-child > th,
.panel > .table-bordered > tbody > tr:first-child > th,
.panel > .table-responsive > .table-bordered > tbody > tr:first-child > th {
  border-bottom: 0;
}
.panel > .table-bordered > tbody > tr:last-child > td,
.panel > .table-responsive > .table-bordered > tbody > tr:last-child > td,
.panel > .table-bordered > tfoot > tr:last-child > td,
.panel > .table-responsive > .table-bordered > tfoot > tr:last-child > td,
.panel > .table-bordered > tbody > tr:last-child > th,
.panel > .table-responsive > .table-bordered > tbody > tr:last-child > th,
.panel > .table-bordered > tfoot > tr:last-child > th,
.panel > .table-responsive > .table-bordered > tfoot > tr:last-child > th {
  border-bottom: 0;
}
.panel > .table-responsive {
  border: 0;
  margin-bottom: 0;
}
.panel-group {
  margin-bottom: 18px;
}
.panel-group .panel {
  margin-bottom: 0;
  border-radius: 2px;
}
.panel-group .panel + .panel {
  margin-top: 5px;
}
.panel-group .panel-heading {
  border-bottom: 0;
}
.panel-group .panel-heading + .panel-collapse > .panel-body,
.panel-group .panel-heading + .panel-collapse > .list-group {
  border-top: 1px solid #ddd;
}
.panel-group .panel-footer {
  border-top: 0;
}
.panel-group .panel-footer + .panel-collapse .panel-body {
  border-bottom: 1px solid #ddd;
}
.panel-default {
  border-color: #ddd;
}
.panel-default > .panel-heading {
  color: #333333;
  background-color: #f5f5f5;
  border-color: #ddd;
}
.panel-default > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #ddd;
}
.panel-default > .panel-heading .badge {
  color: #f5f5f5;
  background-color: #333333;
}
.panel-default > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #ddd;
}
.panel-primary {
  border-color: #337ab7;
}
.panel-primary > .panel-heading {
  color: #fff;
  background-color: #337ab7;
  border-color: #337ab7;
}
.panel-primary > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #337ab7;
}
.panel-primary > .panel-heading .badge {
  color: #337ab7;
  background-color: #fff;
}
.panel-primary > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #337ab7;
}
.panel-success {
  border-color: #d6e9c6;
}
.panel-success > .panel-heading {
  color: #3c763d;
  background-color: #dff0d8;
  border-color: #d6e9c6;
}
.panel-success > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #d6e9c6;
}
.panel-success > .panel-heading .badge {
  color: #dff0d8;
  background-color: #3c763d;
}
.panel-success > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #d6e9c6;
}
.panel-info {
  border-color: #bce8f1;
}
.panel-info > .panel-heading {
  color: #31708f;
  background-color: #d9edf7;
  border-color: #bce8f1;
}
.panel-info > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #bce8f1;
}
.panel-info > .panel-heading .badge {
  color: #d9edf7;
  background-color: #31708f;
}
.panel-info > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #bce8f1;
}
.panel-warning {
  border-color: #faebcc;
}
.panel-warning > .panel-heading {
  color: #8a6d3b;
  background-color: #fcf8e3;
  border-color: #faebcc;
}
.panel-warning > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #faebcc;
}
.panel-warning > .panel-heading .badge {
  color: #fcf8e3;
  background-color: #8a6d3b;
}
.panel-warning > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #faebcc;
}
.panel-danger {
  border-color: #ebccd1;
}
.panel-danger > .panel-heading {
  color: #a94442;
  background-color: #f2dede;
  border-color: #ebccd1;
}
.panel-danger > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #ebccd1;
}
.panel-danger > .panel-heading .badge {
  color: #f2dede;
  background-color: #a94442;
}
.panel-danger > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #ebccd1;
}
.embed-responsive {
  position: relative;
  display: block;
  height: 0;
  padding: 0;
  overflow: hidden;
}
.embed-responsive .embed-responsive-item,
.embed-responsive iframe,
.embed-responsive embed,
.embed-responsive object,
.embed-responsive video {
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  height: 100%;
  width: 100%;
  border: 0;
}
.embed-responsive-16by9 {
  padding-bottom: 56.25%;
}
.embed-responsive-4by3 {
  padding-bottom: 75%;
}
.well {
  min-height: 20px;
  padding: 19px;
  margin-bottom: 20px;
  background-color: #f5f5f5;
  border: 1px solid #e3e3e3;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.05);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.05);
}
.well blockquote {
  border-color: #ddd;
  border-color: rgba(0, 0, 0, 0.15);
}
.well-lg {
  padding: 24px;
  border-radius: 3px;
}
.well-sm {
  padding: 9px;
  border-radius: 1px;
}
.close {
  float: right;
  font-size: 19.5px;
  font-weight: bold;
  line-height: 1;
  color: #000;
  text-shadow: 0 1px 0 #fff;
  opacity: 0.2;
  filter: alpha(opacity=20);
}
.close:hover,
.close:focus {
  color: #000;
  text-decoration: none;
  cursor: pointer;
  opacity: 0.5;
  filter: alpha(opacity=50);
}
button.close {
  padding: 0;
  cursor: pointer;
  background: transparent;
  border: 0;
  -webkit-appearance: none;
}
.modal-open {
  overflow: hidden;
}
.modal {
  display: none;
  overflow: hidden;
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 1050;
  -webkit-overflow-scrolling: touch;
  outline: 0;
}
.modal.fade .modal-dialog {
  -webkit-transform: translate(0, -25%);
  -ms-transform: translate(0, -25%);
  -o-transform: translate(0, -25%);
  transform: translate(0, -25%);
  -webkit-transition: -webkit-transform 0.3s ease-out;
  -moz-transition: -moz-transform 0.3s ease-out;
  -o-transition: -o-transform 0.3s ease-out;
  transition: transform 0.3s ease-out;
}
.modal.in .modal-dialog {
  -webkit-transform: translate(0, 0);
  -ms-transform: translate(0, 0);
  -o-transform: translate(0, 0);
  transform: translate(0, 0);
}
.modal-open .modal {
  overflow-x: hidden;
  overflow-y: auto;
}
.modal-dialog {
  position: relative;
  width: auto;
  margin: 10px;
}
.modal-content {
  position: relative;
  background-color: #fff;
  border: 1px solid #999;
  border: 1px solid rgba(0, 0, 0, 0.2);
  border-radius: 3px;
  -webkit-box-shadow: 0 3px 9px rgba(0, 0, 0, 0.5);
  box-shadow: 0 3px 9px rgba(0, 0, 0, 0.5);
  background-clip: padding-box;
  outline: 0;
}
.modal-backdrop {
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 1040;
  background-color: #000;
}
.modal-backdrop.fade {
  opacity: 0;
  filter: alpha(opacity=0);
}
.modal-backdrop.in {
  opacity: 0.5;
  filter: alpha(opacity=50);
}
.modal-header {
  padding: 15px;
  border-bottom: 1px solid #e5e5e5;
}
.modal-header .close {
  margin-top: -2px;
}
.modal-title {
  margin: 0;
  line-height: 1.42857143;
}
.modal-body {
  position: relative;
  padding: 15px;
}
.modal-footer {
  padding: 15px;
  text-align: right;
  border-top: 1px solid #e5e5e5;
}
.modal-footer .btn + .btn {
  margin-left: 5px;
  margin-bottom: 0;
}
.modal-footer .btn-group .btn + .btn {
  margin-left: -1px;
}
.modal-footer .btn-block + .btn-block {
  margin-left: 0;
}
.modal-scrollbar-measure {
  position: absolute;
  top: -9999px;
  width: 50px;
  height: 50px;
  overflow: scroll;
}
@media (min-width: 768px) {
  .modal-dialog {
    width: 600px;
    margin: 30px auto;
  }
  .modal-content {
    -webkit-box-shadow: 0 5px 15px rgba(0, 0, 0, 0.5);
    box-shadow: 0 5px 15px rgba(0, 0, 0, 0.5);
  }
  .modal-sm {
    width: 300px;
  }
}
@media (min-width: 992px) {
  .modal-lg {
    width: 900px;
  }
}
.tooltip {
  position: absolute;
  z-index: 1070;
  display: block;
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
  font-style: normal;
  font-weight: normal;
  letter-spacing: normal;
  line-break: auto;
  line-height: 1.42857143;
  text-align: left;
  text-align: start;
  text-decoration: none;
  text-shadow: none;
  text-transform: none;
  white-space: normal;
  word-break: normal;
  word-spacing: normal;
  word-wrap: normal;
  font-size: 12px;
  opacity: 0;
  filter: alpha(opacity=0);
}
.tooltip.in {
  opacity: 0.9;
  filter: alpha(opacity=90);
}
.tooltip.top {
  margin-top: -3px;
  padding: 5px 0;
}
.tooltip.right {
  margin-left: 3px;
  padding: 0 5px;
}
.tooltip.bottom {
  margin-top: 3px;
  padding: 5px 0;
}
.tooltip.left {
  margin-left: -3px;
  padding: 0 5px;
}
.tooltip-inner {
  max-width: 200px;
  padding: 3px 8px;
  color: #fff;
  text-align: center;
  background-color: #000;
  border-radius: 2px;
}
.tooltip-arrow {
  position: absolute;
  width: 0;
  height: 0;
  border-color: transparent;
  border-style: solid;
}
.tooltip.top .tooltip-arrow {
  bottom: 0;
  left: 50%;
  margin-left: -5px;
  border-width: 5px 5px 0;
  border-top-color: #000;
}
.tooltip.top-left .tooltip-arrow {
  bottom: 0;
  right: 5px;
  margin-bottom: -5px;
  border-width: 5px 5px 0;
  border-top-color: #000;
}
.tooltip.top-right .tooltip-arrow {
  bottom: 0;
  left: 5px;
  margin-bottom: -5px;
  border-width: 5px 5px 0;
  border-top-color: #000;
}
.tooltip.right .tooltip-arrow {
  top: 50%;
  left: 0;
  margin-top: -5px;
  border-width: 5px 5px 5px 0;
  border-right-color: #000;
}
.tooltip.left .tooltip-arrow {
  top: 50%;
  right: 0;
  margin-top: -5px;
  border-width: 5px 0 5px 5px;
  border-left-color: #000;
}
.tooltip.bottom .tooltip-arrow {
  top: 0;
  left: 50%;
  margin-left: -5px;
  border-width: 0 5px 5px;
  border-bottom-color: #000;
}
.tooltip.bottom-left .tooltip-arrow {
  top: 0;
  right: 5px;
  margin-top: -5px;
  border-width: 0 5px 5px;
  border-bottom-color: #000;
}
.tooltip.bottom-right .tooltip-arrow {
  top: 0;
  left: 5px;
  margin-top: -5px;
  border-width: 0 5px 5px;
  border-bottom-color: #000;
}
.popover {
  position: absolute;
  top: 0;
  left: 0;
  z-index: 1060;
  display: none;
  max-width: 276px;
  padding: 1px;
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
  font-style: normal;
  font-weight: normal;
  letter-spacing: normal;
  line-break: auto;
  line-height: 1.42857143;
  text-align: left;
  text-align: start;
  text-decoration: none;
  text-shadow: none;
  text-transform: none;
  white-space: normal;
  word-break: normal;
  word-spacing: normal;
  word-wrap: normal;
  font-size: 13px;
  background-color: #fff;
  background-clip: padding-box;
  border: 1px solid #ccc;
  border: 1px solid rgba(0, 0, 0, 0.2);
  border-radius: 3px;
  -webkit-box-shadow: 0 5px 10px rgba(0, 0, 0, 0.2);
  box-shadow: 0 5px 10px rgba(0, 0, 0, 0.2);
}
.popover.top {
  margin-top: -10px;
}
.popover.right {
  margin-left: 10px;
}
.popover.bottom {
  margin-top: 10px;
}
.popover.left {
  margin-left: -10px;
}
.popover-title {
  margin: 0;
  padding: 8px 14px;
  font-size: 13px;
  background-color: #f7f7f7;
  border-bottom: 1px solid #ebebeb;
  border-radius: 2px 2px 0 0;
}
.popover-content {
  padding: 9px 14px;
}
.popover > .arrow,
.popover > .arrow:after {
  position: absolute;
  display: block;
  width: 0;
  height: 0;
  border-color: transparent;
  border-style: solid;
}
.popover > .arrow {
  border-width: 11px;
}
.popover > .arrow:after {
  border-width: 10px;
  content: "";
}
.popover.top > .arrow {
  left: 50%;
  margin-left: -11px;
  border-bottom-width: 0;
  border-top-color: #999999;
  border-top-color: rgba(0, 0, 0, 0.25);
  bottom: -11px;
}
.popover.top > .arrow:after {
  content: " ";
  bottom: 1px;
  margin-left: -10px;
  border-bottom-width: 0;
  border-top-color: #fff;
}
.popover.right > .arrow {
  top: 50%;
  left: -11px;
  margin-top: -11px;
  border-left-width: 0;
  border-right-color: #999999;
  border-right-color: rgba(0, 0, 0, 0.25);
}
.popover.right > .arrow:after {
  content: " ";
  left: 1px;
  bottom: -10px;
  border-left-width: 0;
  border-right-color: #fff;
}
.popover.bottom > .arrow {
  left: 50%;
  margin-left: -11px;
  border-top-width: 0;
  border-bottom-color: #999999;
  border-bottom-color: rgba(0, 0, 0, 0.25);
  top: -11px;
}
.popover.bottom > .arrow:after {
  content: " ";
  top: 1px;
  margin-left: -10px;
  border-top-width: 0;
  border-bottom-color: #fff;
}
.popover.left > .arrow {
  top: 50%;
  right: -11px;
  margin-top: -11px;
  border-right-width: 0;
  border-left-color: #999999;
  border-left-color: rgba(0, 0, 0, 0.25);
}
.popover.left > .arrow:after {
  content: " ";
  right: 1px;
  border-right-width: 0;
  border-left-color: #fff;
  bottom: -10px;
}
.carousel {
  position: relative;
}
.carousel-inner {
  position: relative;
  overflow: hidden;
  width: 100%;
}
.carousel-inner > .item {
  display: none;
  position: relative;
  -webkit-transition: 0.6s ease-in-out left;
  -o-transition: 0.6s ease-in-out left;
  transition: 0.6s ease-in-out left;
}
.carousel-inner > .item > img,
.carousel-inner > .item > a > img {
  line-height: 1;
}
@media all and (transform-3d), (-webkit-transform-3d) {
  .carousel-inner > .item {
    -webkit-transition: -webkit-transform 0.6s ease-in-out;
    -moz-transition: -moz-transform 0.6s ease-in-out;
    -o-transition: -o-transform 0.6s ease-in-out;
    transition: transform 0.6s ease-in-out;
    -webkit-backface-visibility: hidden;
    -moz-backface-visibility: hidden;
    backface-visibility: hidden;
    -webkit-perspective: 1000px;
    -moz-perspective: 1000px;
    perspective: 1000px;
  }
  .carousel-inner > .item.next,
  .carousel-inner > .item.active.right {
    -webkit-transform: translate3d(100%, 0, 0);
    transform: translate3d(100%, 0, 0);
    left: 0;
  }
  .carousel-inner > .item.prev,
  .carousel-inner > .item.active.left {
    -webkit-transform: translate3d(-100%, 0, 0);
    transform: translate3d(-100%, 0, 0);
    left: 0;
  }
  .carousel-inner > .item.next.left,
  .carousel-inner > .item.prev.right,
  .carousel-inner > .item.active {
    -webkit-transform: translate3d(0, 0, 0);
    transform: translate3d(0, 0, 0);
    left: 0;
  }
}
.carousel-inner > .active,
.carousel-inner > .next,
.carousel-inner > .prev {
  display: block;
}
.carousel-inner > .active {
  left: 0;
}
.carousel-inner > .next,
.carousel-inner > .prev {
  position: absolute;
  top: 0;
  width: 100%;
}
.carousel-inner > .next {
  left: 100%;
}
.carousel-inner > .prev {
  left: -100%;
}
.carousel-inner > .next.left,
.carousel-inner > .prev.right {
  left: 0;
}
.carousel-inner > .active.left {
  left: -100%;
}
.carousel-inner > .active.right {
  left: 100%;
}
.carousel-control {
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  width: 15%;
  opacity: 0.5;
  filter: alpha(opacity=50);
  font-size: 20px;
  color: #fff;
  text-align: center;
  text-shadow: 0 1px 2px rgba(0, 0, 0, 0.6);
  background-color: rgba(0, 0, 0, 0);
}
.carousel-control.left {
  background-image: -webkit-linear-gradient(left, rgba(0, 0, 0, 0.5) 0%, rgba(0, 0, 0, 0.0001) 100%);
  background-image: -o-linear-gradient(left, rgba(0, 0, 0, 0.5) 0%, rgba(0, 0, 0, 0.0001) 100%);
  background-image: linear-gradient(to right, rgba(0, 0, 0, 0.5) 0%, rgba(0, 0, 0, 0.0001) 100%);
  background-repeat: repeat-x;
  filter: progid:DXImageTransform.Microsoft.gradient(startColorstr='#80000000', endColorstr='#00000000', GradientType=1);
}
.carousel-control.right {
  left: auto;
  right: 0;
  background-image: -webkit-linear-gradient(left, rgba(0, 0, 0, 0.0001) 0%, rgba(0, 0, 0, 0.5) 100%);
  background-image: -o-linear-gradient(left, rgba(0, 0, 0, 0.0001) 0%, rgba(0, 0, 0, 0.5) 100%);
  background-image: linear-gradient(to right, rgba(0, 0, 0, 0.0001) 0%, rgba(0, 0, 0, 0.5) 100%);
  background-repeat: repeat-x;
  filter: progid:DXImageTransform.Microsoft.gradient(startColorstr='#00000000', endColorstr='#80000000', GradientType=1);
}
.carousel-control:hover,
.carousel-control:focus {
  outline: 0;
  color: #fff;
  text-decoration: none;
  opacity: 0.9;
  filter: alpha(opacity=90);
}
.carousel-control .icon-prev,
.carousel-control .icon-next,
.carousel-control .glyphicon-chevron-left,
.carousel-control .glyphicon-chevron-right {
  position: absolute;
  top: 50%;
  margin-top: -10px;
  z-index: 5;
  display: inline-block;
}
.carousel-control .icon-prev,
.carousel-control .glyphicon-chevron-left {
  left: 50%;
  margin-left: -10px;
}
.carousel-control .icon-next,
.carousel-control .glyphicon-chevron-right {
  right: 50%;
  margin-right: -10px;
}
.carousel-control .icon-prev,
.carousel-control .icon-next {
  width: 20px;
  height: 20px;
  line-height: 1;
  font-family: serif;
}
.carousel-control .icon-prev:before {
  content: '\2039';
}
.carousel-control .icon-next:before {
  content: '\203a';
}
.carousel-indicators {
  position: absolute;
  bottom: 10px;
  left: 50%;
  z-index: 15;
  width: 60%;
  margin-left: -30%;
  padding-left: 0;
  list-style: none;
  text-align: center;
}
.carousel-indicators li {
  display: inline-block;
  width: 10px;
  height: 10px;
  margin: 1px;
  text-indent: -999px;
  border: 1px solid #fff;
  border-radius: 10px;
  cursor: pointer;
  background-color: #000 \9;
  background-color: rgba(0, 0, 0, 0);
}
.carousel-indicators .active {
  margin: 0;
  width: 12px;
  height: 12px;
  background-color: #fff;
}
.carousel-caption {
  position: absolute;
  left: 15%;
  right: 15%;
  bottom: 20px;
  z-index: 10;
  padding-top: 20px;
  padding-bottom: 20px;
  color: #fff;
  text-align: center;
  text-shadow: 0 1px 2px rgba(0, 0, 0, 0.6);
}
.carousel-caption .btn {
  text-shadow: none;
}
@media screen and (min-width: 768px) {
  .carousel-control .glyphicon-chevron-left,
  .carousel-control .glyphicon-chevron-right,
  .carousel-control .icon-prev,
  .carousel-control .icon-next {
    width: 30px;
    height: 30px;
    margin-top: -10px;
    font-size: 30px;
  }
  .carousel-control .glyphicon-chevron-left,
  .carousel-control .icon-prev {
    margin-left: -10px;
  }
  .carousel-control .glyphicon-chevron-right,
  .carousel-control .icon-next {
    margin-right: -10px;
  }
  .carousel-caption {
    left: 20%;
    right: 20%;
    padding-bottom: 30px;
  }
  .carousel-indicators {
    bottom: 20px;
  }
}
.clearfix:before,
.clearfix:after,
.dl-horizontal dd:before,
.dl-horizontal dd:after,
.container:before,
.container:after,
.container-fluid:before,
.container-fluid:after,
.row:before,
.row:after,
.form-horizontal .form-group:before,
.form-horizontal .form-group:after,
.btn-toolbar:before,
.btn-toolbar:after,
.btn-group-vertical > .btn-group:before,
.btn-group-vertical > .btn-group:after,
.nav:before,
.nav:after,
.navbar:before,
.navbar:after,
.navbar-header:before,
.navbar-header:after,
.navbar-collapse:before,
.navbar-collapse:after,
.pager:before,
.pager:after,
.panel-body:before,
.panel-body:after,
.modal-header:before,
.modal-header:after,
.modal-footer:before,
.modal-footer:after,
.item_buttons:before,
.item_buttons:after {
  content: " ";
  display: table;
}
.clearfix:after,
.dl-horizontal dd:after,
.container:after,
.container-fluid:after,
.row:after,
.form-horizontal .form-group:after,
.btn-toolbar:after,
.btn-group-vertical > .btn-group:after,
.nav:after,
.navbar:after,
.navbar-header:after,
.navbar-collapse:after,
.pager:after,
.panel-body:after,
.modal-header:after,
.modal-footer:after,
.item_buttons:after {
  clear: both;
}
.center-block {
  display: block;
  margin-left: auto;
  margin-right: auto;
}
.pull-right {
  float: right !important;
}
.pull-left {
  float: left !important;
}
.hide {
  display: none !important;
}
.show {
  display: block !important;
}
.invisible {
  visibility: hidden;
}
.text-hide {
  font: 0/0 a;
  color: transparent;
  text-shadow: none;
  background-color: transparent;
  border: 0;
}
.hidden {
  display: none !important;
}
.affix {
  position: fixed;
}
@-ms-viewport {
  width: device-width;
}
.visible-xs,
.visible-sm,
.visible-md,
.visible-lg {
  display: none !important;
}
.visible-xs-block,
.visible-xs-inline,
.visible-xs-inline-block,
.visible-sm-block,
.visible-sm-inline,
.visible-sm-inline-block,
.visible-md-block,
.visible-md-inline,
.visible-md-inline-block,
.visible-lg-block,
.visible-lg-inline,
.visible-lg-inline-block {
  display: none !important;
}
@media (max-width: 767px) {
  .visible-xs {
    display: block !important;
  }
  table.visible-xs {
    display: table !important;
  }
  tr.visible-xs {
    display: table-row !important;
  }
  th.visible-xs,
  td.visible-xs {
    display: table-cell !important;
  }
}
@media (max-width: 767px) {
  .visible-xs-block {
    display: block !important;
  }
}
@media (max-width: 767px) {
  .visible-xs-inline {
    display: inline !important;
  }
}
@media (max-width: 767px) {
  .visible-xs-inline-block {
    display: inline-block !important;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  .visible-sm {
    display: block !important;
  }
  table.visible-sm {
    display: table !important;
  }
  tr.visible-sm {
    display: table-row !important;
  }
  th.visible-sm,
  td.visible-sm {
    display: table-cell !important;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  .visible-sm-block {
    display: block !important;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  .visible-sm-inline {
    display: inline !important;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  .visible-sm-inline-block {
    display: inline-block !important;
  }
}
@media (min-width: 992px) and (max-width: 1199px) {
  .visible-md {
    display: block !important;
  }
  table.visible-md {
    display: table !important;
  }
  tr.visible-md {
    display: table-row !important;
  }
  th.visible-md,
  td.visible-md {
    display: table-cell !important;
  }
}
@media (min-width: 992px) and (max-width: 1199px) {
  .visible-md-block {
    display: block !important;
  }
}
@media (min-width: 992px) and (max-width: 1199px) {
  .visible-md-inline {
    display: inline !important;
  }
}
@media (min-width: 992px) and (max-width: 1199px) {
  .visible-md-inline-block {
    display: inline-block !important;
  }
}
@media (min-width: 1200px) {
  .visible-lg {
    display: block !important;
  }
  table.visible-lg {
    display: table !important;
  }
  tr.visible-lg {
    display: table-row !important;
  }
  th.visible-lg,
  td.visible-lg {
    display: table-cell !important;
  }
}
@media (min-width: 1200px) {
  .visible-lg-block {
    display: block !important;
  }
}
@media (min-width: 1200px) {
  .visible-lg-inline {
    display: inline !important;
  }
}
@media (min-width: 1200px) {
  .visible-lg-inline-block {
    display: inline-block !important;
  }
}
@media (max-width: 767px) {
  .hidden-xs {
    display: none !important;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  .hidden-sm {
    display: none !important;
  }
}
@media (min-width: 992px) and (max-width: 1199px) {
  .hidden-md {
    display: none !important;
  }
}
@media (min-width: 1200px) {
  .hidden-lg {
    display: none !important;
  }
}
.visible-print {
  display: none !important;
}
@media print {
  .visible-print {
    display: block !important;
  }
  table.visible-print {
    display: table !important;
  }
  tr.visible-print {
    display: table-row !important;
  }
  th.visible-print,
  td.visible-print {
    display: table-cell !important;
  }
}
.visible-print-block {
  display: none !important;
}
@media print {
  .visible-print-block {
    display: block !important;
  }
}
.visible-print-inline {
  display: none !important;
}
@media print {
  .visible-print-inline {
    display: inline !important;
  }
}
.visible-print-inline-block {
  display: none !important;
}
@media print {
  .visible-print-inline-block {
    display: inline-block !important;
  }
}
@media print {
  .hidden-print {
    display: none !important;
  }
}
/*!
*
* Font Awesome
*
*/
/*!
 *  Font Awesome 4.7.0 by @davegandy - http://fontawesome.io - @fontawesome
 *  License - http://fontawesome.io/license (Font: SIL OFL 1.1, CSS: MIT License)
 */
/* FONT PATH
 * -------------------------- */
@font-face {
  font-family: 'FontAwesome';
  src: url('../components/font-awesome/fonts/fontawesome-webfont.eot?v=4.7.0');
  src: url('../components/font-awesome/fonts/fontawesome-webfont.eot?#iefix&v=4.7.0') format('embedded-opentype'), url('../components/font-awesome/fonts/fontawesome-webfont.woff2?v=4.7.0') format('woff2'), url('../components/font-awesome/fonts/fontawesome-webfont.woff?v=4.7.0') format('woff'), url('../components/font-awesome/fonts/fontawesome-webfont.ttf?v=4.7.0') format('truetype'), url('../components/font-awesome/fonts/fontawesome-webfont.svg?v=4.7.0#fontawesomeregular') format('svg');
  font-weight: normal;
  font-style: normal;
}
.fa {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
/* makes the font 33% larger relative to the icon container */
.fa-lg {
  font-size: 1.33333333em;
  line-height: 0.75em;
  vertical-align: -15%;
}
.fa-2x {
  font-size: 2em;
}
.fa-3x {
  font-size: 3em;
}
.fa-4x {
  font-size: 4em;
}
.fa-5x {
  font-size: 5em;
}
.fa-fw {
  width: 1.28571429em;
  text-align: center;
}
.fa-ul {
  padding-left: 0;
  margin-left: 2.14285714em;
  list-style-type: none;
}
.fa-ul > li {
  position: relative;
}
.fa-li {
  position: absolute;
  left: -2.14285714em;
  width: 2.14285714em;
  top: 0.14285714em;
  text-align: center;
}
.fa-li.fa-lg {
  left: -1.85714286em;
}
.fa-border {
  padding: .2em .25em .15em;
  border: solid 0.08em #eee;
  border-radius: .1em;
}
.fa-pull-left {
  float: left;
}
.fa-pull-right {
  float: right;
}
.fa.fa-pull-left {
  margin-right: .3em;
}
.fa.fa-pull-right {
  margin-left: .3em;
}
/* Deprecated as of 4.4.0 */
.pull-right {
  float: right;
}
.pull-left {
  float: left;
}
.fa.pull-left {
  margin-right: .3em;
}
.fa.pull-right {
  margin-left: .3em;
}
.fa-spin {
  -webkit-animation: fa-spin 2s infinite linear;
  animation: fa-spin 2s infinite linear;
}
.fa-pulse {
  -webkit-animation: fa-spin 1s infinite steps(8);
  animation: fa-spin 1s infinite steps(8);
}
@-webkit-keyframes fa-spin {
  0% {
    -webkit-transform: rotate(0deg);
    transform: rotate(0deg);
  }
  100% {
    -webkit-transform: rotate(359deg);
    transform: rotate(359deg);
  }
}
@keyframes fa-spin {
  0% {
    -webkit-transform: rotate(0deg);
    transform: rotate(0deg);
  }
  100% {
    -webkit-transform: rotate(359deg);
    transform: rotate(359deg);
  }
}
.fa-rotate-90 {
  -ms-filter: "progid:DXImageTransform.Microsoft.BasicImage(rotation=1)";
  -webkit-transform: rotate(90deg);
  -ms-transform: rotate(90deg);
  transform: rotate(90deg);
}
.fa-rotate-180 {
  -ms-filter: "progid:DXImageTransform.Microsoft.BasicImage(rotation=2)";
  -webkit-transform: rotate(180deg);
  -ms-transform: rotate(180deg);
  transform: rotate(180deg);
}
.fa-rotate-270 {
  -ms-filter: "progid:DXImageTransform.Microsoft.BasicImage(rotation=3)";
  -webkit-transform: rotate(270deg);
  -ms-transform: rotate(270deg);
  transform: rotate(270deg);
}
.fa-flip-horizontal {
  -ms-filter: "progid:DXImageTransform.Microsoft.BasicImage(rotation=0, mirror=1)";
  -webkit-transform: scale(-1, 1);
  -ms-transform: scale(-1, 1);
  transform: scale(-1, 1);
}
.fa-flip-vertical {
  -ms-filter: "progid:DXImageTransform.Microsoft.BasicImage(rotation=2, mirror=1)";
  -webkit-transform: scale(1, -1);
  -ms-transform: scale(1, -1);
  transform: scale(1, -1);
}
:root .fa-rotate-90,
:root .fa-rotate-180,
:root .fa-rotate-270,
:root .fa-flip-horizontal,
:root .fa-flip-vertical {
  filter: none;
}
.fa-stack {
  position: relative;
  display: inline-block;
  width: 2em;
  height: 2em;
  line-height: 2em;
  vertical-align: middle;
}
.fa-stack-1x,
.fa-stack-2x {
  position: absolute;
  left: 0;
  width: 100%;
  text-align: center;
}
.fa-stack-1x {
  line-height: inherit;
}
.fa-stack-2x {
  font-size: 2em;
}
.fa-inverse {
  color: #fff;
}
/* Font Awesome uses the Unicode Private Use Area (PUA) to ensure screen
   readers do not read off random characters that represent icons */
.fa-glass:before {
  content: "\f000";
}
.fa-music:before {
  content: "\f001";
}
.fa-search:before {
  content: "\f002";
}
.fa-envelope-o:before {
  content: "\f003";
}
.fa-heart:before {
  content: "\f004";
}
.fa-star:before {
  content: "\f005";
}
.fa-star-o:before {
  content: "\f006";
}
.fa-user:before {
  content: "\f007";
}
.fa-film:before {
  content: "\f008";
}
.fa-th-large:before {
  content: "\f009";
}
.fa-th:before {
  content: "\f00a";
}
.fa-th-list:before {
  content: "\f00b";
}
.fa-check:before {
  content: "\f00c";
}
.fa-remove:before,
.fa-close:before,
.fa-times:before {
  content: "\f00d";
}
.fa-search-plus:before {
  content: "\f00e";
}
.fa-search-minus:before {
  content: "\f010";
}
.fa-power-off:before {
  content: "\f011";
}
.fa-signal:before {
  content: "\f012";
}
.fa-gear:before,
.fa-cog:before {
  content: "\f013";
}
.fa-trash-o:before {
  content: "\f014";
}
.fa-home:before {
  content: "\f015";
}
.fa-file-o:before {
  content: "\f016";
}
.fa-clock-o:before {
  content: "\f017";
}
.fa-road:before {
  content: "\f018";
}
.fa-download:before {
  content: "\f019";
}
.fa-arrow-circle-o-down:before {
  content: "\f01a";
}
.fa-arrow-circle-o-up:before {
  content: "\f01b";
}
.fa-inbox:before {
  content: "\f01c";
}
.fa-play-circle-o:before {
  content: "\f01d";
}
.fa-rotate-right:before,
.fa-repeat:before {
  content: "\f01e";
}
.fa-refresh:before {
  content: "\f021";
}
.fa-list-alt:before {
  content: "\f022";
}
.fa-lock:before {
  content: "\f023";
}
.fa-flag:before {
  content: "\f024";
}
.fa-headphones:before {
  content: "\f025";
}
.fa-volume-off:before {
  content: "\f026";
}
.fa-volume-down:before {
  content: "\f027";
}
.fa-volume-up:before {
  content: "\f028";
}
.fa-qrcode:before {
  content: "\f029";
}
.fa-barcode:before {
  content: "\f02a";
}
.fa-tag:before {
  content: "\f02b";
}
.fa-tags:before {
  content: "\f02c";
}
.fa-book:before {
  content: "\f02d";
}
.fa-bookmark:before {
  content: "\f02e";
}
.fa-print:before {
  content: "\f02f";
}
.fa-camera:before {
  content: "\f030";
}
.fa-font:before {
  content: "\f031";
}
.fa-bold:before {
  content: "\f032";
}
.fa-italic:before {
  content: "\f033";
}
.fa-text-height:before {
  content: "\f034";
}
.fa-text-width:before {
  content: "\f035";
}
.fa-align-left:before {
  content: "\f036";
}
.fa-align-center:before {
  content: "\f037";
}
.fa-align-right:before {
  content: "\f038";
}
.fa-align-justify:before {
  content: "\f039";
}
.fa-list:before {
  content: "\f03a";
}
.fa-dedent:before,
.fa-outdent:before {
  content: "\f03b";
}
.fa-indent:before {
  content: "\f03c";
}
.fa-video-camera:before {
  content: "\f03d";
}
.fa-photo:before,
.fa-image:before,
.fa-picture-o:before {
  content: "\f03e";
}
.fa-pencil:before {
  content: "\f040";
}
.fa-map-marker:before {
  content: "\f041";
}
.fa-adjust:before {
  content: "\f042";
}
.fa-tint:before {
  content: "\f043";
}
.fa-edit:before,
.fa-pencil-square-o:before {
  content: "\f044";
}
.fa-share-square-o:before {
  content: "\f045";
}
.fa-check-square-o:before {
  content: "\f046";
}
.fa-arrows:before {
  content: "\f047";
}
.fa-step-backward:before {
  content: "\f048";
}
.fa-fast-backward:before {
  content: "\f049";
}
.fa-backward:before {
  content: "\f04a";
}
.fa-play:before {
  content: "\f04b";
}
.fa-pause:before {
  content: "\f04c";
}
.fa-stop:before {
  content: "\f04d";
}
.fa-forward:before {
  content: "\f04e";
}
.fa-fast-forward:before {
  content: "\f050";
}
.fa-step-forward:before {
  content: "\f051";
}
.fa-eject:before {
  content: "\f052";
}
.fa-chevron-left:before {
  content: "\f053";
}
.fa-chevron-right:before {
  content: "\f054";
}
.fa-plus-circle:before {
  content: "\f055";
}
.fa-minus-circle:before {
  content: "\f056";
}
.fa-times-circle:before {
  content: "\f057";
}
.fa-check-circle:before {
  content: "\f058";
}
.fa-question-circle:before {
  content: "\f059";
}
.fa-info-circle:before {
  content: "\f05a";
}
.fa-crosshairs:before {
  content: "\f05b";
}
.fa-times-circle-o:before {
  content: "\f05c";
}
.fa-check-circle-o:before {
  content: "\f05d";
}
.fa-ban:before {
  content: "\f05e";
}
.fa-arrow-left:before {
  content: "\f060";
}
.fa-arrow-right:before {
  content: "\f061";
}
.fa-arrow-up:before {
  content: "\f062";
}
.fa-arrow-down:before {
  content: "\f063";
}
.fa-mail-forward:before,
.fa-share:before {
  content: "\f064";
}
.fa-expand:before {
  content: "\f065";
}
.fa-compress:before {
  content: "\f066";
}
.fa-plus:before {
  content: "\f067";
}
.fa-minus:before {
  content: "\f068";
}
.fa-asterisk:before {
  content: "\f069";
}
.fa-exclamation-circle:before {
  content: "\f06a";
}
.fa-gift:before {
  content: "\f06b";
}
.fa-leaf:before {
  content: "\f06c";
}
.fa-fire:before {
  content: "\f06d";
}
.fa-eye:before {
  content: "\f06e";
}
.fa-eye-slash:before {
  content: "\f070";
}
.fa-warning:before,
.fa-exclamation-triangle:before {
  content: "\f071";
}
.fa-plane:before {
  content: "\f072";
}
.fa-calendar:before {
  content: "\f073";
}
.fa-random:before {
  content: "\f074";
}
.fa-comment:before {
  content: "\f075";
}
.fa-magnet:before {
  content: "\f076";
}
.fa-chevron-up:before {
  content: "\f077";
}
.fa-chevron-down:before {
  content: "\f078";
}
.fa-retweet:before {
  content: "\f079";
}
.fa-shopping-cart:before {
  content: "\f07a";
}
.fa-folder:before {
  content: "\f07b";
}
.fa-folder-open:before {
  content: "\f07c";
}
.fa-arrows-v:before {
  content: "\f07d";
}
.fa-arrows-h:before {
  content: "\f07e";
}
.fa-bar-chart-o:before,
.fa-bar-chart:before {
  content: "\f080";
}
.fa-twitter-square:before {
  content: "\f081";
}
.fa-facebook-square:before {
  content: "\f082";
}
.fa-camera-retro:before {
  content: "\f083";
}
.fa-key:before {
  content: "\f084";
}
.fa-gears:before,
.fa-cogs:before {
  content: "\f085";
}
.fa-comments:before {
  content: "\f086";
}
.fa-thumbs-o-up:before {
  content: "\f087";
}
.fa-thumbs-o-down:before {
  content: "\f088";
}
.fa-star-half:before {
  content: "\f089";
}
.fa-heart-o:before {
  content: "\f08a";
}
.fa-sign-out:before {
  content: "\f08b";
}
.fa-linkedin-square:before {
  content: "\f08c";
}
.fa-thumb-tack:before {
  content: "\f08d";
}
.fa-external-link:before {
  content: "\f08e";
}
.fa-sign-in:before {
  content: "\f090";
}
.fa-trophy:before {
  content: "\f091";
}
.fa-github-square:before {
  content: "\f092";
}
.fa-upload:before {
  content: "\f093";
}
.fa-lemon-o:before {
  content: "\f094";
}
.fa-phone:before {
  content: "\f095";
}
.fa-square-o:before {
  content: "\f096";
}
.fa-bookmark-o:before {
  content: "\f097";
}
.fa-phone-square:before {
  content: "\f098";
}
.fa-twitter:before {
  content: "\f099";
}
.fa-facebook-f:before,
.fa-facebook:before {
  content: "\f09a";
}
.fa-github:before {
  content: "\f09b";
}
.fa-unlock:before {
  content: "\f09c";
}
.fa-credit-card:before {
  content: "\f09d";
}
.fa-feed:before,
.fa-rss:before {
  content: "\f09e";
}
.fa-hdd-o:before {
  content: "\f0a0";
}
.fa-bullhorn:before {
  content: "\f0a1";
}
.fa-bell:before {
  content: "\f0f3";
}
.fa-certificate:before {
  content: "\f0a3";
}
.fa-hand-o-right:before {
  content: "\f0a4";
}
.fa-hand-o-left:before {
  content: "\f0a5";
}
.fa-hand-o-up:before {
  content: "\f0a6";
}
.fa-hand-o-down:before {
  content: "\f0a7";
}
.fa-arrow-circle-left:before {
  content: "\f0a8";
}
.fa-arrow-circle-right:before {
  content: "\f0a9";
}
.fa-arrow-circle-up:before {
  content: "\f0aa";
}
.fa-arrow-circle-down:before {
  content: "\f0ab";
}
.fa-globe:before {
  content: "\f0ac";
}
.fa-wrench:before {
  content: "\f0ad";
}
.fa-tasks:before {
  content: "\f0ae";
}
.fa-filter:before {
  content: "\f0b0";
}
.fa-briefcase:before {
  content: "\f0b1";
}
.fa-arrows-alt:before {
  content: "\f0b2";
}
.fa-group:before,
.fa-users:before {
  content: "\f0c0";
}
.fa-chain:before,
.fa-link:before {
  content: "\f0c1";
}
.fa-cloud:before {
  content: "\f0c2";
}
.fa-flask:before {
  content: "\f0c3";
}
.fa-cut:before,
.fa-scissors:before {
  content: "\f0c4";
}
.fa-copy:before,
.fa-files-o:before {
  content: "\f0c5";
}
.fa-paperclip:before {
  content: "\f0c6";
}
.fa-save:before,
.fa-floppy-o:before {
  content: "\f0c7";
}
.fa-square:before {
  content: "\f0c8";
}
.fa-navicon:before,
.fa-reorder:before,
.fa-bars:before {
  content: "\f0c9";
}
.fa-list-ul:before {
  content: "\f0ca";
}
.fa-list-ol:before {
  content: "\f0cb";
}
.fa-strikethrough:before {
  content: "\f0cc";
}
.fa-underline:before {
  content: "\f0cd";
}
.fa-table:before {
  content: "\f0ce";
}
.fa-magic:before {
  content: "\f0d0";
}
.fa-truck:before {
  content: "\f0d1";
}
.fa-pinterest:before {
  content: "\f0d2";
}
.fa-pinterest-square:before {
  content: "\f0d3";
}
.fa-google-plus-square:before {
  content: "\f0d4";
}
.fa-google-plus:before {
  content: "\f0d5";
}
.fa-money:before {
  content: "\f0d6";
}
.fa-caret-down:before {
  content: "\f0d7";
}
.fa-caret-up:before {
  content: "\f0d8";
}
.fa-caret-left:before {
  content: "\f0d9";
}
.fa-caret-right:before {
  content: "\f0da";
}
.fa-columns:before {
  content: "\f0db";
}
.fa-unsorted:before,
.fa-sort:before {
  content: "\f0dc";
}
.fa-sort-down:before,
.fa-sort-desc:before {
  content: "\f0dd";
}
.fa-sort-up:before,
.fa-sort-asc:before {
  content: "\f0de";
}
.fa-envelope:before {
  content: "\f0e0";
}
.fa-linkedin:before {
  content: "\f0e1";
}
.fa-rotate-left:before,
.fa-undo:before {
  content: "\f0e2";
}
.fa-legal:before,
.fa-gavel:before {
  content: "\f0e3";
}
.fa-dashboard:before,
.fa-tachometer:before {
  content: "\f0e4";
}
.fa-comment-o:before {
  content: "\f0e5";
}
.fa-comments-o:before {
  content: "\f0e6";
}
.fa-flash:before,
.fa-bolt:before {
  content: "\f0e7";
}
.fa-sitemap:before {
  content: "\f0e8";
}
.fa-umbrella:before {
  content: "\f0e9";
}
.fa-paste:before,
.fa-clipboard:before {
  content: "\f0ea";
}
.fa-lightbulb-o:before {
  content: "\f0eb";
}
.fa-exchange:before {
  content: "\f0ec";
}
.fa-cloud-download:before {
  content: "\f0ed";
}
.fa-cloud-upload:before {
  content: "\f0ee";
}
.fa-user-md:before {
  content: "\f0f0";
}
.fa-stethoscope:before {
  content: "\f0f1";
}
.fa-suitcase:before {
  content: "\f0f2";
}
.fa-bell-o:before {
  content: "\f0a2";
}
.fa-coffee:before {
  content: "\f0f4";
}
.fa-cutlery:before {
  content: "\f0f5";
}
.fa-file-text-o:before {
  content: "\f0f6";
}
.fa-building-o:before {
  content: "\f0f7";
}
.fa-hospital-o:before {
  content: "\f0f8";
}
.fa-ambulance:before {
  content: "\f0f9";
}
.fa-medkit:before {
  content: "\f0fa";
}
.fa-fighter-jet:before {
  content: "\f0fb";
}
.fa-beer:before {
  content: "\f0fc";
}
.fa-h-square:before {
  content: "\f0fd";
}
.fa-plus-square:before {
  content: "\f0fe";
}
.fa-angle-double-left:before {
  content: "\f100";
}
.fa-angle-double-right:before {
  content: "\f101";
}
.fa-angle-double-up:before {
  content: "\f102";
}
.fa-angle-double-down:before {
  content: "\f103";
}
.fa-angle-left:before {
  content: "\f104";
}
.fa-angle-right:before {
  content: "\f105";
}
.fa-angle-up:before {
  content: "\f106";
}
.fa-angle-down:before {
  content: "\f107";
}
.fa-desktop:before {
  content: "\f108";
}
.fa-laptop:before {
  content: "\f109";
}
.fa-tablet:before {
  content: "\f10a";
}
.fa-mobile-phone:before,
.fa-mobile:before {
  content: "\f10b";
}
.fa-circle-o:before {
  content: "\f10c";
}
.fa-quote-left:before {
  content: "\f10d";
}
.fa-quote-right:before {
  content: "\f10e";
}
.fa-spinner:before {
  content: "\f110";
}
.fa-circle:before {
  content: "\f111";
}
.fa-mail-reply:before,
.fa-reply:before {
  content: "\f112";
}
.fa-github-alt:before {
  content: "\f113";
}
.fa-folder-o:before {
  content: "\f114";
}
.fa-folder-open-o:before {
  content: "\f115";
}
.fa-smile-o:before {
  content: "\f118";
}
.fa-frown-o:before {
  content: "\f119";
}
.fa-meh-o:before {
  content: "\f11a";
}
.fa-gamepad:before {
  content: "\f11b";
}
.fa-keyboard-o:before {
  content: "\f11c";
}
.fa-flag-o:before {
  content: "\f11d";
}
.fa-flag-checkered:before {
  content: "\f11e";
}
.fa-terminal:before {
  content: "\f120";
}
.fa-code:before {
  content: "\f121";
}
.fa-mail-reply-all:before,
.fa-reply-all:before {
  content: "\f122";
}
.fa-star-half-empty:before,
.fa-star-half-full:before,
.fa-star-half-o:before {
  content: "\f123";
}
.fa-location-arrow:before {
  content: "\f124";
}
.fa-crop:before {
  content: "\f125";
}
.fa-code-fork:before {
  content: "\f126";
}
.fa-unlink:before,
.fa-chain-broken:before {
  content: "\f127";
}
.fa-question:before {
  content: "\f128";
}
.fa-info:before {
  content: "\f129";
}
.fa-exclamation:before {
  content: "\f12a";
}
.fa-superscript:before {
  content: "\f12b";
}
.fa-subscript:before {
  content: "\f12c";
}
.fa-eraser:before {
  content: "\f12d";
}
.fa-puzzle-piece:before {
  content: "\f12e";
}
.fa-microphone:before {
  content: "\f130";
}
.fa-microphone-slash:before {
  content: "\f131";
}
.fa-shield:before {
  content: "\f132";
}
.fa-calendar-o:before {
  content: "\f133";
}
.fa-fire-extinguisher:before {
  content: "\f134";
}
.fa-rocket:before {
  content: "\f135";
}
.fa-maxcdn:before {
  content: "\f136";
}
.fa-chevron-circle-left:before {
  content: "\f137";
}
.fa-chevron-circle-right:before {
  content: "\f138";
}
.fa-chevron-circle-up:before {
  content: "\f139";
}
.fa-chevron-circle-down:before {
  content: "\f13a";
}
.fa-html5:before {
  content: "\f13b";
}
.fa-css3:before {
  content: "\f13c";
}
.fa-anchor:before {
  content: "\f13d";
}
.fa-unlock-alt:before {
  content: "\f13e";
}
.fa-bullseye:before {
  content: "\f140";
}
.fa-ellipsis-h:before {
  content: "\f141";
}
.fa-ellipsis-v:before {
  content: "\f142";
}
.fa-rss-square:before {
  content: "\f143";
}
.fa-play-circle:before {
  content: "\f144";
}
.fa-ticket:before {
  content: "\f145";
}
.fa-minus-square:before {
  content: "\f146";
}
.fa-minus-square-o:before {
  content: "\f147";
}
.fa-level-up:before {
  content: "\f148";
}
.fa-level-down:before {
  content: "\f149";
}
.fa-check-square:before {
  content: "\f14a";
}
.fa-pencil-square:before {
  content: "\f14b";
}
.fa-external-link-square:before {
  content: "\f14c";
}
.fa-share-square:before {
  content: "\f14d";
}
.fa-compass:before {
  content: "\f14e";
}
.fa-toggle-down:before,
.fa-caret-square-o-down:before {
  content: "\f150";
}
.fa-toggle-up:before,
.fa-caret-square-o-up:before {
  content: "\f151";
}
.fa-toggle-right:before,
.fa-caret-square-o-right:before {
  content: "\f152";
}
.fa-euro:before,
.fa-eur:before {
  content: "\f153";
}
.fa-gbp:before {
  content: "\f154";
}
.fa-dollar:before,
.fa-usd:before {
  content: "\f155";
}
.fa-rupee:before,
.fa-inr:before {
  content: "\f156";
}
.fa-cny:before,
.fa-rmb:before,
.fa-yen:before,
.fa-jpy:before {
  content: "\f157";
}
.fa-ruble:before,
.fa-rouble:before,
.fa-rub:before {
  content: "\f158";
}
.fa-won:before,
.fa-krw:before {
  content: "\f159";
}
.fa-bitcoin:before,
.fa-btc:before {
  content: "\f15a";
}
.fa-file:before {
  content: "\f15b";
}
.fa-file-text:before {
  content: "\f15c";
}
.fa-sort-alpha-asc:before {
  content: "\f15d";
}
.fa-sort-alpha-desc:before {
  content: "\f15e";
}
.fa-sort-amount-asc:before {
  content: "\f160";
}
.fa-sort-amount-desc:before {
  content: "\f161";
}
.fa-sort-numeric-asc:before {
  content: "\f162";
}
.fa-sort-numeric-desc:before {
  content: "\f163";
}
.fa-thumbs-up:before {
  content: "\f164";
}
.fa-thumbs-down:before {
  content: "\f165";
}
.fa-youtube-square:before {
  content: "\f166";
}
.fa-youtube:before {
  content: "\f167";
}
.fa-xing:before {
  content: "\f168";
}
.fa-xing-square:before {
  content: "\f169";
}
.fa-youtube-play:before {
  content: "\f16a";
}
.fa-dropbox:before {
  content: "\f16b";
}
.fa-stack-overflow:before {
  content: "\f16c";
}
.fa-instagram:before {
  content: "\f16d";
}
.fa-flickr:before {
  content: "\f16e";
}
.fa-adn:before {
  content: "\f170";
}
.fa-bitbucket:before {
  content: "\f171";
}
.fa-bitbucket-square:before {
  content: "\f172";
}
.fa-tumblr:before {
  content: "\f173";
}
.fa-tumblr-square:before {
  content: "\f174";
}
.fa-long-arrow-down:before {
  content: "\f175";
}
.fa-long-arrow-up:before {
  content: "\f176";
}
.fa-long-arrow-left:before {
  content: "\f177";
}
.fa-long-arrow-right:before {
  content: "\f178";
}
.fa-apple:before {
  content: "\f179";
}
.fa-windows:before {
  content: "\f17a";
}
.fa-android:before {
  content: "\f17b";
}
.fa-linux:before {
  content: "\f17c";
}
.fa-dribbble:before {
  content: "\f17d";
}
.fa-skype:before {
  content: "\f17e";
}
.fa-foursquare:before {
  content: "\f180";
}
.fa-trello:before {
  content: "\f181";
}
.fa-female:before {
  content: "\f182";
}
.fa-male:before {
  content: "\f183";
}
.fa-gittip:before,
.fa-gratipay:before {
  content: "\f184";
}
.fa-sun-o:before {
  content: "\f185";
}
.fa-moon-o:before {
  content: "\f186";
}
.fa-archive:before {
  content: "\f187";
}
.fa-bug:before {
  content: "\f188";
}
.fa-vk:before {
  content: "\f189";
}
.fa-weibo:before {
  content: "\f18a";
}
.fa-renren:before {
  content: "\f18b";
}
.fa-pagelines:before {
  content: "\f18c";
}
.fa-stack-exchange:before {
  content: "\f18d";
}
.fa-arrow-circle-o-right:before {
  content: "\f18e";
}
.fa-arrow-circle-o-left:before {
  content: "\f190";
}
.fa-toggle-left:before,
.fa-caret-square-o-left:before {
  content: "\f191";
}
.fa-dot-circle-o:before {
  content: "\f192";
}
.fa-wheelchair:before {
  content: "\f193";
}
.fa-vimeo-square:before {
  content: "\f194";
}
.fa-turkish-lira:before,
.fa-try:before {
  content: "\f195";
}
.fa-plus-square-o:before {
  content: "\f196";
}
.fa-space-shuttle:before {
  content: "\f197";
}
.fa-slack:before {
  content: "\f198";
}
.fa-envelope-square:before {
  content: "\f199";
}
.fa-wordpress:before {
  content: "\f19a";
}
.fa-openid:before {
  content: "\f19b";
}
.fa-institution:before,
.fa-bank:before,
.fa-university:before {
  content: "\f19c";
}
.fa-mortar-board:before,
.fa-graduation-cap:before {
  content: "\f19d";
}
.fa-yahoo:before {
  content: "\f19e";
}
.fa-google:before {
  content: "\f1a0";
}
.fa-reddit:before {
  content: "\f1a1";
}
.fa-reddit-square:before {
  content: "\f1a2";
}
.fa-stumbleupon-circle:before {
  content: "\f1a3";
}
.fa-stumbleupon:before {
  content: "\f1a4";
}
.fa-delicious:before {
  content: "\f1a5";
}
.fa-digg:before {
  content: "\f1a6";
}
.fa-pied-piper-pp:before {
  content: "\f1a7";
}
.fa-pied-piper-alt:before {
  content: "\f1a8";
}
.fa-drupal:before {
  content: "\f1a9";
}
.fa-joomla:before {
  content: "\f1aa";
}
.fa-language:before {
  content: "\f1ab";
}
.fa-fax:before {
  content: "\f1ac";
}
.fa-building:before {
  content: "\f1ad";
}
.fa-child:before {
  content: "\f1ae";
}
.fa-paw:before {
  content: "\f1b0";
}
.fa-spoon:before {
  content: "\f1b1";
}
.fa-cube:before {
  content: "\f1b2";
}
.fa-cubes:before {
  content: "\f1b3";
}
.fa-behance:before {
  content: "\f1b4";
}
.fa-behance-square:before {
  content: "\f1b5";
}
.fa-steam:before {
  content: "\f1b6";
}
.fa-steam-square:before {
  content: "\f1b7";
}
.fa-recycle:before {
  content: "\f1b8";
}
.fa-automobile:before,
.fa-car:before {
  content: "\f1b9";
}
.fa-cab:before,
.fa-taxi:before {
  content: "\f1ba";
}
.fa-tree:before {
  content: "\f1bb";
}
.fa-spotify:before {
  content: "\f1bc";
}
.fa-deviantart:before {
  content: "\f1bd";
}
.fa-soundcloud:before {
  content: "\f1be";
}
.fa-database:before {
  content: "\f1c0";
}
.fa-file-pdf-o:before {
  content: "\f1c1";
}
.fa-file-word-o:before {
  content: "\f1c2";
}
.fa-file-excel-o:before {
  content: "\f1c3";
}
.fa-file-powerpoint-o:before {
  content: "\f1c4";
}
.fa-file-photo-o:before,
.fa-file-picture-o:before,
.fa-file-image-o:before {
  content: "\f1c5";
}
.fa-file-zip-o:before,
.fa-file-archive-o:before {
  content: "\f1c6";
}
.fa-file-sound-o:before,
.fa-file-audio-o:before {
  content: "\f1c7";
}
.fa-file-movie-o:before,
.fa-file-video-o:before {
  content: "\f1c8";
}
.fa-file-code-o:before {
  content: "\f1c9";
}
.fa-vine:before {
  content: "\f1ca";
}
.fa-codepen:before {
  content: "\f1cb";
}
.fa-jsfiddle:before {
  content: "\f1cc";
}
.fa-life-bouy:before,
.fa-life-buoy:before,
.fa-life-saver:before,
.fa-support:before,
.fa-life-ring:before {
  content: "\f1cd";
}
.fa-circle-o-notch:before {
  content: "\f1ce";
}
.fa-ra:before,
.fa-resistance:before,
.fa-rebel:before {
  content: "\f1d0";
}
.fa-ge:before,
.fa-empire:before {
  content: "\f1d1";
}
.fa-git-square:before {
  content: "\f1d2";
}
.fa-git:before {
  content: "\f1d3";
}
.fa-y-combinator-square:before,
.fa-yc-square:before,
.fa-hacker-news:before {
  content: "\f1d4";
}
.fa-tencent-weibo:before {
  content: "\f1d5";
}
.fa-qq:before {
  content: "\f1d6";
}
.fa-wechat:before,
.fa-weixin:before {
  content: "\f1d7";
}
.fa-send:before,
.fa-paper-plane:before {
  content: "\f1d8";
}
.fa-send-o:before,
.fa-paper-plane-o:before {
  content: "\f1d9";
}
.fa-history:before {
  content: "\f1da";
}
.fa-circle-thin:before {
  content: "\f1db";
}
.fa-header:before {
  content: "\f1dc";
}
.fa-paragraph:before {
  content: "\f1dd";
}
.fa-sliders:before {
  content: "\f1de";
}
.fa-share-alt:before {
  content: "\f1e0";
}
.fa-share-alt-square:before {
  content: "\f1e1";
}
.fa-bomb:before {
  content: "\f1e2";
}
.fa-soccer-ball-o:before,
.fa-futbol-o:before {
  content: "\f1e3";
}
.fa-tty:before {
  content: "\f1e4";
}
.fa-binoculars:before {
  content: "\f1e5";
}
.fa-plug:before {
  content: "\f1e6";
}
.fa-slideshare:before {
  content: "\f1e7";
}
.fa-twitch:before {
  content: "\f1e8";
}
.fa-yelp:before {
  content: "\f1e9";
}
.fa-newspaper-o:before {
  content: "\f1ea";
}
.fa-wifi:before {
  content: "\f1eb";
}
.fa-calculator:before {
  content: "\f1ec";
}
.fa-paypal:before {
  content: "\f1ed";
}
.fa-google-wallet:before {
  content: "\f1ee";
}
.fa-cc-visa:before {
  content: "\f1f0";
}
.fa-cc-mastercard:before {
  content: "\f1f1";
}
.fa-cc-discover:before {
  content: "\f1f2";
}
.fa-cc-amex:before {
  content: "\f1f3";
}
.fa-cc-paypal:before {
  content: "\f1f4";
}
.fa-cc-stripe:before {
  content: "\f1f5";
}
.fa-bell-slash:before {
  content: "\f1f6";
}
.fa-bell-slash-o:before {
  content: "\f1f7";
}
.fa-trash:before {
  content: "\f1f8";
}
.fa-copyright:before {
  content: "\f1f9";
}
.fa-at:before {
  content: "\f1fa";
}
.fa-eyedropper:before {
  content: "\f1fb";
}
.fa-paint-brush:before {
  content: "\f1fc";
}
.fa-birthday-cake:before {
  content: "\f1fd";
}
.fa-area-chart:before {
  content: "\f1fe";
}
.fa-pie-chart:before {
  content: "\f200";
}
.fa-line-chart:before {
  content: "\f201";
}
.fa-lastfm:before {
  content: "\f202";
}
.fa-lastfm-square:before {
  content: "\f203";
}
.fa-toggle-off:before {
  content: "\f204";
}
.fa-toggle-on:before {
  content: "\f205";
}
.fa-bicycle:before {
  content: "\f206";
}
.fa-bus:before {
  content: "\f207";
}
.fa-ioxhost:before {
  content: "\f208";
}
.fa-angellist:before {
  content: "\f209";
}
.fa-cc:before {
  content: "\f20a";
}
.fa-shekel:before,
.fa-sheqel:before,
.fa-ils:before {
  content: "\f20b";
}
.fa-meanpath:before {
  content: "\f20c";
}
.fa-buysellads:before {
  content: "\f20d";
}
.fa-connectdevelop:before {
  content: "\f20e";
}
.fa-dashcube:before {
  content: "\f210";
}
.fa-forumbee:before {
  content: "\f211";
}
.fa-leanpub:before {
  content: "\f212";
}
.fa-sellsy:before {
  content: "\f213";
}
.fa-shirtsinbulk:before {
  content: "\f214";
}
.fa-simplybuilt:before {
  content: "\f215";
}
.fa-skyatlas:before {
  content: "\f216";
}
.fa-cart-plus:before {
  content: "\f217";
}
.fa-cart-arrow-down:before {
  content: "\f218";
}
.fa-diamond:before {
  content: "\f219";
}
.fa-ship:before {
  content: "\f21a";
}
.fa-user-secret:before {
  content: "\f21b";
}
.fa-motorcycle:before {
  content: "\f21c";
}
.fa-street-view:before {
  content: "\f21d";
}
.fa-heartbeat:before {
  content: "\f21e";
}
.fa-venus:before {
  content: "\f221";
}
.fa-mars:before {
  content: "\f222";
}
.fa-mercury:before {
  content: "\f223";
}
.fa-intersex:before,
.fa-transgender:before {
  content: "\f224";
}
.fa-transgender-alt:before {
  content: "\f225";
}
.fa-venus-double:before {
  content: "\f226";
}
.fa-mars-double:before {
  content: "\f227";
}
.fa-venus-mars:before {
  content: "\f228";
}
.fa-mars-stroke:before {
  content: "\f229";
}
.fa-mars-stroke-v:before {
  content: "\f22a";
}
.fa-mars-stroke-h:before {
  content: "\f22b";
}
.fa-neuter:before {
  content: "\f22c";
}
.fa-genderless:before {
  content: "\f22d";
}
.fa-facebook-official:before {
  content: "\f230";
}
.fa-pinterest-p:before {
  content: "\f231";
}
.fa-whatsapp:before {
  content: "\f232";
}
.fa-server:before {
  content: "\f233";
}
.fa-user-plus:before {
  content: "\f234";
}
.fa-user-times:before {
  content: "\f235";
}
.fa-hotel:before,
.fa-bed:before {
  content: "\f236";
}
.fa-viacoin:before {
  content: "\f237";
}
.fa-train:before {
  content: "\f238";
}
.fa-subway:before {
  content: "\f239";
}
.fa-medium:before {
  content: "\f23a";
}
.fa-yc:before,
.fa-y-combinator:before {
  content: "\f23b";
}
.fa-optin-monster:before {
  content: "\f23c";
}
.fa-opencart:before {
  content: "\f23d";
}
.fa-expeditedssl:before {
  content: "\f23e";
}
.fa-battery-4:before,
.fa-battery:before,
.fa-battery-full:before {
  content: "\f240";
}
.fa-battery-3:before,
.fa-battery-three-quarters:before {
  content: "\f241";
}
.fa-battery-2:before,
.fa-battery-half:before {
  content: "\f242";
}
.fa-battery-1:before,
.fa-battery-quarter:before {
  content: "\f243";
}
.fa-battery-0:before,
.fa-battery-empty:before {
  content: "\f244";
}
.fa-mouse-pointer:before {
  content: "\f245";
}
.fa-i-cursor:before {
  content: "\f246";
}
.fa-object-group:before {
  content: "\f247";
}
.fa-object-ungroup:before {
  content: "\f248";
}
.fa-sticky-note:before {
  content: "\f249";
}
.fa-sticky-note-o:before {
  content: "\f24a";
}
.fa-cc-jcb:before {
  content: "\f24b";
}
.fa-cc-diners-club:before {
  content: "\f24c";
}
.fa-clone:before {
  content: "\f24d";
}
.fa-balance-scale:before {
  content: "\f24e";
}
.fa-hourglass-o:before {
  content: "\f250";
}
.fa-hourglass-1:before,
.fa-hourglass-start:before {
  content: "\f251";
}
.fa-hourglass-2:before,
.fa-hourglass-half:before {
  content: "\f252";
}
.fa-hourglass-3:before,
.fa-hourglass-end:before {
  content: "\f253";
}
.fa-hourglass:before {
  content: "\f254";
}
.fa-hand-grab-o:before,
.fa-hand-rock-o:before {
  content: "\f255";
}
.fa-hand-stop-o:before,
.fa-hand-paper-o:before {
  content: "\f256";
}
.fa-hand-scissors-o:before {
  content: "\f257";
}
.fa-hand-lizard-o:before {
  content: "\f258";
}
.fa-hand-spock-o:before {
  content: "\f259";
}
.fa-hand-pointer-o:before {
  content: "\f25a";
}
.fa-hand-peace-o:before {
  content: "\f25b";
}
.fa-trademark:before {
  content: "\f25c";
}
.fa-registered:before {
  content: "\f25d";
}
.fa-creative-commons:before {
  content: "\f25e";
}
.fa-gg:before {
  content: "\f260";
}
.fa-gg-circle:before {
  content: "\f261";
}
.fa-tripadvisor:before {
  content: "\f262";
}
.fa-odnoklassniki:before {
  content: "\f263";
}
.fa-odnoklassniki-square:before {
  content: "\f264";
}
.fa-get-pocket:before {
  content: "\f265";
}
.fa-wikipedia-w:before {
  content: "\f266";
}
.fa-safari:before {
  content: "\f267";
}
.fa-chrome:before {
  content: "\f268";
}
.fa-firefox:before {
  content: "\f269";
}
.fa-opera:before {
  content: "\f26a";
}
.fa-internet-explorer:before {
  content: "\f26b";
}
.fa-tv:before,
.fa-television:before {
  content: "\f26c";
}
.fa-contao:before {
  content: "\f26d";
}
.fa-500px:before {
  content: "\f26e";
}
.fa-amazon:before {
  content: "\f270";
}
.fa-calendar-plus-o:before {
  content: "\f271";
}
.fa-calendar-minus-o:before {
  content: "\f272";
}
.fa-calendar-times-o:before {
  content: "\f273";
}
.fa-calendar-check-o:before {
  content: "\f274";
}
.fa-industry:before {
  content: "\f275";
}
.fa-map-pin:before {
  content: "\f276";
}
.fa-map-signs:before {
  content: "\f277";
}
.fa-map-o:before {
  content: "\f278";
}
.fa-map:before {
  content: "\f279";
}
.fa-commenting:before {
  content: "\f27a";
}
.fa-commenting-o:before {
  content: "\f27b";
}
.fa-houzz:before {
  content: "\f27c";
}
.fa-vimeo:before {
  content: "\f27d";
}
.fa-black-tie:before {
  content: "\f27e";
}
.fa-fonticons:before {
  content: "\f280";
}
.fa-reddit-alien:before {
  content: "\f281";
}
.fa-edge:before {
  content: "\f282";
}
.fa-credit-card-alt:before {
  content: "\f283";
}
.fa-codiepie:before {
  content: "\f284";
}
.fa-modx:before {
  content: "\f285";
}
.fa-fort-awesome:before {
  content: "\f286";
}
.fa-usb:before {
  content: "\f287";
}
.fa-product-hunt:before {
  content: "\f288";
}
.fa-mixcloud:before {
  content: "\f289";
}
.fa-scribd:before {
  content: "\f28a";
}
.fa-pause-circle:before {
  content: "\f28b";
}
.fa-pause-circle-o:before {
  content: "\f28c";
}
.fa-stop-circle:before {
  content: "\f28d";
}
.fa-stop-circle-o:before {
  content: "\f28e";
}
.fa-shopping-bag:before {
  content: "\f290";
}
.fa-shopping-basket:before {
  content: "\f291";
}
.fa-hashtag:before {
  content: "\f292";
}
.fa-bluetooth:before {
  content: "\f293";
}
.fa-bluetooth-b:before {
  content: "\f294";
}
.fa-percent:before {
  content: "\f295";
}
.fa-gitlab:before {
  content: "\f296";
}
.fa-wpbeginner:before {
  content: "\f297";
}
.fa-wpforms:before {
  content: "\f298";
}
.fa-envira:before {
  content: "\f299";
}
.fa-universal-access:before {
  content: "\f29a";
}
.fa-wheelchair-alt:before {
  content: "\f29b";
}
.fa-question-circle-o:before {
  content: "\f29c";
}
.fa-blind:before {
  content: "\f29d";
}
.fa-audio-description:before {
  content: "\f29e";
}
.fa-volume-control-phone:before {
  content: "\f2a0";
}
.fa-braille:before {
  content: "\f2a1";
}
.fa-assistive-listening-systems:before {
  content: "\f2a2";
}
.fa-asl-interpreting:before,
.fa-american-sign-language-interpreting:before {
  content: "\f2a3";
}
.fa-deafness:before,
.fa-hard-of-hearing:before,
.fa-deaf:before {
  content: "\f2a4";
}
.fa-glide:before {
  content: "\f2a5";
}
.fa-glide-g:before {
  content: "\f2a6";
}
.fa-signing:before,
.fa-sign-language:before {
  content: "\f2a7";
}
.fa-low-vision:before {
  content: "\f2a8";
}
.fa-viadeo:before {
  content: "\f2a9";
}
.fa-viadeo-square:before {
  content: "\f2aa";
}
.fa-snapchat:before {
  content: "\f2ab";
}
.fa-snapchat-ghost:before {
  content: "\f2ac";
}
.fa-snapchat-square:before {
  content: "\f2ad";
}
.fa-pied-piper:before {
  content: "\f2ae";
}
.fa-first-order:before {
  content: "\f2b0";
}
.fa-yoast:before {
  content: "\f2b1";
}
.fa-themeisle:before {
  content: "\f2b2";
}
.fa-google-plus-circle:before,
.fa-google-plus-official:before {
  content: "\f2b3";
}
.fa-fa:before,
.fa-font-awesome:before {
  content: "\f2b4";
}
.fa-handshake-o:before {
  content: "\f2b5";
}
.fa-envelope-open:before {
  content: "\f2b6";
}
.fa-envelope-open-o:before {
  content: "\f2b7";
}
.fa-linode:before {
  content: "\f2b8";
}
.fa-address-book:before {
  content: "\f2b9";
}
.fa-address-book-o:before {
  content: "\f2ba";
}
.fa-vcard:before,
.fa-address-card:before {
  content: "\f2bb";
}
.fa-vcard-o:before,
.fa-address-card-o:before {
  content: "\f2bc";
}
.fa-user-circle:before {
  content: "\f2bd";
}
.fa-user-circle-o:before {
  content: "\f2be";
}
.fa-user-o:before {
  content: "\f2c0";
}
.fa-id-badge:before {
  content: "\f2c1";
}
.fa-drivers-license:before,
.fa-id-card:before {
  content: "\f2c2";
}
.fa-drivers-license-o:before,
.fa-id-card-o:before {
  content: "\f2c3";
}
.fa-quora:before {
  content: "\f2c4";
}
.fa-free-code-camp:before {
  content: "\f2c5";
}
.fa-telegram:before {
  content: "\f2c6";
}
.fa-thermometer-4:before,
.fa-thermometer:before,
.fa-thermometer-full:before {
  content: "\f2c7";
}
.fa-thermometer-3:before,
.fa-thermometer-three-quarters:before {
  content: "\f2c8";
}
.fa-thermometer-2:before,
.fa-thermometer-half:before {
  content: "\f2c9";
}
.fa-thermometer-1:before,
.fa-thermometer-quarter:before {
  content: "\f2ca";
}
.fa-thermometer-0:before,
.fa-thermometer-empty:before {
  content: "\f2cb";
}
.fa-shower:before {
  content: "\f2cc";
}
.fa-bathtub:before,
.fa-s15:before,
.fa-bath:before {
  content: "\f2cd";
}
.fa-podcast:before {
  content: "\f2ce";
}
.fa-window-maximize:before {
  content: "\f2d0";
}
.fa-window-minimize:before {
  content: "\f2d1";
}
.fa-window-restore:before {
  content: "\f2d2";
}
.fa-times-rectangle:before,
.fa-window-close:before {
  content: "\f2d3";
}
.fa-times-rectangle-o:before,
.fa-window-close-o:before {
  content: "\f2d4";
}
.fa-bandcamp:before {
  content: "\f2d5";
}
.fa-grav:before {
  content: "\f2d6";
}
.fa-etsy:before {
  content: "\f2d7";
}
.fa-imdb:before {
  content: "\f2d8";
}
.fa-ravelry:before {
  content: "\f2d9";
}
.fa-eercast:before {
  content: "\f2da";
}
.fa-microchip:before {
  content: "\f2db";
}
.fa-snowflake-o:before {
  content: "\f2dc";
}
.fa-superpowers:before {
  content: "\f2dd";
}
.fa-wpexplorer:before {
  content: "\f2de";
}
.fa-meetup:before {
  content: "\f2e0";
}
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  border: 0;
}
.sr-only-focusable:active,
.sr-only-focusable:focus {
  position: static;
  width: auto;
  height: auto;
  margin: 0;
  overflow: visible;
  clip: auto;
}
.sr-only-focusable:active,
.sr-only-focusable:focus {
  position: static;
  width: auto;
  height: auto;
  margin: 0;
  overflow: visible;
  clip: auto;
}
/*!
*
* IPython base
*
*/
.modal.fade .modal-dialog {
  -webkit-transform: translate(0, 0);
  -ms-transform: translate(0, 0);
  -o-transform: translate(0, 0);
  transform: translate(0, 0);
}
code {
  color: #000;
}
pre {
  font-size: inherit;
  line-height: inherit;
}
label {
  font-weight: normal;
}
/* Make the page background atleast 100% the height of the view port */
/* Make the page itself atleast 70% the height of the view port */
.border-box-sizing {
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
}
.corner-all {
  border-radius: 2px;
}
.no-padding {
  padding: 0px;
}
/* Flexible box model classes */
/* Taken from Alex Russell http://infrequently.org/2009/08/css-3-progress/ */
/* This file is a compatability layer.  It allows the usage of flexible box
model layouts accross multiple browsers, including older browsers.  The newest,
universal implementation of the flexible box model is used when available (see
`Modern browsers` comments below).  Browsers that are known to implement this
new spec completely include:

    Firefox 28.0+
    Chrome 29.0+
    Internet Explorer 11+
    Opera 17.0+

Browsers not listed, including Safari, are supported via the styling under the
`Old browsers` comments below.
*/
.hbox {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
}
.hbox > * {
  /* Old browsers */
  -webkit-box-flex: 0;
  -moz-box-flex: 0;
  box-flex: 0;
  /* Modern browsers */
  flex: none;
}
.vbox {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
}
.vbox > * {
  /* Old browsers */
  -webkit-box-flex: 0;
  -moz-box-flex: 0;
  box-flex: 0;
  /* Modern browsers */
  flex: none;
}
.hbox.reverse,
.vbox.reverse,
.reverse {
  /* Old browsers */
  -webkit-box-direction: reverse;
  -moz-box-direction: reverse;
  box-direction: reverse;
  /* Modern browsers */
  flex-direction: row-reverse;
}
.hbox.box-flex0,
.vbox.box-flex0,
.box-flex0 {
  /* Old browsers */
  -webkit-box-flex: 0;
  -moz-box-flex: 0;
  box-flex: 0;
  /* Modern browsers */
  flex: none;
  width: auto;
}
.hbox.box-flex1,
.vbox.box-flex1,
.box-flex1 {
  /* Old browsers */
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  box-flex: 1;
  /* Modern browsers */
  flex: 1;
}
.hbox.box-flex,
.vbox.box-flex,
.box-flex {
  /* Old browsers */
  /* Old browsers */
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  box-flex: 1;
  /* Modern browsers */
  flex: 1;
}
.hbox.box-flex2,
.vbox.box-flex2,
.box-flex2 {
  /* Old browsers */
  -webkit-box-flex: 2;
  -moz-box-flex: 2;
  box-flex: 2;
  /* Modern browsers */
  flex: 2;
}
.box-group1 {
  /*  Deprecated */
  -webkit-box-flex-group: 1;
  -moz-box-flex-group: 1;
  box-flex-group: 1;
}
.box-group2 {
  /* Deprecated */
  -webkit-box-flex-group: 2;
  -moz-box-flex-group: 2;
  box-flex-group: 2;
}
.hbox.start,
.vbox.start,
.start {
  /* Old browsers */
  -webkit-box-pack: start;
  -moz-box-pack: start;
  box-pack: start;
  /* Modern browsers */
  justify-content: flex-start;
}
.hbox.end,
.vbox.end,
.end {
  /* Old browsers */
  -webkit-box-pack: end;
  -moz-box-pack: end;
  box-pack: end;
  /* Modern browsers */
  justify-content: flex-end;
}
.hbox.center,
.vbox.center,
.center {
  /* Old browsers */
  -webkit-box-pack: center;
  -moz-box-pack: center;
  box-pack: center;
  /* Modern browsers */
  justify-content: center;
}
.hbox.baseline,
.vbox.baseline,
.baseline {
  /* Old browsers */
  -webkit-box-pack: baseline;
  -moz-box-pack: baseline;
  box-pack: baseline;
  /* Modern browsers */
  justify-content: baseline;
}
.hbox.stretch,
.vbox.stretch,
.stretch {
  /* Old browsers */
  -webkit-box-pack: stretch;
  -moz-box-pack: stretch;
  box-pack: stretch;
  /* Modern browsers */
  justify-content: stretch;
}
.hbox.align-start,
.vbox.align-start,
.align-start {
  /* Old browsers */
  -webkit-box-align: start;
  -moz-box-align: start;
  box-align: start;
  /* Modern browsers */
  align-items: flex-start;
}
.hbox.align-end,
.vbox.align-end,
.align-end {
  /* Old browsers */
  -webkit-box-align: end;
  -moz-box-align: end;
  box-align: end;
  /* Modern browsers */
  align-items: flex-end;
}
.hbox.align-center,
.vbox.align-center,
.align-center {
  /* Old browsers */
  -webkit-box-align: center;
  -moz-box-align: center;
  box-align: center;
  /* Modern browsers */
  align-items: center;
}
.hbox.align-baseline,
.vbox.align-baseline,
.align-baseline {
  /* Old browsers */
  -webkit-box-align: baseline;
  -moz-box-align: baseline;
  box-align: baseline;
  /* Modern browsers */
  align-items: baseline;
}
.hbox.align-stretch,
.vbox.align-stretch,
.align-stretch {
  /* Old browsers */
  -webkit-box-align: stretch;
  -moz-box-align: stretch;
  box-align: stretch;
  /* Modern browsers */
  align-items: stretch;
}
div.error {
  margin: 2em;
  text-align: center;
}
div.error > h1 {
  font-size: 500%;
  line-height: normal;
}
div.error > p {
  font-size: 200%;
  line-height: normal;
}
div.traceback-wrapper {
  text-align: left;
  max-width: 800px;
  margin: auto;
}
div.traceback-wrapper pre.traceback {
  max-height: 600px;
  overflow: auto;
}
/**
 * Primary styles
 *
 * Author: Jupyter Development Team
 */
body {
  background-color: #fff;
  /* This makes sure that the body covers the entire window and needs to
       be in a different element than the display: box in wrapper below */
  position: absolute;
  left: 0px;
  right: 0px;
  top: 0px;
  bottom: 0px;
  overflow: visible;
}
body > #header {
  /* Initially hidden to prevent FLOUC */
  display: none;
  background-color: #fff;
  /* Display over codemirror */
  position: relative;
  z-index: 100;
}
body > #header #header-container {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  padding: 5px;
  padding-bottom: 5px;
  padding-top: 5px;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
}
body > #header .header-bar {
  width: 100%;
  height: 1px;
  background: #e7e7e7;
  margin-bottom: -1px;
}
@media print {
  body > #header {
    display: none !important;
  }
}
#header-spacer {
  width: 100%;
  visibility: hidden;
}
@media print {
  #header-spacer {
    display: none;
  }
}
#ipython_notebook {
  padding-left: 0px;
  padding-top: 1px;
  padding-bottom: 1px;
}
[dir="rtl"] #ipython_notebook {
  margin-right: 10px;
  margin-left: 0;
}
[dir="rtl"] #ipython_notebook.pull-left {
  float: right !important;
  float: right;
}
.flex-spacer {
  flex: 1;
}
#noscript {
  width: auto;
  padding-top: 16px;
  padding-bottom: 16px;
  text-align: center;
  font-size: 22px;
  color: red;
  font-weight: bold;
}
#ipython_notebook img {
  height: 28px;
}
#site {
  width: 100%;
  display: none;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  overflow: auto;
}
@media print {
  #site {
    height: auto !important;
  }
}
/* Smaller buttons */
.ui-button .ui-button-text {
  padding: 0.2em 0.8em;
  font-size: 77%;
}
input.ui-button {
  padding: 0.3em 0.9em;
}
span#kernel_logo_widget {
  margin: 0 10px;
}
span#login_widget {
  float: right;
}
[dir="rtl"] span#login_widget {
  float: left;
}
span#login_widget > .button,
#logout {
  color: #333;
  background-color: #fff;
  border-color: #ccc;
}
span#login_widget > .button:focus,
#logout:focus,
span#login_widget > .button.focus,
#logout.focus {
  color: #333;
  background-color: #e6e6e6;
  border-color: #8c8c8c;
}
span#login_widget > .button:hover,
#logout:hover {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
span#login_widget > .button:active,
#logout:active,
span#login_widget > .button.active,
#logout.active,
.open > .dropdown-togglespan#login_widget > .button,
.open > .dropdown-toggle#logout {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
span#login_widget > .button:active:hover,
#logout:active:hover,
span#login_widget > .button.active:hover,
#logout.active:hover,
.open > .dropdown-togglespan#login_widget > .button:hover,
.open > .dropdown-toggle#logout:hover,
span#login_widget > .button:active:focus,
#logout:active:focus,
span#login_widget > .button.active:focus,
#logout.active:focus,
.open > .dropdown-togglespan#login_widget > .button:focus,
.open > .dropdown-toggle#logout:focus,
span#login_widget > .button:active.focus,
#logout:active.focus,
span#login_widget > .button.active.focus,
#logout.active.focus,
.open > .dropdown-togglespan#login_widget > .button.focus,
.open > .dropdown-toggle#logout.focus {
  color: #333;
  background-color: #d4d4d4;
  border-color: #8c8c8c;
}
span#login_widget > .button:active,
#logout:active,
span#login_widget > .button.active,
#logout.active,
.open > .dropdown-togglespan#login_widget > .button,
.open > .dropdown-toggle#logout {
  background-image: none;
}
span#login_widget > .button.disabled:hover,
#logout.disabled:hover,
span#login_widget > .button[disabled]:hover,
#logout[disabled]:hover,
fieldset[disabled] span#login_widget > .button:hover,
fieldset[disabled] #logout:hover,
span#login_widget > .button.disabled:focus,
#logout.disabled:focus,
span#login_widget > .button[disabled]:focus,
#logout[disabled]:focus,
fieldset[disabled] span#login_widget > .button:focus,
fieldset[disabled] #logout:focus,
span#login_widget > .button.disabled.focus,
#logout.disabled.focus,
span#login_widget > .button[disabled].focus,
#logout[disabled].focus,
fieldset[disabled] span#login_widget > .button.focus,
fieldset[disabled] #logout.focus {
  background-color: #fff;
  border-color: #ccc;
}
span#login_widget > .button .badge,
#logout .badge {
  color: #fff;
  background-color: #333;
}
.nav-header {
  text-transform: none;
}
#header > span {
  margin-top: 10px;
}
.modal_stretch .modal-dialog {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
  min-height: 80vh;
}
.modal_stretch .modal-dialog .modal-body {
  max-height: calc(100vh - 200px);
  overflow: auto;
  flex: 1;
}
.modal-header {
  cursor: move;
}
@media (min-width: 768px) {
  .modal .modal-dialog {
    width: 700px;
  }
}
@media (min-width: 768px) {
  select.form-control {
    margin-left: 12px;
    margin-right: 12px;
  }
}
/*!
*
* IPython auth
*
*/
.center-nav {
  display: inline-block;
  margin-bottom: -4px;
}
[dir="rtl"] .center-nav form.pull-left {
  float: right !important;
  float: right;
}
[dir="rtl"] .center-nav .navbar-text {
  float: right;
}
[dir="rtl"] .navbar-inner {
  text-align: right;
}
[dir="rtl"] div.text-left {
  text-align: right;
}
/*!
*
* IPython tree view
*
*/
/* We need an invisible input field on top of the sentense*/
/* "Drag file onto the list ..." */
.alternate_upload {
  background-color: none;
  display: inline;
}
.alternate_upload.form {
  padding: 0;
  margin: 0;
}
.alternate_upload input.fileinput {
  position: absolute;
  display: block;
  width: 100%;
  height: 100%;
  overflow: hidden;
  cursor: pointer;
  opacity: 0;
  z-index: 2;
}
.alternate_upload .btn-xs > input.fileinput {
  margin: -1px -5px;
}
.alternate_upload .btn-upload {
  position: relative;
  height: 22px;
}
::-webkit-file-upload-button {
  cursor: pointer;
}
/**
 * Primary styles
 *
 * Author: Jupyter Development Team
 */
ul#tabs {
  margin-bottom: 4px;
}
ul#tabs a {
  padding-top: 6px;
  padding-bottom: 4px;
}
[dir="rtl"] ul#tabs.nav-tabs > li {
  float: right;
}
[dir="rtl"] ul#tabs.nav.nav-tabs {
  padding-right: 0;
}
ul.breadcrumb a:focus,
ul.breadcrumb a:hover {
  text-decoration: none;
}
ul.breadcrumb i.icon-home {
  font-size: 16px;
  margin-right: 4px;
}
ul.breadcrumb span {
  color: #5e5e5e;
}
.list_toolbar {
  padding: 4px 0 4px 0;
  vertical-align: middle;
}
.list_toolbar .tree-buttons {
  padding-top: 1px;
}
[dir="rtl"] .list_toolbar .tree-buttons .pull-right {
  float: left !important;
  float: left;
}
[dir="rtl"] .list_toolbar .col-sm-4,
[dir="rtl"] .list_toolbar .col-sm-8 {
  float: right;
}
.dynamic-buttons {
  padding-top: 3px;
  display: inline-block;
}
.list_toolbar [class*="span"] {
  min-height: 24px;
}
.list_header {
  font-weight: bold;
  background-color: #EEE;
}
.list_placeholder {
  font-weight: bold;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 7px;
  padding-right: 7px;
}
.list_container {
  margin-top: 4px;
  margin-bottom: 20px;
  border: 1px solid #ddd;
  border-radius: 2px;
}
.list_container > div {
  border-bottom: 1px solid #ddd;
}
.list_container > div:hover .list-item {
  background-color: red;
}
.list_container > div:last-child {
  border: none;
}
.list_item:hover .list_item {
  background-color: #ddd;
}
.list_item a {
  text-decoration: none;
}
.list_item:hover {
  background-color: #fafafa;
}
.list_header > div,
.list_item > div {
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 7px;
  padding-right: 7px;
  line-height: 22px;
}
.list_header > div input,
.list_item > div input {
  margin-right: 7px;
  margin-left: 14px;
  vertical-align: text-bottom;
  line-height: 22px;
  position: relative;
  top: -1px;
}
.list_header > div .item_link,
.list_item > div .item_link {
  margin-left: -1px;
  vertical-align: baseline;
  line-height: 22px;
}
[dir="rtl"] .list_item > div input {
  margin-right: 0;
}
.new-file input[type=checkbox] {
  visibility: hidden;
}
.item_name {
  line-height: 22px;
  height: 24px;
}
.item_icon {
  font-size: 14px;
  color: #5e5e5e;
  margin-right: 7px;
  margin-left: 7px;
  line-height: 22px;
  vertical-align: baseline;
}
.item_modified {
  margin-right: 7px;
  margin-left: 7px;
}
[dir="rtl"] .item_modified.pull-right {
  float: left !important;
  float: left;
}
.item_buttons {
  line-height: 1em;
  margin-left: -5px;
}
.item_buttons .btn,
.item_buttons .btn-group,
.item_buttons .input-group {
  float: left;
}
.item_buttons > .btn,
.item_buttons > .btn-group,
.item_buttons > .input-group {
  margin-left: 5px;
}
.item_buttons .btn {
  min-width: 13ex;
}
.item_buttons .running-indicator {
  padding-top: 4px;
  color: #5cb85c;
}
.item_buttons .kernel-name {
  padding-top: 4px;
  color: #5bc0de;
  margin-right: 7px;
  float: left;
}
[dir="rtl"] .item_buttons.pull-right {
  float: left !important;
  float: left;
}
[dir="rtl"] .item_buttons .kernel-name {
  margin-left: 7px;
  float: right;
}
.toolbar_info {
  height: 24px;
  line-height: 24px;
}
.list_item input:not([type=checkbox]) {
  padding-top: 3px;
  padding-bottom: 3px;
  height: 22px;
  line-height: 14px;
  margin: 0px;
}
.highlight_text {
  color: blue;
}
#project_name {
  display: inline-block;
  padding-left: 7px;
  margin-left: -2px;
}
#project_name > .breadcrumb {
  padding: 0px;
  margin-bottom: 0px;
  background-color: transparent;
  font-weight: bold;
}
.sort_button {
  display: inline-block;
  padding-left: 7px;
}
[dir="rtl"] .sort_button.pull-right {
  float: left !important;
  float: left;
}
#tree-selector {
  padding-right: 0px;
}
#button-select-all {
  min-width: 50px;
}
[dir="rtl"] #button-select-all.btn {
  float: right ;
}
#select-all {
  margin-left: 7px;
  margin-right: 2px;
  margin-top: 2px;
  height: 16px;
}
[dir="rtl"] #select-all.pull-left {
  float: right !important;
  float: right;
}
.menu_icon {
  margin-right: 2px;
}
.tab-content .row {
  margin-left: 0px;
  margin-right: 0px;
}
.folder_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f114";
}
.folder_icon:before.fa-pull-left {
  margin-right: .3em;
}
.folder_icon:before.fa-pull-right {
  margin-left: .3em;
}
.folder_icon:before.pull-left {
  margin-right: .3em;
}
.folder_icon:before.pull-right {
  margin-left: .3em;
}
.notebook_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f02d";
  position: relative;
  top: -1px;
}
.notebook_icon:before.fa-pull-left {
  margin-right: .3em;
}
.notebook_icon:before.fa-pull-right {
  margin-left: .3em;
}
.notebook_icon:before.pull-left {
  margin-right: .3em;
}
.notebook_icon:before.pull-right {
  margin-left: .3em;
}
.running_notebook_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f02d";
  position: relative;
  top: -1px;
  color: #5cb85c;
}
.running_notebook_icon:before.fa-pull-left {
  margin-right: .3em;
}
.running_notebook_icon:before.fa-pull-right {
  margin-left: .3em;
}
.running_notebook_icon:before.pull-left {
  margin-right: .3em;
}
.running_notebook_icon:before.pull-right {
  margin-left: .3em;
}
.file_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f016";
  position: relative;
  top: -2px;
}
.file_icon:before.fa-pull-left {
  margin-right: .3em;
}
.file_icon:before.fa-pull-right {
  margin-left: .3em;
}
.file_icon:before.pull-left {
  margin-right: .3em;
}
.file_icon:before.pull-right {
  margin-left: .3em;
}
#notebook_toolbar .pull-right {
  padding-top: 0px;
  margin-right: -1px;
}
ul#new-menu {
  left: auto;
  right: 0;
}
#new-menu .dropdown-header {
  font-size: 10px;
  border-bottom: 1px solid #e5e5e5;
  padding: 0 0 3px;
  margin: -3px 20px 0;
}
.kernel-menu-icon {
  padding-right: 12px;
  width: 24px;
  content: "\f096";
}
.kernel-menu-icon:before {
  content: "\f096";
}
.kernel-menu-icon-current:before {
  content: "\f00c";
}
#tab_content {
  padding-top: 20px;
}
#running .panel-group .panel {
  margin-top: 3px;
  margin-bottom: 1em;
}
#running .panel-group .panel .panel-heading {
  background-color: #EEE;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 7px;
  padding-right: 7px;
  line-height: 22px;
}
#running .panel-group .panel .panel-heading a:focus,
#running .panel-group .panel .panel-heading a:hover {
  text-decoration: none;
}
#running .panel-group .panel .panel-body {
  padding: 0px;
}
#running .panel-group .panel .panel-body .list_container {
  margin-top: 0px;
  margin-bottom: 0px;
  border: 0px;
  border-radius: 0px;
}
#running .panel-group .panel .panel-body .list_container .list_item {
  border-bottom: 1px solid #ddd;
}
#running .panel-group .panel .panel-body .list_container .list_item:last-child {
  border-bottom: 0px;
}
.delete-button {
  display: none;
}
.duplicate-button {
  display: none;
}
.rename-button {
  display: none;
}
.move-button {
  display: none;
}
.download-button {
  display: none;
}
.shutdown-button {
  display: none;
}
.dynamic-instructions {
  display: inline-block;
  padding-top: 4px;
}
/*!
*
* IPython text editor webapp
*
*/
.selected-keymap i.fa {
  padding: 0px 5px;
}
.selected-keymap i.fa:before {
  content: "\f00c";
}
#mode-menu {
  overflow: auto;
  max-height: 20em;
}
.edit_app #header {
  -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
}
.edit_app #menubar .navbar {
  /* Use a negative 1 bottom margin, so the border overlaps the border of the
    header */
  margin-bottom: -1px;
}
.dirty-indicator {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  width: 20px;
}
.dirty-indicator.fa-pull-left {
  margin-right: .3em;
}
.dirty-indicator.fa-pull-right {
  margin-left: .3em;
}
.dirty-indicator.pull-left {
  margin-right: .3em;
}
.dirty-indicator.pull-right {
  margin-left: .3em;
}
.dirty-indicator-dirty {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  width: 20px;
}
.dirty-indicator-dirty.fa-pull-left {
  margin-right: .3em;
}
.dirty-indicator-dirty.fa-pull-right {
  margin-left: .3em;
}
.dirty-indicator-dirty.pull-left {
  margin-right: .3em;
}
.dirty-indicator-dirty.pull-right {
  margin-left: .3em;
}
.dirty-indicator-clean {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  width: 20px;
}
.dirty-indicator-clean.fa-pull-left {
  margin-right: .3em;
}
.dirty-indicator-clean.fa-pull-right {
  margin-left: .3em;
}
.dirty-indicator-clean.pull-left {
  margin-right: .3em;
}
.dirty-indicator-clean.pull-right {
  margin-left: .3em;
}
.dirty-indicator-clean:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f00c";
}
.dirty-indicator-clean:before.fa-pull-left {
  margin-right: .3em;
}
.dirty-indicator-clean:before.fa-pull-right {
  margin-left: .3em;
}
.dirty-indicator-clean:before.pull-left {
  margin-right: .3em;
}
.dirty-indicator-clean:before.pull-right {
  margin-left: .3em;
}
#filename {
  font-size: 16pt;
  display: table;
  padding: 0px 5px;
}
#current-mode {
  padding-left: 5px;
  padding-right: 5px;
}
#texteditor-backdrop {
  padding-top: 20px;
  padding-bottom: 20px;
}
@media not print {
  #texteditor-backdrop {
    background-color: #EEE;
  }
}
@media print {
  #texteditor-backdrop #texteditor-container .CodeMirror-gutter,
  #texteditor-backdrop #texteditor-container .CodeMirror-gutters {
    background-color: #fff;
  }
}
@media not print {
  #texteditor-backdrop #texteditor-container .CodeMirror-gutter,
  #texteditor-backdrop #texteditor-container .CodeMirror-gutters {
    background-color: #fff;
  }
}
@media not print {
  #texteditor-backdrop #texteditor-container {
    padding: 0px;
    background-color: #fff;
    -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
    box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  }
}
.CodeMirror-dialog {
  background-color: #fff;
}
/*!
*
* IPython notebook
*
*/
/* CSS font colors for translated ANSI escape sequences */
/* The color values are a mix of
   http://www.xcolors.net/dl/baskerville-ivorylight and
   http://www.xcolors.net/dl/euphrasia */
.ansi-black-fg {
  color: #3E424D;
}
.ansi-black-bg {
  background-color: #3E424D;
}
.ansi-black-intense-fg {
  color: #282C36;
}
.ansi-black-intense-bg {
  background-color: #282C36;
}
.ansi-red-fg {
  color: #E75C58;
}
.ansi-red-bg {
  background-color: #E75C58;
}
.ansi-red-intense-fg {
  color: #B22B31;
}
.ansi-red-intense-bg {
  background-color: #B22B31;
}
.ansi-green-fg {
  color: #00A250;
}
.ansi-green-bg {
  background-color: #00A250;
}
.ansi-green-intense-fg {
  color: #007427;
}
.ansi-green-intense-bg {
  background-color: #007427;
}
.ansi-yellow-fg {
  color: #DDB62B;
}
.ansi-yellow-bg {
  background-color: #DDB62B;
}
.ansi-yellow-intense-fg {
  color: #B27D12;
}
.ansi-yellow-intense-bg {
  background-color: #B27D12;
}
.ansi-blue-fg {
  color: #208FFB;
}
.ansi-blue-bg {
  background-color: #208FFB;
}
.ansi-blue-intense-fg {
  color: #0065CA;
}
.ansi-blue-intense-bg {
  background-color: #0065CA;
}
.ansi-magenta-fg {
  color: #D160C4;
}
.ansi-magenta-bg {
  background-color: #D160C4;
}
.ansi-magenta-intense-fg {
  color: #A03196;
}
.ansi-magenta-intense-bg {
  background-color: #A03196;
}
.ansi-cyan-fg {
  color: #60C6C8;
}
.ansi-cyan-bg {
  background-color: #60C6C8;
}
.ansi-cyan-intense-fg {
  color: #258F8F;
}
.ansi-cyan-intense-bg {
  background-color: #258F8F;
}
.ansi-white-fg {
  color: #C5C1B4;
}
.ansi-white-bg {
  background-color: #C5C1B4;
}
.ansi-white-intense-fg {
  color: #A1A6B2;
}
.ansi-white-intense-bg {
  background-color: #A1A6B2;
}
.ansi-default-inverse-fg {
  color: #FFFFFF;
}
.ansi-default-inverse-bg {
  background-color: #000000;
}
.ansi-bold {
  font-weight: bold;
}
.ansi-underline {
  text-decoration: underline;
}
/* The following styles are deprecated an will be removed in a future version */
.ansibold {
  font-weight: bold;
}
.ansi-inverse {
  outline: 0.5px dotted;
}
/* use dark versions for foreground, to improve visibility */
.ansiblack {
  color: black;
}
.ansired {
  color: darkred;
}
.ansigreen {
  color: darkgreen;
}
.ansiyellow {
  color: #c4a000;
}
.ansiblue {
  color: darkblue;
}
.ansipurple {
  color: darkviolet;
}
.ansicyan {
  color: steelblue;
}
.ansigray {
  color: gray;
}
/* and light for background, for the same reason */
.ansibgblack {
  background-color: black;
}
.ansibgred {
  background-color: red;
}
.ansibggreen {
  background-color: green;
}
.ansibgyellow {
  background-color: yellow;
}
.ansibgblue {
  background-color: blue;
}
.ansibgpurple {
  background-color: magenta;
}
.ansibgcyan {
  background-color: cyan;
}
.ansibggray {
  background-color: gray;
}
div.cell {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
  border-radius: 2px;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  border-width: 1px;
  border-style: solid;
  border-color: transparent;
  width: 100%;
  padding: 5px;
  /* This acts as a spacer between cells, that is outside the border */
  margin: 0px;
  outline: none;
  position: relative;
  overflow: visible;
}
div.cell:before {
  position: absolute;
  display: block;
  top: -1px;
  left: -1px;
  width: 5px;
  height: calc(100% +  2px);
  content: '';
  background: transparent;
}
div.cell.jupyter-soft-selected {
  border-left-color: #E3F2FD;
  border-left-width: 1px;
  padding-left: 5px;
  border-right-color: #E3F2FD;
  border-right-width: 1px;
  background: #E3F2FD;
}
@media print {
  div.cell.jupyter-soft-selected {
    border-color: transparent;
  }
}
div.cell.selected,
div.cell.selected.jupyter-soft-selected {
  border-color: #ababab;
}
div.cell.selected:before,
div.cell.selected.jupyter-soft-selected:before {
  position: absolute;
  display: block;
  top: -1px;
  left: -1px;
  width: 5px;
  height: calc(100% +  2px);
  content: '';
  background: #42A5F5;
}
@media print {
  div.cell.selected,
  div.cell.selected.jupyter-soft-selected {
    border-color: transparent;
  }
}
.edit_mode div.cell.selected {
  border-color: #66BB6A;
}
.edit_mode div.cell.selected:before {
  position: absolute;
  display: block;
  top: -1px;
  left: -1px;
  width: 5px;
  height: calc(100% +  2px);
  content: '';
  background: #66BB6A;
}
@media print {
  .edit_mode div.cell.selected {
    border-color: transparent;
  }
}
.prompt {
  /* This needs to be wide enough for 3 digit prompt numbers: In[100]: */
  min-width: 14ex;
  /* This padding is tuned to match the padding on the CodeMirror editor. */
  padding: 0.4em;
  margin: 0px;
  font-family: monospace;
  text-align: right;
  /* This has to match that of the the CodeMirror class line-height below */
  line-height: 1.21429em;
  /* Don't highlight prompt number selection */
  -webkit-touch-callout: none;
  -webkit-user-select: none;
  -khtml-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
  /* Use default cursor */
  cursor: default;
}
@media (max-width: 540px) {
  .prompt {
    text-align: left;
  }
}
div.inner_cell {
  min-width: 0;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
  /* Old browsers */
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  box-flex: 1;
  /* Modern browsers */
  flex: 1;
}
/* input_area and input_prompt must match in top border and margin for alignment */
div.input_area {
  border: 1px solid #cfcfcf;
  border-radius: 2px;
  background: #f7f7f7;
  line-height: 1.21429em;
}
/* This is needed so that empty prompt areas can collapse to zero height when there
   is no content in the output_subarea and the prompt. The main purpose of this is
   to make sure that empty JavaScript output_subareas have no height. */
div.prompt:empty {
  padding-top: 0;
  padding-bottom: 0;
}
div.unrecognized_cell {
  padding: 5px 5px 5px 0px;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
}
div.unrecognized_cell .inner_cell {
  border-radius: 2px;
  padding: 5px;
  font-weight: bold;
  color: red;
  border: 1px solid #cfcfcf;
  background: #eaeaea;
}
div.unrecognized_cell .inner_cell a {
  color: inherit;
  text-decoration: none;
}
div.unrecognized_cell .inner_cell a:hover {
  color: inherit;
  text-decoration: none;
}
@media (max-width: 540px) {
  div.unrecognized_cell > div.prompt {
    display: none;
  }
}
div.code_cell {
  /* avoid page breaking on code cells when printing */
}
@media print {
  div.code_cell {
    page-break-inside: avoid;
  }
}
/* any special styling for code cells that are currently running goes here */
div.input {
  page-break-inside: avoid;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
}
@media (max-width: 540px) {
  div.input {
    /* Old browsers */
    display: -webkit-box;
    -webkit-box-orient: vertical;
    -webkit-box-align: stretch;
    display: -moz-box;
    -moz-box-orient: vertical;
    -moz-box-align: stretch;
    display: box;
    box-orient: vertical;
    box-align: stretch;
    /* Modern browsers */
    display: flex;
    flex-direction: column;
    align-items: stretch;
  }
}
/* input_area and input_prompt must match in top border and margin for alignment */
div.input_prompt {
  color: #303F9F;
  border-top: 1px solid transparent;
}
div.input_area > div.highlight {
  margin: 0.4em;
  border: none;
  padding: 0px;
  background-color: transparent;
}
div.input_area > div.highlight > pre {
  margin: 0px;
  border: none;
  padding: 0px;
  background-color: transparent;
}
/* The following gets added to the <head> if it is detected that the user has a
 * monospace font with inconsistent normal/bold/italic height.  See
 * notebookmain.js.  Such fonts will have keywords vertically offset with
 * respect to the rest of the text.  The user should select a better font.
 * See: https://github.com/ipython/ipython/issues/1503
 *
 * .CodeMirror span {
 *      vertical-align: bottom;
 * }
 */
.CodeMirror {
  line-height: 1.21429em;
  /* Changed from 1em to our global default */
  font-size: 14px;
  height: auto;
  /* Changed to auto to autogrow */
  background: none;
  /* Changed from white to allow our bg to show through */
}
.CodeMirror-scroll {
  /*  The CodeMirror docs are a bit fuzzy on if overflow-y should be hidden or visible.*/
  /*  We have found that if it is visible, vertical scrollbars appear with font size changes.*/
  overflow-y: hidden;
  overflow-x: auto;
}
.CodeMirror-lines {
  /* In CM2, this used to be 0.4em, but in CM3 it went to 4px. We need the em value because */
  /* we have set a different line-height and want this to scale with that. */
  /* Note that this should set vertical padding only, since CodeMirror assumes
       that horizontal padding will be set on CodeMirror pre */
  padding: 0.4em 0;
}
.CodeMirror-linenumber {
  padding: 0 8px 0 4px;
}
.CodeMirror-gutters {
  border-bottom-left-radius: 2px;
  border-top-left-radius: 2px;
}
.CodeMirror pre {
  /* In CM3 this went to 4px from 0 in CM2. This sets horizontal padding only,
    use .CodeMirror-lines for vertical */
  padding: 0 0.4em;
  border: 0;
  border-radius: 0;
}
.CodeMirror-cursor {
  border-left: 1.4px solid black;
}
@media screen and (min-width: 2138px) and (max-width: 4319px) {
  .CodeMirror-cursor {
    border-left: 2px solid black;
  }
}
@media screen and (min-width: 4320px) {
  .CodeMirror-cursor {
    border-left: 4px solid black;
  }
}
/*

Original style from softwaremaniacs.org (c) Ivan Sagalaev <Maniac@SoftwareManiacs.Org>
Adapted from GitHub theme

*/
.highlight-base {
  color: #000;
}
.highlight-variable {
  color: #000;
}
.highlight-variable-2 {
  color: #1a1a1a;
}
.highlight-variable-3 {
  color: #333333;
}
.highlight-string {
  color: #BA2121;
}
.highlight-comment {
  color: #408080;
  font-style: italic;
}
.highlight-number {
  color: #080;
}
.highlight-atom {
  color: #88F;
}
.highlight-keyword {
  color: #008000;
  font-weight: bold;
}
.highlight-builtin {
  color: #008000;
}
.highlight-error {
  color: #f00;
}
.highlight-operator {
  color: #AA22FF;
  font-weight: bold;
}
.highlight-meta {
  color: #AA22FF;
}
/* previously not defined, copying from default codemirror */
.highlight-def {
  color: #00f;
}
.highlight-string-2 {
  color: #f50;
}
.highlight-qualifier {
  color: #555;
}
.highlight-bracket {
  color: #997;
}
.highlight-tag {
  color: #170;
}
.highlight-attribute {
  color: #00c;
}
.highlight-header {
  color: blue;
}
.highlight-quote {
  color: #090;
}
.highlight-link {
  color: #00c;
}
/* apply the same style to codemirror */
.cm-s-ipython span.cm-keyword {
  color: #008000;
  font-weight: bold;
}
.cm-s-ipython span.cm-atom {
  color: #88F;
}
.cm-s-ipython span.cm-number {
  color: #080;
}
.cm-s-ipython span.cm-def {
  color: #00f;
}
.cm-s-ipython span.cm-variable {
  color: #000;
}
.cm-s-ipython span.cm-operator {
  color: #AA22FF;
  font-weight: bold;
}
.cm-s-ipython span.cm-variable-2 {
  color: #1a1a1a;
}
.cm-s-ipython span.cm-variable-3 {
  color: #333333;
}
.cm-s-ipython span.cm-comment {
  color: #408080;
  font-style: italic;
}
.cm-s-ipython span.cm-string {
  color: #BA2121;
}
.cm-s-ipython span.cm-string-2 {
  color: #f50;
}
.cm-s-ipython span.cm-meta {
  color: #AA22FF;
}
.cm-s-ipython span.cm-qualifier {
  color: #555;
}
.cm-s-ipython span.cm-builtin {
  color: #008000;
}
.cm-s-ipython span.cm-bracket {
  color: #997;
}
.cm-s-ipython span.cm-tag {
  color: #170;
}
.cm-s-ipython span.cm-attribute {
  color: #00c;
}
.cm-s-ipython span.cm-header {
  color: blue;
}
.cm-s-ipython span.cm-quote {
  color: #090;
}
.cm-s-ipython span.cm-link {
  color: #00c;
}
.cm-s-ipython span.cm-error {
  color: #f00;
}
.cm-s-ipython span.cm-tab {
  background: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADAAAAAMCAYAAAAkuj5RAAAAAXNSR0IArs4c6QAAAGFJREFUSMft1LsRQFAQheHPowAKoACx3IgEKtaEHujDjORSgWTH/ZOdnZOcM/sgk/kFFWY0qV8foQwS4MKBCS3qR6ixBJvElOobYAtivseIE120FaowJPN75GMu8j/LfMwNjh4HUpwg4LUAAAAASUVORK5CYII=);
  background-position: right;
  background-repeat: no-repeat;
}
div.output_wrapper {
  /* this position must be relative to enable descendents to be absolute within it */
  position: relative;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
  z-index: 1;
}
/* class for the output area when it should be height-limited */
div.output_scroll {
  /* ideally, this would be max-height, but FF barfs all over that */
  height: 24em;
  /* FF needs this *and the wrapper* to specify full width, or it will shrinkwrap */
  width: 100%;
  overflow: auto;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 2px 8px rgba(0, 0, 0, 0.8);
  box-shadow: inset 0 2px 8px rgba(0, 0, 0, 0.8);
  display: block;
}
/* output div while it is collapsed */
div.output_collapsed {
  margin: 0px;
  padding: 0px;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
}
div.out_prompt_overlay {
  height: 100%;
  padding: 0px 0.4em;
  position: absolute;
  border-radius: 2px;
}
div.out_prompt_overlay:hover {
  /* use inner shadow to get border that is computed the same on WebKit/FF */
  -webkit-box-shadow: inset 0 0 1px #000;
  box-shadow: inset 0 0 1px #000;
  background: rgba(240, 240, 240, 0.5);
}
div.output_prompt {
  color: #D84315;
}
/* This class is the outer container of all output sections. */
div.output_area {
  padding: 0px;
  page-break-inside: avoid;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
}
div.output_area .MathJax_Display {
  text-align: left !important;
}
div.output_area .rendered_html table {
  margin-left: 0;
  margin-right: 0;
}
div.output_area .rendered_html img {
  margin-left: 0;
  margin-right: 0;
}
div.output_area img,
div.output_area svg {
  max-width: 100%;
  height: auto;
}
div.output_area img.unconfined,
div.output_area svg.unconfined {
  max-width: none;
}
div.output_area .mglyph > img {
  max-width: none;
}
/* This is needed to protect the pre formating from global settings such
   as that of bootstrap */
.output {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
}
@media (max-width: 540px) {
  div.output_area {
    /* Old browsers */
    display: -webkit-box;
    -webkit-box-orient: vertical;
    -webkit-box-align: stretch;
    display: -moz-box;
    -moz-box-orient: vertical;
    -moz-box-align: stretch;
    display: box;
    box-orient: vertical;
    box-align: stretch;
    /* Modern browsers */
    display: flex;
    flex-direction: column;
    align-items: stretch;
  }
}
div.output_area pre {
  margin: 0;
  padding: 1px 0 1px 0;
  border: 0;
  vertical-align: baseline;
  color: black;
  background-color: transparent;
  border-radius: 0;
}
/* This class is for the output subarea inside the output_area and after
   the prompt div. */
div.output_subarea {
  overflow-x: auto;
  padding: 0.4em;
  /* Old browsers */
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  box-flex: 1;
  /* Modern browsers */
  flex: 1;
  max-width: calc(100% - 14ex);
}
div.output_scroll div.output_subarea {
  overflow-x: visible;
}
/* The rest of the output_* classes are for special styling of the different
   output types */
/* all text output has this class: */
div.output_text {
  text-align: left;
  color: #000;
  /* This has to match that of the the CodeMirror class line-height below */
  line-height: 1.21429em;
}
/* stdout/stderr are 'text' as well as 'stream', but execute_result/error are *not* streams */
div.output_stderr {
  background: #fdd;
  /* very light red background for stderr */
}
div.output_latex {
  text-align: left;
}
/* Empty output_javascript divs should have no height */
div.output_javascript:empty {
  padding: 0;
}
.js-error {
  color: darkred;
}
/* raw_input styles */
div.raw_input_container {
  line-height: 1.21429em;
  padding-top: 5px;
}
pre.raw_input_prompt {
  /* nothing needed here. */
}
input.raw_input {
  font-family: monospace;
  font-size: inherit;
  color: inherit;
  width: auto;
  /* make sure input baseline aligns with prompt */
  vertical-align: baseline;
  /* padding + margin = 0.5em between prompt and cursor */
  padding: 0em 0.25em;
  margin: 0em 0.25em;
}
input.raw_input:focus {
  box-shadow: none;
}
p.p-space {
  margin-bottom: 10px;
}
div.output_unrecognized {
  padding: 5px;
  font-weight: bold;
  color: red;
}
div.output_unrecognized a {
  color: inherit;
  text-decoration: none;
}
div.output_unrecognized a:hover {
  color: inherit;
  text-decoration: none;
}
.rendered_html {
  color: #000;
  /* any extras will just be numbers: */
}
.rendered_html em {
  font-style: italic;
}
.rendered_html strong {
  font-weight: bold;
}
.rendered_html u {
  text-decoration: underline;
}
.rendered_html :link {
  text-decoration: underline;
}
.rendered_html :visited {
  text-decoration: underline;
}
.rendered_html h1 {
  font-size: 185.7%;
  margin: 1.08em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
}
.rendered_html h2 {
  font-size: 157.1%;
  margin: 1.27em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
}
.rendered_html h3 {
  font-size: 128.6%;
  margin: 1.55em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
}
.rendered_html h4 {
  font-size: 100%;
  margin: 2em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
}
.rendered_html h5 {
  font-size: 100%;
  margin: 2em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
  font-style: italic;
}
.rendered_html h6 {
  font-size: 100%;
  margin: 2em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
  font-style: italic;
}
.rendered_html h1:first-child {
  margin-top: 0.538em;
}
.rendered_html h2:first-child {
  margin-top: 0.636em;
}
.rendered_html h3:first-child {
  margin-top: 0.777em;
}
.rendered_html h4:first-child {
  margin-top: 1em;
}
.rendered_html h5:first-child {
  margin-top: 1em;
}
.rendered_html h6:first-child {
  margin-top: 1em;
}
.rendered_html ul:not(.list-inline),
.rendered_html ol:not(.list-inline) {
  padding-left: 2em;
}
.rendered_html ul {
  list-style: disc;
}
.rendered_html ul ul {
  list-style: square;
  margin-top: 0;
}
.rendered_html ul ul ul {
  list-style: circle;
}
.rendered_html ol {
  list-style: decimal;
}
.rendered_html ol ol {
  list-style: upper-alpha;
  margin-top: 0;
}
.rendered_html ol ol ol {
  list-style: lower-alpha;
}
.rendered_html ol ol ol ol {
  list-style: lower-roman;
}
.rendered_html ol ol ol ol ol {
  list-style: decimal;
}
.rendered_html * + ul {
  margin-top: 1em;
}
.rendered_html * + ol {
  margin-top: 1em;
}
.rendered_html hr {
  color: black;
  background-color: black;
}
.rendered_html pre {
  margin: 1em 2em;
  padding: 0px;
  background-color: #fff;
}
.rendered_html code {
  background-color: #eff0f1;
}
.rendered_html p code {
  padding: 1px 5px;
}
.rendered_html pre code {
  background-color: #fff;
}
.rendered_html pre,
.rendered_html code {
  border: 0;
  color: #000;
  font-size: 100%;
}
.rendered_html blockquote {
  margin: 1em 2em;
}
.rendered_html table {
  margin-left: auto;
  margin-right: auto;
  border: none;
  border-collapse: collapse;
  border-spacing: 0;
  color: black;
  font-size: 12px;
  table-layout: fixed;
}
.rendered_html thead {
  border-bottom: 1px solid black;
  vertical-align: bottom;
}
.rendered_html tr,
.rendered_html th,
.rendered_html td {
  text-align: right;
  vertical-align: middle;
  padding: 0.5em 0.5em;
  line-height: normal;
  white-space: normal;
  max-width: none;
  border: none;
}
.rendered_html th {
  font-weight: bold;
}
.rendered_html tbody tr:nth-child(odd) {
  background: #f5f5f5;
}
.rendered_html tbody tr:hover {
  background: rgba(66, 165, 245, 0.2);
}
.rendered_html * + table {
  margin-top: 1em;
}
.rendered_html p {
  text-align: left;
}
.rendered_html * + p {
  margin-top: 1em;
}
.rendered_html img {
  display: block;
  margin-left: auto;
  margin-right: auto;
}
.rendered_html * + img {
  margin-top: 1em;
}
.rendered_html img,
.rendered_html svg {
  max-width: 100%;
  height: auto;
}
.rendered_html img.unconfined,
.rendered_html svg.unconfined {
  max-width: none;
}
.rendered_html .alert {
  margin-bottom: initial;
}
.rendered_html * + .alert {
  margin-top: 1em;
}
[dir="rtl"] .rendered_html p {
  text-align: right;
}
div.text_cell {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
}
@media (max-width: 540px) {
  div.text_cell > div.prompt {
    display: none;
  }
}
div.text_cell_render {
  /*font-family: "Helvetica Neue", Arial, Helvetica, Geneva, sans-serif;*/
  outline: none;
  resize: none;
  width: inherit;
  border-style: none;
  padding: 0.5em 0.5em 0.5em 0.4em;
  color: #000;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
}
a.anchor-link:link {
  text-decoration: none;
  padding: 0px 20px;
  visibility: hidden;
}
h1:hover .anchor-link,
h2:hover .anchor-link,
h3:hover .anchor-link,
h4:hover .anchor-link,
h5:hover .anchor-link,
h6:hover .anchor-link {
  visibility: visible;
}
.text_cell.rendered .input_area {
  display: none;
}
.text_cell.rendered .rendered_html {
  overflow-x: auto;
  overflow-y: hidden;
}
.text_cell.rendered .rendered_html tr,
.text_cell.rendered .rendered_html th,
.text_cell.rendered .rendered_html td {
  max-width: none;
}
.text_cell.unrendered .text_cell_render {
  display: none;
}
.text_cell .dropzone .input_area {
  border: 2px dashed #bababa;
  margin: -1px;
}
.cm-header-1,
.cm-header-2,
.cm-header-3,
.cm-header-4,
.cm-header-5,
.cm-header-6 {
  font-weight: bold;
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
}
.cm-header-1 {
  font-size: 185.7%;
}
.cm-header-2 {
  font-size: 157.1%;
}
.cm-header-3 {
  font-size: 128.6%;
}
.cm-header-4 {
  font-size: 110%;
}
.cm-header-5 {
  font-size: 100%;
  font-style: italic;
}
.cm-header-6 {
  font-size: 100%;
  font-style: italic;
}
/*!
*
* IPython notebook webapp
*
*/
@media (max-width: 767px) {
  .notebook_app {
    padding-left: 0px;
    padding-right: 0px;
  }
}
#ipython-main-app {
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  height: 100%;
}
div#notebook_panel {
  margin: 0px;
  padding: 0px;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  height: 100%;
}
div#notebook {
  font-size: 14px;
  line-height: 20px;
  overflow-y: hidden;
  overflow-x: auto;
  width: 100%;
  /* This spaces the page away from the edge of the notebook area */
  padding-top: 20px;
  margin: 0px;
  outline: none;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  min-height: 100%;
}
@media not print {
  #notebook-container {
    padding: 15px;
    background-color: #fff;
    min-height: 0;
    -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
    box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  }
}
@media print {
  #notebook-container {
    width: 100%;
  }
}
div.ui-widget-content {
  border: 1px solid #ababab;
  outline: none;
}
pre.dialog {
  background-color: #f7f7f7;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding: 0.4em;
  padding-left: 2em;
}
p.dialog {
  padding: 0.2em;
}
/* Word-wrap output correctly.  This is the CSS3 spelling, though Firefox seems
   to not honor it correctly.  Webkit browsers (Chrome, rekonq, Safari) do.
 */
pre,
code,
kbd,
samp {
  white-space: pre-wrap;
}
#fonttest {
  font-family: monospace;
}
p {
  margin-bottom: 0;
}
.end_space {
  min-height: 100px;
  transition: height .2s ease;
}
.notebook_app > #header {
  -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
}
@media not print {
  .notebook_app {
    background-color: #EEE;
  }
}
kbd {
  border-style: solid;
  border-width: 1px;
  box-shadow: none;
  margin: 2px;
  padding-left: 2px;
  padding-right: 2px;
  padding-top: 1px;
  padding-bottom: 1px;
}
.jupyter-keybindings {
  padding: 1px;
  line-height: 24px;
  border-bottom: 1px solid gray;
}
.jupyter-keybindings input {
  margin: 0;
  padding: 0;
  border: none;
}
.jupyter-keybindings i {
  padding: 6px;
}
.well code {
  background-color: #ffffff;
  border-color: #ababab;
  border-width: 1px;
  border-style: solid;
  padding: 2px;
  padding-top: 1px;
  padding-bottom: 1px;
}
/* CSS for the cell toolbar */
.celltoolbar {
  border: thin solid #CFCFCF;
  border-bottom: none;
  background: #EEE;
  border-radius: 2px 2px 0px 0px;
  width: 100%;
  height: 29px;
  padding-right: 4px;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
  /* Old browsers */
  -webkit-box-pack: end;
  -moz-box-pack: end;
  box-pack: end;
  /* Modern browsers */
  justify-content: flex-end;
  display: -webkit-flex;
}
@media print {
  .celltoolbar {
    display: none;
  }
}
.ctb_hideshow {
  display: none;
  vertical-align: bottom;
}
/* ctb_show is added to the ctb_hideshow div to show the cell toolbar.
   Cell toolbars are only shown when the ctb_global_show class is also set.
*/
.ctb_global_show .ctb_show.ctb_hideshow {
  display: block;
}
.ctb_global_show .ctb_show + .input_area,
.ctb_global_show .ctb_show + div.text_cell_input,
.ctb_global_show .ctb_show ~ div.text_cell_render {
  border-top-right-radius: 0px;
  border-top-left-radius: 0px;
}
.ctb_global_show .ctb_show ~ div.text_cell_render {
  border: 1px solid #cfcfcf;
}
.celltoolbar {
  font-size: 87%;
  padding-top: 3px;
}
.celltoolbar select {
  display: block;
  width: 100%;
  height: 32px;
  padding: 6px 12px;
  font-size: 13px;
  line-height: 1.42857143;
  color: #555555;
  background-color: #fff;
  background-image: none;
  border: 1px solid #ccc;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  -webkit-transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  -o-transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  height: 30px;
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
  width: inherit;
  font-size: inherit;
  height: 22px;
  padding: 0px;
  display: inline-block;
}
.celltoolbar select:focus {
  border-color: #66afe9;
  outline: 0;
  -webkit-box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, 0.6);
  box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, 0.6);
}
.celltoolbar select::-moz-placeholder {
  color: #999;
  opacity: 1;
}
.celltoolbar select:-ms-input-placeholder {
  color: #999;
}
.celltoolbar select::-webkit-input-placeholder {
  color: #999;
}
.celltoolbar select::-ms-expand {
  border: 0;
  background-color: transparent;
}
.celltoolbar select[disabled],
.celltoolbar select[readonly],
fieldset[disabled] .celltoolbar select {
  background-color: #eeeeee;
  opacity: 1;
}
.celltoolbar select[disabled],
fieldset[disabled] .celltoolbar select {
  cursor: not-allowed;
}
textarea.celltoolbar select {
  height: auto;
}
select.celltoolbar select {
  height: 30px;
  line-height: 30px;
}
textarea.celltoolbar select,
select[multiple].celltoolbar select {
  height: auto;
}
.celltoolbar label {
  margin-left: 5px;
  margin-right: 5px;
}
.tags_button_container {
  width: 100%;
  display: flex;
}
.tag-container {
  display: flex;
  flex-direction: row;
  flex-grow: 1;
  overflow: hidden;
  position: relative;
}
.tag-container > * {
  margin: 0 4px;
}
.remove-tag-btn {
  margin-left: 4px;
}
.tags-input {
  display: flex;
}
.cell-tag:last-child:after {
  content: "";
  position: absolute;
  right: 0;
  width: 40px;
  height: 100%;
  /* Fade to background color of cell toolbar */
  background: linear-gradient(to right, rgba(0, 0, 0, 0), #EEE);
}
.tags-input > * {
  margin-left: 4px;
}
.cell-tag,
.tags-input input,
.tags-input button {
  display: block;
  width: 100%;
  height: 32px;
  padding: 6px 12px;
  font-size: 13px;
  line-height: 1.42857143;
  color: #555555;
  background-color: #fff;
  background-image: none;
  border: 1px solid #ccc;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  -webkit-transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  -o-transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  height: 30px;
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
  box-shadow: none;
  width: inherit;
  font-size: inherit;
  height: 22px;
  line-height: 22px;
  padding: 0px 4px;
  display: inline-block;
}
.cell-tag:focus,
.tags-input input:focus,
.tags-input button:focus {
  border-color: #66afe9;
  outline: 0;
  -webkit-box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, 0.6);
  box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, 0.6);
}
.cell-tag::-moz-placeholder,
.tags-input input::-moz-placeholder,
.tags-input button::-moz-placeholder {
  color: #999;
  opacity: 1;
}
.cell-tag:-ms-input-placeholder,
.tags-input input:-ms-input-placeholder,
.tags-input button:-ms-input-placeholder {
  color: #999;
}
.cell-tag::-webkit-input-placeholder,
.tags-input input::-webkit-input-placeholder,
.tags-input button::-webkit-input-placeholder {
  color: #999;
}
.cell-tag::-ms-expand,
.tags-input input::-ms-expand,
.tags-input button::-ms-expand {
  border: 0;
  background-color: transparent;
}
.cell-tag[disabled],
.tags-input input[disabled],
.tags-input button[disabled],
.cell-tag[readonly],
.tags-input input[readonly],
.tags-input button[readonly],
fieldset[disabled] .cell-tag,
fieldset[disabled] .tags-input input,
fieldset[disabled] .tags-input button {
  background-color: #eeeeee;
  opacity: 1;
}
.cell-tag[disabled],
.tags-input input[disabled],
.tags-input button[disabled],
fieldset[disabled] .cell-tag,
fieldset[disabled] .tags-input input,
fieldset[disabled] .tags-input button {
  cursor: not-allowed;
}
textarea.cell-tag,
textarea.tags-input input,
textarea.tags-input button {
  height: auto;
}
select.cell-tag,
select.tags-input input,
select.tags-input button {
  height: 30px;
  line-height: 30px;
}
textarea.cell-tag,
textarea.tags-input input,
textarea.tags-input button,
select[multiple].cell-tag,
select[multiple].tags-input input,
select[multiple].tags-input button {
  height: auto;
}
.cell-tag,
.tags-input button {
  padding: 0px 4px;
}
.cell-tag {
  background-color: #fff;
  white-space: nowrap;
}
.tags-input input[type=text]:focus {
  outline: none;
  box-shadow: none;
  border-color: #ccc;
}
.completions {
  position: absolute;
  z-index: 110;
  overflow: hidden;
  border: 1px solid #ababab;
  border-radius: 2px;
  -webkit-box-shadow: 0px 6px 10px -1px #adadad;
  box-shadow: 0px 6px 10px -1px #adadad;
  line-height: 1;
}
.completions select {
  background: white;
  outline: none;
  border: none;
  padding: 0px;
  margin: 0px;
  overflow: auto;
  font-family: monospace;
  font-size: 110%;
  color: #000;
  width: auto;
}
.completions select option.context {
  color: #286090;
}
#kernel_logo_widget .current_kernel_logo {
  display: none;
  margin-top: -1px;
  margin-bottom: -1px;
  width: 32px;
  height: 32px;
}
[dir="rtl"] #kernel_logo_widget {
  float: left !important;
  float: left;
}
.modal .modal-body .move-path {
  display: flex;
  flex-direction: row;
  justify-content: space;
  align-items: center;
}
.modal .modal-body .move-path .server-root {
  padding-right: 20px;
}
.modal .modal-body .move-path .path-input {
  flex: 1;
}
#menubar {
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  margin-top: 1px;
}
#menubar .navbar {
  border-top: 1px;
  border-radius: 0px 0px 2px 2px;
  margin-bottom: 0px;
}
#menubar .navbar-toggle {
  float: left;
  padding-top: 7px;
  padding-bottom: 7px;
  border: none;
}
#menubar .navbar-collapse {
  clear: left;
}
[dir="rtl"] #menubar .navbar-toggle {
  float: right;
}
[dir="rtl"] #menubar .navbar-collapse {
  clear: right;
}
[dir="rtl"] #menubar .navbar-nav {
  float: right;
}
[dir="rtl"] #menubar .nav {
  padding-right: 0px;
}
[dir="rtl"] #menubar .navbar-nav > li {
  float: right;
}
[dir="rtl"] #menubar .navbar-right {
  float: left !important;
}
[dir="rtl"] ul.dropdown-menu {
  text-align: right;
  left: auto;
}
[dir="rtl"] ul#new-menu.dropdown-menu {
  right: auto;
  left: 0;
}
.nav-wrapper {
  border-bottom: 1px solid #e7e7e7;
}
i.menu-icon {
  padding-top: 4px;
}
[dir="rtl"] i.menu-icon.pull-right {
  float: left !important;
  float: left;
}
ul#help_menu li a {
  overflow: hidden;
  padding-right: 2.2em;
}
ul#help_menu li a i {
  margin-right: -1.2em;
}
[dir="rtl"] ul#help_menu li a {
  padding-left: 2.2em;
}
[dir="rtl"] ul#help_menu li a i {
  margin-right: 0;
  margin-left: -1.2em;
}
[dir="rtl"] ul#help_menu li a i.pull-right {
  float: left !important;
  float: left;
}
.dropdown-submenu {
  position: relative;
}
.dropdown-submenu > .dropdown-menu {
  top: 0;
  left: 100%;
  margin-top: -6px;
  margin-left: -1px;
}
[dir="rtl"] .dropdown-submenu > .dropdown-menu {
  right: 100%;
  margin-right: -1px;
}
.dropdown-submenu:hover > .dropdown-menu {
  display: block;
}
.dropdown-submenu > a:after {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: block;
  content: "\f0da";
  float: right;
  color: #333333;
  margin-top: 2px;
  margin-right: -10px;
}
.dropdown-submenu > a:after.fa-pull-left {
  margin-right: .3em;
}
.dropdown-submenu > a:after.fa-pull-right {
  margin-left: .3em;
}
.dropdown-submenu > a:after.pull-left {
  margin-right: .3em;
}
.dropdown-submenu > a:after.pull-right {
  margin-left: .3em;
}
[dir="rtl"] .dropdown-submenu > a:after {
  float: left;
  content: "\f0d9";
  margin-right: 0;
  margin-left: -10px;
}
.dropdown-submenu:hover > a:after {
  color: #262626;
}
.dropdown-submenu.pull-left {
  float: none;
}
.dropdown-submenu.pull-left > .dropdown-menu {
  left: -100%;
  margin-left: 10px;
}
#notification_area {
  float: right !important;
  float: right;
  z-index: 10;
}
[dir="rtl"] #notification_area {
  float: left !important;
  float: left;
}
.indicator_area {
  float: right !important;
  float: right;
  color: #777;
  margin-left: 5px;
  margin-right: 5px;
  width: 11px;
  z-index: 10;
  text-align: center;
  width: auto;
}
[dir="rtl"] .indicator_area {
  float: left !important;
  float: left;
}
#kernel_indicator {
  float: right !important;
  float: right;
  color: #777;
  margin-left: 5px;
  margin-right: 5px;
  width: 11px;
  z-index: 10;
  text-align: center;
  width: auto;
  border-left: 1px solid;
}
#kernel_indicator .kernel_indicator_name {
  padding-left: 5px;
  padding-right: 5px;
}
[dir="rtl"] #kernel_indicator {
  float: left !important;
  float: left;
  border-left: 0;
  border-right: 1px solid;
}
#modal_indicator {
  float: right !important;
  float: right;
  color: #777;
  margin-left: 5px;
  margin-right: 5px;
  width: 11px;
  z-index: 10;
  text-align: center;
  width: auto;
}
[dir="rtl"] #modal_indicator {
  float: left !important;
  float: left;
}
#readonly-indicator {
  float: right !important;
  float: right;
  color: #777;
  margin-left: 5px;
  margin-right: 5px;
  width: 11px;
  z-index: 10;
  text-align: center;
  width: auto;
  margin-top: 2px;
  margin-bottom: 0px;
  margin-left: 0px;
  margin-right: 0px;
  display: none;
}
.modal_indicator:before {
  width: 1.28571429em;
  text-align: center;
}
.edit_mode .modal_indicator:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f040";
}
.edit_mode .modal_indicator:before.fa-pull-left {
  margin-right: .3em;
}
.edit_mode .modal_indicator:before.fa-pull-right {
  margin-left: .3em;
}
.edit_mode .modal_indicator:before.pull-left {
  margin-right: .3em;
}
.edit_mode .modal_indicator:before.pull-right {
  margin-left: .3em;
}
.command_mode .modal_indicator:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: ' ';
}
.command_mode .modal_indicator:before.fa-pull-left {
  margin-right: .3em;
}
.command_mode .modal_indicator:before.fa-pull-right {
  margin-left: .3em;
}
.command_mode .modal_indicator:before.pull-left {
  margin-right: .3em;
}
.command_mode .modal_indicator:before.pull-right {
  margin-left: .3em;
}
.kernel_idle_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f10c";
}
.kernel_idle_icon:before.fa-pull-left {
  margin-right: .3em;
}
.kernel_idle_icon:before.fa-pull-right {
  margin-left: .3em;
}
.kernel_idle_icon:before.pull-left {
  margin-right: .3em;
}
.kernel_idle_icon:before.pull-right {
  margin-left: .3em;
}
.kernel_busy_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f111";
}
.kernel_busy_icon:before.fa-pull-left {
  margin-right: .3em;
}
.kernel_busy_icon:before.fa-pull-right {
  margin-left: .3em;
}
.kernel_busy_icon:before.pull-left {
  margin-right: .3em;
}
.kernel_busy_icon:before.pull-right {
  margin-left: .3em;
}
.kernel_dead_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f1e2";
}
.kernel_dead_icon:before.fa-pull-left {
  margin-right: .3em;
}
.kernel_dead_icon:before.fa-pull-right {
  margin-left: .3em;
}
.kernel_dead_icon:before.pull-left {
  margin-right: .3em;
}
.kernel_dead_icon:before.pull-right {
  margin-left: .3em;
}
.kernel_disconnected_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f127";
}
.kernel_disconnected_icon:before.fa-pull-left {
  margin-right: .3em;
}
.kernel_disconnected_icon:before.fa-pull-right {
  margin-left: .3em;
}
.kernel_disconnected_icon:before.pull-left {
  margin-right: .3em;
}
.kernel_disconnected_icon:before.pull-right {
  margin-left: .3em;
}
.notification_widget {
  color: #777;
  z-index: 10;
  background: rgba(240, 240, 240, 0.5);
  margin-right: 4px;
  color: #333;
  background-color: #fff;
  border-color: #ccc;
}
.notification_widget:focus,
.notification_widget.focus {
  color: #333;
  background-color: #e6e6e6;
  border-color: #8c8c8c;
}
.notification_widget:hover {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
.notification_widget:active,
.notification_widget.active,
.open > .dropdown-toggle.notification_widget {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
.notification_widget:active:hover,
.notification_widget.active:hover,
.open > .dropdown-toggle.notification_widget:hover,
.notification_widget:active:focus,
.notification_widget.active:focus,
.open > .dropdown-toggle.notification_widget:focus,
.notification_widget:active.focus,
.notification_widget.active.focus,
.open > .dropdown-toggle.notification_widget.focus {
  color: #333;
  background-color: #d4d4d4;
  border-color: #8c8c8c;
}
.notification_widget:active,
.notification_widget.active,
.open > .dropdown-toggle.notification_widget {
  background-image: none;
}
.notification_widget.disabled:hover,
.notification_widget[disabled]:hover,
fieldset[disabled] .notification_widget:hover,
.notification_widget.disabled:focus,
.notification_widget[disabled]:focus,
fieldset[disabled] .notification_widget:focus,
.notification_widget.disabled.focus,
.notification_widget[disabled].focus,
fieldset[disabled] .notification_widget.focus {
  background-color: #fff;
  border-color: #ccc;
}
.notification_widget .badge {
  color: #fff;
  background-color: #333;
}
.notification_widget.warning {
  color: #fff;
  background-color: #f0ad4e;
  border-color: #eea236;
}
.notification_widget.warning:focus,
.notification_widget.warning.focus {
  color: #fff;
  background-color: #ec971f;
  border-color: #985f0d;
}
.notification_widget.warning:hover {
  color: #fff;
  background-color: #ec971f;
  border-color: #d58512;
}
.notification_widget.warning:active,
.notification_widget.warning.active,
.open > .dropdown-toggle.notification_widget.warning {
  color: #fff;
  background-color: #ec971f;
  border-color: #d58512;
}
.notification_widget.warning:active:hover,
.notification_widget.warning.active:hover,
.open > .dropdown-toggle.notification_widget.warning:hover,
.notification_widget.warning:active:focus,
.notification_widget.warning.active:focus,
.open > .dropdown-toggle.notification_widget.warning:focus,
.notification_widget.warning:active.focus,
.notification_widget.warning.active.focus,
.open > .dropdown-toggle.notification_widget.warning.focus {
  color: #fff;
  background-color: #d58512;
  border-color: #985f0d;
}
.notification_widget.warning:active,
.notification_widget.warning.active,
.open > .dropdown-toggle.notification_widget.warning {
  background-image: none;
}
.notification_widget.warning.disabled:hover,
.notification_widget.warning[disabled]:hover,
fieldset[disabled] .notification_widget.warning:hover,
.notification_widget.warning.disabled:focus,
.notification_widget.warning[disabled]:focus,
fieldset[disabled] .notification_widget.warning:focus,
.notification_widget.warning.disabled.focus,
.notification_widget.warning[disabled].focus,
fieldset[disabled] .notification_widget.warning.focus {
  background-color: #f0ad4e;
  border-color: #eea236;
}
.notification_widget.warning .badge {
  color: #f0ad4e;
  background-color: #fff;
}
.notification_widget.success {
  color: #fff;
  background-color: #5cb85c;
  border-color: #4cae4c;
}
.notification_widget.success:focus,
.notification_widget.success.focus {
  color: #fff;
  background-color: #449d44;
  border-color: #255625;
}
.notification_widget.success:hover {
  color: #fff;
  background-color: #449d44;
  border-color: #398439;
}
.notification_widget.success:active,
.notification_widget.success.active,
.open > .dropdown-toggle.notification_widget.success {
  color: #fff;
  background-color: #449d44;
  border-color: #398439;
}
.notification_widget.success:active:hover,
.notification_widget.success.active:hover,
.open > .dropdown-toggle.notification_widget.success:hover,
.notification_widget.success:active:focus,
.notification_widget.success.active:focus,
.open > .dropdown-toggle.notification_widget.success:focus,
.notification_widget.success:active.focus,
.notification_widget.success.active.focus,
.open > .dropdown-toggle.notification_widget.success.focus {
  color: #fff;
  background-color: #398439;
  border-color: #255625;
}
.notification_widget.success:active,
.notification_widget.success.active,
.open > .dropdown-toggle.notification_widget.success {
  background-image: none;
}
.notification_widget.success.disabled:hover,
.notification_widget.success[disabled]:hover,
fieldset[disabled] .notification_widget.success:hover,
.notification_widget.success.disabled:focus,
.notification_widget.success[disabled]:focus,
fieldset[disabled] .notification_widget.success:focus,
.notification_widget.success.disabled.focus,
.notification_widget.success[disabled].focus,
fieldset[disabled] .notification_widget.success.focus {
  background-color: #5cb85c;
  border-color: #4cae4c;
}
.notification_widget.success .badge {
  color: #5cb85c;
  background-color: #fff;
}
.notification_widget.info {
  color: #fff;
  background-color: #5bc0de;
  border-color: #46b8da;
}
.notification_widget.info:focus,
.notification_widget.info.focus {
  color: #fff;
  background-color: #31b0d5;
  border-color: #1b6d85;
}
.notification_widget.info:hover {
  color: #fff;
  background-color: #31b0d5;
  border-color: #269abc;
}
.notification_widget.info:active,
.notification_widget.info.active,
.open > .dropdown-toggle.notification_widget.info {
  color: #fff;
  background-color: #31b0d5;
  border-color: #269abc;
}
.notification_widget.info:active:hover,
.notification_widget.info.active:hover,
.open > .dropdown-toggle.notification_widget.info:hover,
.notification_widget.info:active:focus,
.notification_widget.info.active:focus,
.open > .dropdown-toggle.notification_widget.info:focus,
.notification_widget.info:active.focus,
.notification_widget.info.active.focus,
.open > .dropdown-toggle.notification_widget.info.focus {
  color: #fff;
  background-color: #269abc;
  border-color: #1b6d85;
}
.notification_widget.info:active,
.notification_widget.info.active,
.open > .dropdown-toggle.notification_widget.info {
  background-image: none;
}
.notification_widget.info.disabled:hover,
.notification_widget.info[disabled]:hover,
fieldset[disabled] .notification_widget.info:hover,
.notification_widget.info.disabled:focus,
.notification_widget.info[disabled]:focus,
fieldset[disabled] .notification_widget.info:focus,
.notification_widget.info.disabled.focus,
.notification_widget.info[disabled].focus,
fieldset[disabled] .notification_widget.info.focus {
  background-color: #5bc0de;
  border-color: #46b8da;
}
.notification_widget.info .badge {
  color: #5bc0de;
  background-color: #fff;
}
.notification_widget.danger {
  color: #fff;
  background-color: #d9534f;
  border-color: #d43f3a;
}
.notification_widget.danger:focus,
.notification_widget.danger.focus {
  color: #fff;
  background-color: #c9302c;
  border-color: #761c19;
}
.notification_widget.danger:hover {
  color: #fff;
  background-color: #c9302c;
  border-color: #ac2925;
}
.notification_widget.danger:active,
.notification_widget.danger.active,
.open > .dropdown-toggle.notification_widget.danger {
  color: #fff;
  background-color: #c9302c;
  border-color: #ac2925;
}
.notification_widget.danger:active:hover,
.notification_widget.danger.active:hover,
.open > .dropdown-toggle.notification_widget.danger:hover,
.notification_widget.danger:active:focus,
.notification_widget.danger.active:focus,
.open > .dropdown-toggle.notification_widget.danger:focus,
.notification_widget.danger:active.focus,
.notification_widget.danger.active.focus,
.open > .dropdown-toggle.notification_widget.danger.focus {
  color: #fff;
  background-color: #ac2925;
  border-color: #761c19;
}
.notification_widget.danger:active,
.notification_widget.danger.active,
.open > .dropdown-toggle.notification_widget.danger {
  background-image: none;
}
.notification_widget.danger.disabled:hover,
.notification_widget.danger[disabled]:hover,
fieldset[disabled] .notification_widget.danger:hover,
.notification_widget.danger.disabled:focus,
.notification_widget.danger[disabled]:focus,
fieldset[disabled] .notification_widget.danger:focus,
.notification_widget.danger.disabled.focus,
.notification_widget.danger[disabled].focus,
fieldset[disabled] .notification_widget.danger.focus {
  background-color: #d9534f;
  border-color: #d43f3a;
}
.notification_widget.danger .badge {
  color: #d9534f;
  background-color: #fff;
}
div#pager {
  background-color: #fff;
  font-size: 14px;
  line-height: 20px;
  overflow: hidden;
  display: none;
  position: fixed;
  bottom: 0px;
  width: 100%;
  max-height: 50%;
  padding-top: 8px;
  -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  /* Display over codemirror */
  z-index: 100;
  /* Hack which prevents jquery ui resizable from changing top. */
  top: auto !important;
}
div#pager pre {
  line-height: 1.21429em;
  color: #000;
  background-color: #f7f7f7;
  padding: 0.4em;
}
div#pager #pager-button-area {
  position: absolute;
  top: 8px;
  right: 20px;
}
div#pager #pager-contents {
  position: relative;
  overflow: auto;
  width: 100%;
  height: 100%;
}
div#pager #pager-contents #pager-container {
  position: relative;
  padding: 15px 0px;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
}
div#pager .ui-resizable-handle {
  top: 0px;
  height: 8px;
  background: #f7f7f7;
  border-top: 1px solid #cfcfcf;
  border-bottom: 1px solid #cfcfcf;
  /* This injects handle bars (a short, wide = symbol) for
        the resize handle. */
}
div#pager .ui-resizable-handle::after {
  content: '';
  top: 2px;
  left: 50%;
  height: 3px;
  width: 30px;
  margin-left: -15px;
  position: absolute;
  border-top: 1px solid #cfcfcf;
}
.quickhelp {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
  line-height: 1.8em;
}
.shortcut_key {
  display: inline-block;
  width: 21ex;
  text-align: right;
  font-family: monospace;
}
.shortcut_descr {
  display: inline-block;
  /* Old browsers */
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  box-flex: 1;
  /* Modern browsers */
  flex: 1;
}
span.save_widget {
  height: 30px;
  margin-top: 4px;
  display: flex;
  justify-content: flex-start;
  align-items: baseline;
  width: 50%;
  flex: 1;
}
span.save_widget span.filename {
  height: 100%;
  line-height: 1em;
  margin-left: 16px;
  border: none;
  font-size: 146.5%;
  text-overflow: ellipsis;
  overflow: hidden;
  white-space: nowrap;
  border-radius: 2px;
}
span.save_widget span.filename:hover {
  background-color: #e6e6e6;
}
[dir="rtl"] span.save_widget.pull-left {
  float: right !important;
  float: right;
}
[dir="rtl"] span.save_widget span.filename {
  margin-left: 0;
  margin-right: 16px;
}
span.checkpoint_status,
span.autosave_status {
  font-size: small;
  white-space: nowrap;
  padding: 0 5px;
}
@media (max-width: 767px) {
  span.save_widget {
    font-size: small;
    padding: 0 0 0 5px;
  }
  span.checkpoint_status,
  span.autosave_status {
    display: none;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  span.checkpoint_status {
    display: none;
  }
  span.autosave_status {
    font-size: x-small;
  }
}
.toolbar {
  padding: 0px;
  margin-left: -5px;
  margin-top: 2px;
  margin-bottom: 5px;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
}
.toolbar select,
.toolbar label {
  width: auto;
  vertical-align: middle;
  margin-right: 2px;
  margin-bottom: 0px;
  display: inline;
  font-size: 92%;
  margin-left: 0.3em;
  margin-right: 0.3em;
  padding: 0px;
  padding-top: 3px;
}
.toolbar .btn {
  padding: 2px 8px;
}
.toolbar .btn-group {
  margin-top: 0px;
  margin-left: 5px;
}
.toolbar-btn-label {
  margin-left: 6px;
}
#maintoolbar {
  margin-bottom: -3px;
  margin-top: -8px;
  border: 0px;
  min-height: 27px;
  margin-left: 0px;
  padding-top: 11px;
  padding-bottom: 3px;
}
#maintoolbar .navbar-text {
  float: none;
  vertical-align: middle;
  text-align: right;
  margin-left: 5px;
  margin-right: 0px;
  margin-top: 0px;
}
.select-xs {
  height: 24px;
}
[dir="rtl"] .btn-group > .btn,
.btn-group-vertical > .btn {
  float: right;
}
.pulse,
.dropdown-menu > li > a.pulse,
li.pulse > a.dropdown-toggle,
li.pulse.open > a.dropdown-toggle {
  background-color: #F37626;
  color: white;
}
/**
 * Primary styles
 *
 * Author: Jupyter Development Team
 */
/** WARNING IF YOU ARE EDITTING THIS FILE, if this is a .css file, It has a lot
 * of chance of beeing generated from the ../less/[samename].less file, you can
 * try to get back the less file by reverting somme commit in history
 **/
/*
 * We'll try to get something pretty, so we
 * have some strange css to have the scroll bar on
 * the left with fix button on the top right of the tooltip
 */
@-moz-keyframes fadeOut {
  from {
    opacity: 1;
  }
  to {
    opacity: 0;
  }
}
@-webkit-keyframes fadeOut {
  from {
    opacity: 1;
  }
  to {
    opacity: 0;
  }
}
@-moz-keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
@-webkit-keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
/*properties of tooltip after "expand"*/
.bigtooltip {
  overflow: auto;
  height: 200px;
  -webkit-transition-property: height;
  -webkit-transition-duration: 500ms;
  -moz-transition-property: height;
  -moz-transition-duration: 500ms;
  transition-property: height;
  transition-duration: 500ms;
}
/*properties of tooltip before "expand"*/
.smalltooltip {
  -webkit-transition-property: height;
  -webkit-transition-duration: 500ms;
  -moz-transition-property: height;
  -moz-transition-duration: 500ms;
  transition-property: height;
  transition-duration: 500ms;
  text-overflow: ellipsis;
  overflow: hidden;
  height: 80px;
}
.tooltipbuttons {
  position: absolute;
  padding-right: 15px;
  top: 0px;
  right: 0px;
}
.tooltiptext {
  /*avoid the button to overlap on some docstring*/
  padding-right: 30px;
}
.ipython_tooltip {
  max-width: 700px;
  /*fade-in animation when inserted*/
  -webkit-animation: fadeOut 400ms;
  -moz-animation: fadeOut 400ms;
  animation: fadeOut 400ms;
  -webkit-animation: fadeIn 400ms;
  -moz-animation: fadeIn 400ms;
  animation: fadeIn 400ms;
  vertical-align: middle;
  background-color: #f7f7f7;
  overflow: visible;
  border: #ababab 1px solid;
  outline: none;
  padding: 3px;
  margin: 0px;
  padding-left: 7px;
  font-family: monospace;
  min-height: 50px;
  -moz-box-shadow: 0px 6px 10px -1px #adadad;
  -webkit-box-shadow: 0px 6px 10px -1px #adadad;
  box-shadow: 0px 6px 10px -1px #adadad;
  border-radius: 2px;
  position: absolute;
  z-index: 1000;
}
.ipython_tooltip a {
  float: right;
}
.ipython_tooltip .tooltiptext pre {
  border: 0;
  border-radius: 0;
  font-size: 100%;
  background-color: #f7f7f7;
}
.pretooltiparrow {
  left: 0px;
  margin: 0px;
  top: -16px;
  width: 40px;
  height: 16px;
  overflow: hidden;
  position: absolute;
}
.pretooltiparrow:before {
  background-color: #f7f7f7;
  border: 1px #ababab solid;
  z-index: 11;
  content: "";
  position: absolute;
  left: 15px;
  top: 10px;
  width: 25px;
  height: 25px;
  -webkit-transform: rotate(45deg);
  -moz-transform: rotate(45deg);
  -ms-transform: rotate(45deg);
  -o-transform: rotate(45deg);
}
ul.typeahead-list i {
  margin-left: -10px;
  width: 18px;
}
[dir="rtl"] ul.typeahead-list i {
  margin-left: 0;
  margin-right: -10px;
}
ul.typeahead-list {
  max-height: 80vh;
  overflow: auto;
}
ul.typeahead-list > li > a {
  /** Firefox bug **/
  /* see https://github.com/jupyter/notebook/issues/559 */
  white-space: normal;
}
ul.typeahead-list  > li > a.pull-right {
  float: left !important;
  float: left;
}
[dir="rtl"] .typeahead-list {
  text-align: right;
}
.cmd-palette .modal-body {
  padding: 7px;
}
.cmd-palette form {
  background: white;
}
.cmd-palette input {
  outline: none;
}
.no-shortcut {
  min-width: 20px;
  color: transparent;
}
[dir="rtl"] .no-shortcut.pull-right {
  float: left !important;
  float: left;
}
[dir="rtl"] .command-shortcut.pull-right {
  float: left !important;
  float: left;
}
.command-shortcut:before {
  content: "(command mode)";
  padding-right: 3px;
  color: #777777;
}
.edit-shortcut:before {
  content: "(edit)";
  padding-right: 3px;
  color: #777777;
}
[dir="rtl"] .edit-shortcut.pull-right {
  float: left !important;
  float: left;
}
#find-and-replace #replace-preview .match,
#find-and-replace #replace-preview .insert {
  background-color: #BBDEFB;
  border-color: #90CAF9;
  border-style: solid;
  border-width: 1px;
  border-radius: 0px;
}
[dir="ltr"] #find-and-replace .input-group-btn + .form-control {
  border-left: none;
}
[dir="rtl"] #find-and-replace .input-group-btn + .form-control {
  border-right: none;
}
#find-and-replace #replace-preview .replace .match {
  background-color: #FFCDD2;
  border-color: #EF9A9A;
  border-radius: 0px;
}
#find-and-replace #replace-preview .replace .insert {
  background-color: #C8E6C9;
  border-color: #A5D6A7;
  border-radius: 0px;
}
#find-and-replace #replace-preview {
  max-height: 60vh;
  overflow: auto;
}
#find-and-replace #replace-preview pre {
  padding: 5px 10px;
}
.terminal-app {
  background: #EEE;
}
.terminal-app #header {
  background: #fff;
  -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
}
.terminal-app .terminal {
  width: 100%;
  float: left;
  font-family: monospace;
  color: white;
  background: black;
  padding: 0.4em;
  border-radius: 2px;
  -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.4);
  box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.4);
}
.terminal-app .terminal,
.terminal-app .terminal dummy-screen {
  line-height: 1em;
  font-size: 14px;
}
.terminal-app .terminal .xterm-rows {
  padding: 10px;
}
.terminal-app .terminal-cursor {
  color: black;
  background: white;
}
.terminal-app #terminado-container {
  margin-top: 20px;
}
/*# sourceMappingURL=style.min.css.map */
    </style>
<style type="text/css">
    .highlight .hll { background-color: #ffffcc }
.highlight  { background: #f8f8f8; }
.highlight .c { color: #408080; font-style: italic } /* Comment */
.highlight .err { border: 1px solid #FF0000 } /* Error */
.highlight .k { color: #008000; font-weight: bold } /* Keyword */
.highlight .o { color: #666666 } /* Operator */
.highlight .ch { color: #408080; font-style: italic } /* Comment.Hashbang */
.highlight .cm { color: #408080; font-style: italic } /* Comment.Multiline */
.highlight .cp { color: #BC7A00 } /* Comment.Preproc */
.highlight .cpf { color: #408080; font-style: italic } /* Comment.PreprocFile */
.highlight .c1 { color: #408080; font-style: italic } /* Comment.Single */
.highlight .cs { color: #408080; font-style: italic } /* Comment.Special */
.highlight .gd { color: #A00000 } /* Generic.Deleted */
.highlight .ge { font-style: italic } /* Generic.Emph */
.highlight .gr { color: #FF0000 } /* Generic.Error */
.highlight .gh { color: #000080; font-weight: bold } /* Generic.Heading */
.highlight .gi { color: #00A000 } /* Generic.Inserted */
.highlight .go { color: #888888 } /* Generic.Output */
.highlight .gp { color: #000080; font-weight: bold } /* Generic.Prompt */
.highlight .gs { font-weight: bold } /* Generic.Strong */
.highlight .gu { color: #800080; font-weight: bold } /* Generic.Subheading */
.highlight .gt { color: #0044DD } /* Generic.Traceback */
.highlight .kc { color: #008000; font-weight: bold } /* Keyword.Constant */
.highlight .kd { color: #008000; font-weight: bold } /* Keyword.Declaration */
.highlight .kn { color: #008000; font-weight: bold } /* Keyword.Namespace */
.highlight .kp { color: #008000 } /* Keyword.Pseudo */
.highlight .kr { color: #008000; font-weight: bold } /* Keyword.Reserved */
.highlight .kt { color: #B00040 } /* Keyword.Type */
.highlight .m { color: #666666 } /* Literal.Number */
.highlight .s { color: #BA2121 } /* Literal.String */
.highlight .na { color: #7D9029 } /* Name.Attribute */
.highlight .nb { color: #008000 } /* Name.Builtin */
.highlight .nc { color: #0000FF; font-weight: bold } /* Name.Class */
.highlight .no { color: #880000 } /* Name.Constant */
.highlight .nd { color: #AA22FF } /* Name.Decorator */
.highlight .ni { color: #999999; font-weight: bold } /* Name.Entity */
.highlight .ne { color: #D2413A; font-weight: bold } /* Name.Exception */
.highlight .nf { color: #0000FF } /* Name.Function */
.highlight .nl { color: #A0A000 } /* Name.Label */
.highlight .nn { color: #0000FF; font-weight: bold } /* Name.Namespace */
.highlight .nt { color: #008000; font-weight: bold } /* Name.Tag */
.highlight .nv { color: #19177C } /* Name.Variable */
.highlight .ow { color: #AA22FF; font-weight: bold } /* Operator.Word */
.highlight .w { color: #bbbbbb } /* Text.Whitespace */
.highlight .mb { color: #666666 } /* Literal.Number.Bin */
.highlight .mf { color: #666666 } /* Literal.Number.Float */
.highlight .mh { color: #666666 } /* Literal.Number.Hex */
.highlight .mi { color: #666666 } /* Literal.Number.Integer */
.highlight .mo { color: #666666 } /* Literal.Number.Oct */
.highlight .sa { color: #BA2121 } /* Literal.String.Affix */
.highlight .sb { color: #BA2121 } /* Literal.String.Backtick */
.highlight .sc { color: #BA2121 } /* Literal.String.Char */
.highlight .dl { color: #BA2121 } /* Literal.String.Delimiter */
.highlight .sd { color: #BA2121; font-style: italic } /* Literal.String.Doc */
.highlight .s2 { color: #BA2121 } /* Literal.String.Double */
.highlight .se { color: #BB6622; font-weight: bold } /* Literal.String.Escape */
.highlight .sh { color: #BA2121 } /* Literal.String.Heredoc */
.highlight .si { color: #BB6688; font-weight: bold } /* Literal.String.Interpol */
.highlight .sx { color: #008000 } /* Literal.String.Other */
.highlight .sr { color: #BB6688 } /* Literal.String.Regex */
.highlight .s1 { color: #BA2121 } /* Literal.String.Single */
.highlight .ss { color: #19177C } /* Literal.String.Symbol */
.highlight .bp { color: #008000 } /* Name.Builtin.Pseudo */
.highlight .fm { color: #0000FF } /* Name.Function.Magic */
.highlight .vc { color: #19177C } /* Name.Variable.Class */
.highlight .vg { color: #19177C } /* Name.Variable.Global */
.highlight .vi { color: #19177C } /* Name.Variable.Instance */
.highlight .vm { color: #19177C } /* Name.Variable.Magic */
.highlight .il { color: #666666 } /* Literal.Number.Integer.Long */
    </style>


<style type="text/css">
/* Overrides of notebook CSS for static HTML export */
body {
  overflow: visible;
  padding: 8px;
}

div#notebook {
  overflow: visible;
  border-top: none;
}@media print {
  div.cell {
    display: block;
    page-break-inside: avoid;
  }
  div.output_wrapper {
    display: block;
    page-break-inside: avoid;
  }
  div.output {
    display: block;
    page-break-inside: avoid;
  }
}
</style>

<!-- Custom stylesheet, it must be in the same directory as the html file -->
<link rel="stylesheet" href="custom.css">

<!-- Loading mathjax macro -->
<!-- Load mathjax -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/latest.js?config=TeX-AMS_HTML"></script>
    <!-- MathJax configuration -->
    <script type="text/x-mathjax-config">
    MathJax.Hub.Config({
        tex2jax: {
            inlineMath: [ ['$','$'], ["\\(","\\)"] ],
            displayMath: [ ['$$','$$'], ["\\[","\\]"] ],
            processEscapes: true,
            processEnvironments: true
        },
        // Center justify equations in code and markdown cells. Elsewhere
        // we use CSS to left justify single line equations in code cells.
        displayAlign: 'center',
        "HTML-CSS": {
            styles: {'.MathJax_Display': {"margin": 0}},
            linebreaks: { automatic: true }
        }
    });
    </script>
    <!-- End of mathjax configuration --></head>
<body>
  <div tabindex="-1" id="notebook" class="border-box-sizing">
    <div class="container" id="notebook-container">

<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[29]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">os</span>
<span class="kn">import</span> <span class="nn">sys</span>
<span class="kn">import</span> <span class="nn">scipy.io</span>
<span class="kn">import</span> <span class="nn">scipy.misc</span>
<span class="kn">import</span> <span class="nn">matplotlib.pyplot</span> <span class="k">as</span> <span class="nn">plt</span>
<span class="kn">from</span> <span class="nn">matplotlib.pyplot</span> <span class="kn">import</span> <span class="n">imshow</span>
<span class="kn">from</span> <span class="nn">PIL</span> <span class="kn">import</span> <span class="n">Image</span>
<span class="kn">from</span> <span class="nn">nst_utils</span> <span class="kn">import</span> <span class="o">*</span>
<span class="kn">import</span> <span class="nn">numpy</span> <span class="k">as</span> <span class="nn">np</span>
<span class="kn">import</span> <span class="nn">tensorflow</span> <span class="k">as</span> <span class="nn">tf</span>
<span class="kn">import</span> <span class="nn">warnings</span><span class="p">;</span> <span class="n">warnings</span><span class="o">.</span><span class="n">simplefilter</span><span class="p">(</span><span class="s1">&#39;ignore&#39;</span><span class="p">)</span>

<span class="o">%</span><span class="k">matplotlib</span> inline
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="The-Challenge">The Challenge<a class="anchor-link" href="#The-Challenge">&#182;</a></h2><p>I love art. Unfortunately, I am not the best at expressing my art. Here's me having a go at drawing my dog:</p>
<p><img src="images/poca_drawing.png"></p>
<p>While there is some merit in this attempt (notice the waggling tail and the shadow details), when i picture a drawing of my dog I imagine a Picasso. In this notebook I'm going to do just that, by using neural style transfer to learn Picasso's style and use it on a photo of my dog, which is going to serve as our content image. My objective is to end up with a picture that mimics the style of Pablo Picasso, while keeping the end result as close as possible to the original.</p>
<p>This challenge is inspired by the exercise in Style Transfer from the Week 4 of the course Convolutional Neural Networks by Deeplearning.ai on Coursera.</p>
<p>More concretely, I am going to use a content image (C - photo of poca), and a style image (S - a painting of Picasso) to output a generated image (G) that looks like the original image C but with the style of S.
Let's get started.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>As I mentioned, we are going to use Neural Style Transfer on this project, meaning that we are going to use a convolutional network that was previously trained with much more data than what we have available. Additionally, orignal task of this network was not the creation of art, and that's fine. The reasons for that is that, we are not looking for the outputs of this network but rather the activations at earlier layers, hoping to detect low level features that are caracteristic of Picasso and his paintings.</p>
<p>In this exercise we will use a 19-layer version of the VGG network.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[7]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">model</span> <span class="o">=</span> <span class="n">load_vgg_model</span><span class="p">(</span><span class="s2">&quot;pretrained-model/imagenet-vgg-verydeep-19.mat&quot;</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="n">model</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>{&#39;input&#39;: &lt;tf.Variable &#39;Variable_1:0&#39; shape=(1, 300, 400, 3) dtype=float32_ref&gt;, &#39;conv1_1&#39;: &lt;tf.Tensor &#39;Relu_16:0&#39; shape=(1, 300, 400, 64) dtype=float32&gt;, &#39;conv1_2&#39;: &lt;tf.Tensor &#39;Relu_17:0&#39; shape=(1, 300, 400, 64) dtype=float32&gt;, &#39;avgpool1&#39;: &lt;tf.Tensor &#39;AvgPool_5:0&#39; shape=(1, 150, 200, 64) dtype=float32&gt;, &#39;conv2_1&#39;: &lt;tf.Tensor &#39;Relu_18:0&#39; shape=(1, 150, 200, 128) dtype=float32&gt;, &#39;conv2_2&#39;: &lt;tf.Tensor &#39;Relu_19:0&#39; shape=(1, 150, 200, 128) dtype=float32&gt;, &#39;avgpool2&#39;: &lt;tf.Tensor &#39;AvgPool_6:0&#39; shape=(1, 75, 100, 128) dtype=float32&gt;, &#39;conv3_1&#39;: &lt;tf.Tensor &#39;Relu_20:0&#39; shape=(1, 75, 100, 256) dtype=float32&gt;, &#39;conv3_2&#39;: &lt;tf.Tensor &#39;Relu_21:0&#39; shape=(1, 75, 100, 256) dtype=float32&gt;, &#39;conv3_3&#39;: &lt;tf.Tensor &#39;Relu_22:0&#39; shape=(1, 75, 100, 256) dtype=float32&gt;, &#39;conv3_4&#39;: &lt;tf.Tensor &#39;Relu_23:0&#39; shape=(1, 75, 100, 256) dtype=float32&gt;, &#39;avgpool3&#39;: &lt;tf.Tensor &#39;AvgPool_7:0&#39; shape=(1, 38, 50, 256) dtype=float32&gt;, &#39;conv4_1&#39;: &lt;tf.Tensor &#39;Relu_24:0&#39; shape=(1, 38, 50, 512) dtype=float32&gt;, &#39;conv4_2&#39;: &lt;tf.Tensor &#39;Relu_25:0&#39; shape=(1, 38, 50, 512) dtype=float32&gt;, &#39;conv4_3&#39;: &lt;tf.Tensor &#39;Relu_26:0&#39; shape=(1, 38, 50, 512) dtype=float32&gt;, &#39;conv4_4&#39;: &lt;tf.Tensor &#39;Relu_27:0&#39; shape=(1, 38, 50, 512) dtype=float32&gt;, &#39;avgpool4&#39;: &lt;tf.Tensor &#39;AvgPool_8:0&#39; shape=(1, 19, 25, 512) dtype=float32&gt;, &#39;conv5_1&#39;: &lt;tf.Tensor &#39;Relu_28:0&#39; shape=(1, 19, 25, 512) dtype=float32&gt;, &#39;conv5_2&#39;: &lt;tf.Tensor &#39;Relu_29:0&#39; shape=(1, 19, 25, 512) dtype=float32&gt;, &#39;conv5_3&#39;: &lt;tf.Tensor &#39;Relu_30:0&#39; shape=(1, 19, 25, 512) dtype=float32&gt;, &#39;conv5_4&#39;: &lt;tf.Tensor &#39;Relu_31:0&#39; shape=(1, 19, 25, 512) dtype=float32&gt;, &#39;avgpool5&#39;: &lt;tf.Tensor &#39;AvgPool_9:0&#39; shape=(1, 10, 13, 512) dtype=float32&gt;}
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="The-model">The model<a class="anchor-link" href="#The-model">&#182;</a></h2><p>The model will have :</p>
<ul>
<li>A function that calculates the cost between the generated image and the content image $J_{content}(C,G)$</li>
<li>A function that calculates the style difference between the generated image and the style image $J_{style}(S,G)$</li>
<li>A function that calculates both costs summed up $J(G) = \alpha J_{content}(C,G) + \beta J_{style}(S,G)$. </li>
</ul>
<h3 id="Content-Image">Content Image<a class="anchor-link" href="#Content-Image">&#182;</a></h3><p>Our content image is a photo of Poca, at the beach:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[8]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">content_image</span> <span class="o">=</span> <span class="n">scipy</span><span class="o">.</span><span class="n">misc</span><span class="o">.</span><span class="n">imread</span><span class="p">(</span><span class="s2">&quot;images\pipoca_beach_small.jpg&quot;</span><span class="p">)</span>
<span class="n">imshow</span><span class="p">(</span><span class="n">content_image</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[8]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>&lt;matplotlib.image.AxesImage at 0x1d1da649e10&gt;</pre>
</div>

</div>

<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,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
"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>To compute the content cost we need a function that takes in the activation layers of the content and style images and computes the difference between, adjusted for the size of the image.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[9]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="k">def</span> <span class="nf">compute_content_cost</span><span class="p">(</span><span class="n">a_C</span><span class="p">,</span> <span class="n">a_G</span><span class="p">):</span>

    <span class="c1"># Dimensions from a_G</span>
    <span class="n">m</span><span class="p">,</span> <span class="n">n_H</span><span class="p">,</span> <span class="n">n_W</span><span class="p">,</span> <span class="n">n_C</span> <span class="o">=</span> <span class="n">a_G</span><span class="o">.</span><span class="n">get_shape</span><span class="p">()</span><span class="o">.</span><span class="n">as_list</span><span class="p">()</span>

    <span class="c1"># Reshape a_C and a_G</span>
    <span class="n">a_C_unrolled</span> <span class="o">=</span> <span class="n">tf</span><span class="o">.</span><span class="n">transpose</span><span class="p">(</span><span class="n">tf</span><span class="o">.</span><span class="n">reshape</span><span class="p">(</span><span class="n">a_C</span><span class="p">,</span> <span class="p">[</span><span class="n">n_H</span> <span class="o">*</span> <span class="n">n_W</span><span class="p">,</span> <span class="n">n_C</span><span class="p">]</span> <span class="p">))</span>
    <span class="n">a_G_unrolled</span> <span class="o">=</span> <span class="n">tf</span><span class="o">.</span><span class="n">transpose</span><span class="p">(</span><span class="n">tf</span><span class="o">.</span><span class="n">reshape</span><span class="p">(</span><span class="n">a_G</span><span class="p">,</span> <span class="p">[</span><span class="n">n_H</span> <span class="o">*</span> <span class="n">n_W</span><span class="p">,</span> <span class="n">n_C</span><span class="p">]</span> <span class="p">))</span>

    <span class="c1"># compute the cost with tensorflow</span>
    <span class="n">J_content</span> <span class="o">=</span> <span class="n">tf</span><span class="o">.</span><span class="n">reduce_sum</span><span class="p">(</span><span class="n">tf</span><span class="o">.</span><span class="n">square</span><span class="p">(</span><span class="n">tf</span><span class="o">.</span><span class="n">subtract</span><span class="p">(</span><span class="n">a_G_unrolled</span><span class="p">,</span><span class="n">a_C_unrolled</span><span class="p">)))</span> <span class="o">*</span> <span class="p">(</span><span class="mi">1</span><span class="o">/</span><span class="p">(</span><span class="mi">4</span><span class="o">*</span><span class="n">n_H</span><span class="o">*</span><span class="n">n_W</span><span class="o">*</span><span class="n">n_C</span><span class="p">))</span>

    <span class="k">return</span> <span class="n">J_content</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[10]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">style_image</span> <span class="o">=</span> <span class="n">scipy</span><span class="o">.</span><span class="n">misc</span><span class="o">.</span><span class="n">imread</span><span class="p">(</span><span class="s2">&quot;picasso_small.jpg&quot;</span><span class="p">)</span>
<span class="n">imshow</span><span class="p">(</span><span class="n">style_image</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[10]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>&lt;matplotlib.image.AxesImage at 0x1d1bc152ef0&gt;</pre>
</div>

</div>

<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,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
"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[11]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="k">def</span> <span class="nf">gram_matrix</span><span class="p">(</span><span class="n">A</span><span class="p">):</span>

    <span class="n">GA</span> <span class="o">=</span> <span class="n">tf</span><span class="o">.</span><span class="n">matmul</span><span class="p">(</span><span class="n">A</span><span class="p">,</span><span class="n">tf</span><span class="o">.</span><span class="n">transpose</span><span class="p">(</span><span class="n">A</span><span class="p">))</span>

    <span class="k">return</span> <span class="n">GA</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[13]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="k">def</span> <span class="nf">compute_layer_style_cost</span><span class="p">(</span><span class="n">a_S</span><span class="p">,</span> <span class="n">a_G</span><span class="p">):</span>

    <span class="c1"># Retrieve dimensions from a_G (≈1 line)</span>
    <span class="n">m</span><span class="p">,</span> <span class="n">n_H</span><span class="p">,</span> <span class="n">n_W</span><span class="p">,</span> <span class="n">n_C</span> <span class="o">=</span> <span class="n">a_G</span><span class="o">.</span><span class="n">get_shape</span><span class="p">()</span><span class="o">.</span><span class="n">as_list</span><span class="p">()</span>

    <span class="c1"># Reshape the images to have them of shape (n_C, n_H*n_W)</span>
    <span class="n">a_S</span> <span class="o">=</span> <span class="n">tf</span><span class="o">.</span><span class="n">transpose</span><span class="p">(</span><span class="n">tf</span><span class="o">.</span><span class="n">reshape</span><span class="p">(</span><span class="n">a_S</span><span class="p">,</span> <span class="p">[</span><span class="n">n_H</span> <span class="o">*</span> <span class="n">n_W</span><span class="p">,</span> <span class="n">n_C</span><span class="p">]))</span>
    <span class="n">a_G</span> <span class="o">=</span> <span class="n">tf</span><span class="o">.</span><span class="n">transpose</span><span class="p">(</span><span class="n">tf</span><span class="o">.</span><span class="n">reshape</span><span class="p">(</span><span class="n">a_G</span><span class="p">,</span> <span class="p">[</span><span class="n">n_H</span> <span class="o">*</span> <span class="n">n_W</span><span class="p">,</span> <span class="n">n_C</span><span class="p">]))</span>

    <span class="c1"># Computing gram_matrices for both images S and G</span>
    <span class="n">GS</span> <span class="o">=</span> <span class="n">gram_matrix</span><span class="p">(</span><span class="n">a_S</span><span class="p">)</span>
    <span class="n">GG</span> <span class="o">=</span> <span class="n">gram_matrix</span><span class="p">(</span><span class="n">a_G</span><span class="p">)</span>

    <span class="c1"># Computing the loss</span>
    <span class="n">J_style_layer</span> <span class="o">=</span> <span class="n">tf</span><span class="o">.</span><span class="n">reduce_sum</span><span class="p">(</span><span class="n">tf</span><span class="o">.</span><span class="n">square</span><span class="p">(</span><span class="n">tf</span><span class="o">.</span><span class="n">subtract</span><span class="p">(</span><span class="n">GS</span><span class="p">,</span> <span class="n">GG</span><span class="p">)))</span> <span class="o">*</span> <span class="p">(</span><span class="mi">1</span> <span class="o">/</span> <span class="p">(</span><span class="mi">4</span> <span class="o">*</span> <span class="n">n_C</span> <span class="o">**</span><span class="mi">2</span> <span class="o">*</span> <span class="p">(</span><span class="n">n_H</span> <span class="o">*</span> <span class="n">n_W</span><span class="p">)</span> <span class="o">**</span><span class="mi">2</span><span class="p">))</span>

    <span class="k">return</span> <span class="n">J_style_layer</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[14]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">STYLE_LAYERS</span> <span class="o">=</span> <span class="p">[</span>
    <span class="p">(</span><span class="s1">&#39;conv1_1&#39;</span><span class="p">,</span> <span class="mf">0.2</span><span class="p">),</span>
    <span class="p">(</span><span class="s1">&#39;conv2_1&#39;</span><span class="p">,</span> <span class="mf">0.2</span><span class="p">),</span>
    <span class="p">(</span><span class="s1">&#39;conv3_1&#39;</span><span class="p">,</span> <span class="mf">0.2</span><span class="p">),</span>
    <span class="p">(</span><span class="s1">&#39;conv4_1&#39;</span><span class="p">,</span> <span class="mf">0.2</span><span class="p">),</span>
    <span class="p">(</span><span class="s1">&#39;conv5_1&#39;</span><span class="p">,</span> <span class="mf">0.2</span><span class="p">)]</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[15]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="k">def</span> <span class="nf">compute_style_cost</span><span class="p">(</span><span class="n">model</span><span class="p">,</span> <span class="n">STYLE_LAYERS</span><span class="p">):</span>

    <span class="c1"># initialize the overall style cost</span>
    <span class="n">J_style</span> <span class="o">=</span> <span class="mi">0</span>

    <span class="k">for</span> <span class="n">layer_name</span><span class="p">,</span> <span class="n">coeff</span> <span class="ow">in</span> <span class="n">STYLE_LAYERS</span><span class="p">:</span>

        <span class="c1"># Select the output tensor of the currently selected layer</span>
        <span class="n">out</span> <span class="o">=</span> <span class="n">model</span><span class="p">[</span><span class="n">layer_name</span><span class="p">]</span>

        <span class="c1"># Set a_S to be the hidden layer activation from the layer we have selected, by running the session on out</span>
        <span class="n">a_S</span> <span class="o">=</span> <span class="n">sess</span><span class="o">.</span><span class="n">run</span><span class="p">(</span><span class="n">out</span><span class="p">)</span>

        <span class="c1"># Set a_G to be the hidden layer activation from same layer. </span>
        <span class="n">a_G</span> <span class="o">=</span> <span class="n">out</span>

        <span class="c1"># Compute style_cost for the current layer</span>
        <span class="n">J_style_layer</span> <span class="o">=</span> <span class="n">compute_layer_style_cost</span><span class="p">(</span><span class="n">a_S</span><span class="p">,</span> <span class="n">a_G</span><span class="p">)</span>

        <span class="c1"># Add coeff * J_style_layer of this layer to overall style cost</span>
        <span class="n">J_style</span> <span class="o">+=</span> <span class="n">coeff</span> <span class="o">*</span> <span class="n">J_style_layer</span>

    <span class="k">return</span> <span class="n">J_style</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[16]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="k">def</span> <span class="nf">total_cost</span><span class="p">(</span><span class="n">J_content</span><span class="p">,</span> <span class="n">J_style</span><span class="p">,</span> <span class="n">alpha</span> <span class="o">=</span> <span class="mi">10</span><span class="p">,</span> <span class="n">beta</span> <span class="o">=</span> <span class="mi">40</span><span class="p">):</span>

    <span class="n">J</span> <span class="o">=</span> <span class="n">J</span> <span class="o">=</span> <span class="n">alpha</span> <span class="o">*</span> <span class="n">J_content</span> <span class="o">+</span> <span class="n">beta</span> <span class="o">*</span> <span class="n">J_style</span>

    <span class="k">return</span> <span class="n">J</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[17]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># Reset the graph</span>
<span class="n">tf</span><span class="o">.</span><span class="n">reset_default_graph</span><span class="p">()</span>

<span class="c1"># Start interactive session</span>
<span class="n">sess</span> <span class="o">=</span> <span class="n">tf</span><span class="o">.</span><span class="n">InteractiveSession</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[18]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">content_image</span> <span class="o">=</span> <span class="n">scipy</span><span class="o">.</span><span class="n">misc</span><span class="o">.</span><span class="n">imread</span><span class="p">(</span><span class="s2">&quot;pipoca_400300.jpg&quot;</span><span class="p">)</span>
<span class="n">content_image</span> <span class="o">=</span> <span class="n">reshape_and_normalize_image</span><span class="p">(</span><span class="n">content_image</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[21]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">style_image</span> <span class="o">=</span> <span class="n">scipy</span><span class="o">.</span><span class="n">misc</span><span class="o">.</span><span class="n">imread</span><span class="p">(</span><span class="s2">&quot;picasso_small.jpg&quot;</span><span class="p">)</span>
<span class="n">style_image</span> <span class="o">=</span> <span class="n">reshape_and_normalize_image</span><span class="p">(</span><span class="n">style_image</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[22]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">generated_image</span> <span class="o">=</span> <span class="n">generate_noise_image</span><span class="p">(</span><span class="n">content_image</span><span class="p">)</span>
<span class="n">imshow</span><span class="p">(</span><span class="n">generated_image</span><span class="p">[</span><span class="mi">0</span><span class="p">])</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stderr output_text">
<pre>Clipping input data to the valid range for imshow with RGB data ([0..1] for floats or [0..255] for integers).
</pre>
</div>
</div>

<div class="output_area">

    <div class="prompt output_prompt">Out[22]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>&lt;matplotlib.image.AxesImage at 0x1d1bc7d5da0&gt;</pre>
</div>

</div>

<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,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
"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[23]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">model</span> <span class="o">=</span> <span class="n">load_vgg_model</span><span class="p">(</span><span class="s2">&quot;pretrained-model/imagenet-vgg-verydeep-19.mat&quot;</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[24]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># Assign the content image to be the input of the VGG model.  </span>
<span class="n">sess</span><span class="o">.</span><span class="n">run</span><span class="p">(</span><span class="n">model</span><span class="p">[</span><span class="s1">&#39;input&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">assign</span><span class="p">(</span><span class="n">content_image</span><span class="p">))</span>

<span class="c1"># Select the output tensor of layer conv4_2</span>
<span class="n">out</span> <span class="o">=</span> <span class="n">model</span><span class="p">[</span><span class="s1">&#39;conv4_2&#39;</span><span class="p">]</span>

<span class="c1"># Set a_C to be the hidden layer activation from the layer we have selected</span>
<span class="n">a_C</span> <span class="o">=</span> <span class="n">sess</span><span class="o">.</span><span class="n">run</span><span class="p">(</span><span class="n">out</span><span class="p">)</span>

<span class="c1"># Set a_G to be the hidden layer activation from same layer.</span>
<span class="n">a_G</span> <span class="o">=</span> <span class="n">out</span>

<span class="c1"># Compute the content cost</span>
<span class="n">J_content</span> <span class="o">=</span> <span class="n">compute_content_cost</span><span class="p">(</span><span class="n">a_C</span><span class="p">,</span> <span class="n">a_G</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[25]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># Assign the input of the model to be the &quot;style&quot; image </span>
<span class="n">sess</span><span class="o">.</span><span class="n">run</span><span class="p">(</span><span class="n">model</span><span class="p">[</span><span class="s1">&#39;input&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">assign</span><span class="p">(</span><span class="n">style_image</span><span class="p">))</span>

<span class="c1"># Compute the style cost</span>
<span class="n">J_style</span> <span class="o">=</span> <span class="n">compute_style_cost</span><span class="p">(</span><span class="n">model</span><span class="p">,</span> <span class="n">STYLE_LAYERS</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[26]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">J</span> <span class="o">=</span> <span class="n">total_cost</span><span class="p">(</span><span class="n">J_content</span><span class="p">,</span> <span class="n">J_style</span><span class="p">,</span> <span class="n">alpha</span> <span class="o">=</span> <span class="mi">10</span><span class="p">,</span> <span class="n">beta</span> <span class="o">=</span> <span class="mi">40</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[27]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># define optimizer (1 line)</span>
<span class="n">optimizer</span> <span class="o">=</span> <span class="n">tf</span><span class="o">.</span><span class="n">train</span><span class="o">.</span><span class="n">AdamOptimizer</span><span class="p">(</span><span class="mf">2.0</span><span class="p">)</span>

<span class="c1"># define train_step (1 line)</span>
<span class="n">train_step</span> <span class="o">=</span> <span class="n">optimizer</span><span class="o">.</span><span class="n">minimize</span><span class="p">(</span><span class="n">J</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[28]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="k">def</span> <span class="nf">model_nn</span><span class="p">(</span><span class="n">sess</span><span class="p">,</span> <span class="n">input_image</span><span class="p">,</span> <span class="n">num_iterations</span> <span class="o">=</span> <span class="mi">800</span><span class="p">):</span>

    <span class="c1"># Initialize global variables (you need to run the session on the initializer)</span>

    <span class="n">sess</span><span class="o">.</span><span class="n">run</span><span class="p">(</span><span class="n">tf</span><span class="o">.</span><span class="n">global_variables_initializer</span><span class="p">())</span>

    <span class="c1"># Run the noisy input image (initial generated image) through the model. Use assign().</span>

    <span class="n">generated_image</span> <span class="o">=</span> <span class="n">sess</span><span class="o">.</span><span class="n">run</span><span class="p">(</span><span class="n">model</span><span class="p">[</span><span class="s1">&#39;input&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">assign</span><span class="p">(</span><span class="n">input_image</span><span class="p">))</span>

    <span class="k">for</span> <span class="n">i</span> <span class="ow">in</span> <span class="nb">range</span><span class="p">(</span><span class="n">num_iterations</span><span class="p">):</span>

        <span class="c1"># Run the session on the train_step to minimize the total cost</span>
        <span class="n">sess</span><span class="o">.</span><span class="n">run</span><span class="p">(</span><span class="n">train_step</span><span class="p">)</span>

        <span class="c1"># Compute the generated image by running the session on the current model[&#39;input&#39;]</span>
        <span class="n">generated_image</span> <span class="o">=</span> <span class="n">sess</span><span class="o">.</span><span class="n">run</span><span class="p">(</span><span class="n">model</span><span class="p">[</span><span class="s1">&#39;input&#39;</span><span class="p">])</span>

        <span class="c1"># Print every 20 iteration.</span>
        <span class="k">if</span> <span class="n">i</span><span class="o">%</span><span class="k">20</span> == 0:
            <span class="n">Jt</span><span class="p">,</span> <span class="n">Jc</span><span class="p">,</span> <span class="n">Js</span> <span class="o">=</span> <span class="n">sess</span><span class="o">.</span><span class="n">run</span><span class="p">([</span><span class="n">J</span><span class="p">,</span> <span class="n">J_content</span><span class="p">,</span> <span class="n">J_style</span><span class="p">])</span>
            <span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Iteration &quot;</span> <span class="o">+</span> <span class="nb">str</span><span class="p">(</span><span class="n">i</span><span class="p">)</span> <span class="o">+</span> <span class="s2">&quot; :&quot;</span><span class="p">)</span>
            <span class="nb">print</span><span class="p">(</span><span class="s2">&quot;total cost = &quot;</span> <span class="o">+</span> <span class="nb">str</span><span class="p">(</span><span class="n">Jt</span><span class="p">))</span>
            <span class="nb">print</span><span class="p">(</span><span class="s2">&quot;content cost = &quot;</span> <span class="o">+</span> <span class="nb">str</span><span class="p">(</span><span class="n">Jc</span><span class="p">))</span>
            <span class="nb">print</span><span class="p">(</span><span class="s2">&quot;style cost = &quot;</span> <span class="o">+</span> <span class="nb">str</span><span class="p">(</span><span class="n">Js</span><span class="p">))</span>

            <span class="c1"># save current generated image in the &quot;/output&quot; directory</span>
            <span class="n">save_image</span><span class="p">(</span><span class="s2">&quot;output/&quot;</span> <span class="o">+</span> <span class="nb">str</span><span class="p">(</span><span class="n">i</span><span class="p">)</span> <span class="o">+</span> <span class="s2">&quot;.png&quot;</span><span class="p">,</span> <span class="n">generated_image</span><span class="p">)</span>

    <span class="c1"># save last generated image</span>
    <span class="n">save_image</span><span class="p">(</span><span class="s1">&#39;output/generated_image.jpg&#39;</span><span class="p">,</span> <span class="n">generated_image</span><span class="p">)</span>

    <span class="k">return</span> <span class="n">generated_image</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>The last step is to run <code>model_nn(sess, generated_image)</code>
After running the code above we finally have our converted photo which looks like this:
<img src="images/poca_picasso.png"></p>
<p>We could go back and possibly choose a different layer but, in this case, I'm quite happy with the results.</p>

</div>
</div>
</div>
    </div>
  </div>
</body>




</html>
