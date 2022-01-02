<!DOCTYPE html>
<html lang="en">
<head>
 <meta charset="UTF-8">
 <meta name="viewport" content="width=device-width, initial-scale=1.0">
 <meta http-equiv="X-UA-Compatible" content="ie=edge">
 
 <link rel="stylesheet" href="assets/style.min.css">
 <title>Make Some Pixel Art</title>
</head>
<body>
  <header>
   <h1>NFT Studios<span></span></h1>
   <p>Javascript library to create pixel art from an image.</p>
   <div class="actions">
      <a href="#tryit" class="btn call">try it</a>
      <a href="#examples" class="btn ">examples</a>
      <a href="#docs" class="btn">Documentation</a>
      <a href="https://github.com/giventofly/pixelit" class="btn"  rel="nofollow noopener" target="_blank" title="github repository">github</a>
   </div>
  
  </header>
 <section class="example" id="examples">
   <div class="wrap">
    <p>NFT Studios allows you to take an image and convert into pixel art. You can define the "pixel" size, create a pixel image using a color palette and also convert to a pixel grayscale image.</p> 
    <p>You can use NFT Studios to be your jump start to make some pixel art. Check the documentation for all the available api methods.</p>
    
    <h2>Default usage</h2>
    <p>Blocksize of 7 and no other modification</p>
    <img src="assets/px-normal.jpg" alt="image pixelated block 4">
    
    <h2>Color palette</h2>
    <p>Blocksize of 17 and a 4 Color palette</p>
    <img src="assets/px-palette4c.jpg" alt="image pixelated 4c palette">

    <h2>Greyscale</h2>
    <p>blocksize of 10 and greyscale</p>
    <img src="assets/px-grey.jpg" alt="image pixelated greyscale">

    <h2>Color palette</h2>
    <p>Blocksize of 8 and a 16 Color palette</p>
    <img src="assets/px-16cp.jpg" alt="image pixelated 16c palette">

    </div>
  </section>
<section class="working">
  <div class="wrap">
  <h2>Use NFT Studios now</h2>
  <p>You can try NFT Studios live here, you can use the default image (just change some value) or upload an image to start see the changes.</p>

  <!-- max width -->
<div class="container maxwidth" id="tryit">
  <div class="selectors">
    <!--upload image -->
    <label id="uploadimage" for="pixlInput">Upload Image<input type="file" class="inputbtn" id="pixlInput"></label>
    <!-- block size -->
    <label for="blocksize" class="inputbtn">Block size<span id="blockvalue">7</span><input value="7" type="range" min="1" max="25" id="blocksize"></label>
    <!-- greyscale -->
    <label for="greyscale" class="inputbtn" >Greyscale<input type="checkbox" id="greyscale"></label>
    <!-- palette -->
    <label for="palette" class="inputbtn">palette<input type="checkbox"  id="palette"></label>
    <!-- max height -->
    <label for="maxheight" class="inputbtn">Max Height<input type="input"  id="maxheight" placeholder="in px"></label>
    <!-- max width -->
    <label for="maxwidth" class="inputbtn">Max Width<input type="input" id="maxwidth" placeholder="in px"></label
  </div>
  <div class="infoselects">
   <!-- color palette example-->
   <div class="colorpalette">
    <div class="text"><button class="btn small" id="changepalette">Change palette</button></div>
    <div class="icons" id="palettecolor">
    
    </div>
   </div>
   <div class="dothings">
   <!-- download image -->
   <Button id="downloadimage" class="btn small call">Download Image</Button>
   </div>
   
  </div>
 
 </div>
 <canvas id="pixelitcanvas"></canvas>
  </div>
</section>
 <section class="docs" id="docs">
   <div class="wrap withmargins">
  <h2>Documentation</h2>
  <h3>Quick usage</h3>
  <p>To use the quick default configuration you need an element from where to draw the image and canvas element with the id pixelitcanvas. Then load the pixelit.js script and apply it on an image.</p>
  <pre>
&lt;img src="assets/sky.jpg"  id="pixelitimg" alt=""&gt;
&lt;canvas id="pixelitcanvas"&gt;&lt;/canvas&gt;
&lt;script src="dist/pixelit.js"&gt;&lt;/script&gt;
&lt;script&gt;
  //create object
  const px = new pixelit();
  px.draw().pixelate();
&lt;/script</pre>

  
  <h3>Options</h3>
  <p>You can pass some options when creating the instance (you can alter them later using the api methods).</p>
  <pre>
config = {
  to : elem, defaults to document.getElementById("pixelitcanvas")
  from : elem, defaults to document.getElementById("pixelitimg")
  scale : int from 0-50, defaults to 8
  palette : [[r,g,b]], defaults to a fixed palette
  maxHeight: int, defaults to null
  maxWidth: int, defaults to null
}
  </pre>


  <h3>API</h3>
  <p>You can chain all methods together, beware that the order they are applied can change the final result.</p> 
  <p>Applying first the color palette and then the greyscale can give a slightlity different image.</p>

<p class="api"><strong>.draw()</strong> draw to canvas from image source and resizes if max height or max width is reached</p>
<p class="api"><strong>.hideFromImg()</strong> hides the from image element, is applied on object creation</p>
<p class="api"><strong>.setDrawFrom(elem)</strong> elem to get the image to pixelate</p>
<p class="api"><strong>.setDrawTo(elem)</strong> canvas elem to draw the image</p>
<p class="api"><strong>.setFromImgSource(src)</strong> change the src from the image element</p>
<p class="api"><strong>.setpalette(arr)</strong> sets the color palette to use, takes an array of rgb colors: [[int,int,int]], int from 0 to 255</p>
<p class="api"><strong>.setMaxWidth(int)</strong> set canvas image maximum width, it can resize the output image, only used when .resizeImage() is applied</p>
<p class="api"><strong>.setMaxHeight(int)</strong> set canvas image maximum height, it can resize the output image, max height overrides max width, only used when .resizeImage() is applied</p>
<p class="api"><strong>.setScale(int)</strong> set pixelate scale [0...50]</p>
<p class="api"><strong>.getpalette()</strong> returns array of current palette, can't be chained</p>
<p class="api"><strong>.convertGrayscale()</strong> converts image to greyscale, apply only after .draw is called</p>
<p class="api"><strong>.convertpalette()</strong> converts image with the defined color palette, apply only after .draw is called</p>
<p class="api"><strong>.resizeImage()</strong> resizes the output image if bigger than the defined max Height or max Width</p>
<p class="api"><strong>.pixelate()</strong> draws a pixelated version of the from image to the to canvas, , apply only after .draw is called</p>
<p class="api"><strong>.saveImage()</strong> saves/downloads current image</p>


</div>
  
</section>
 <section class="links"><div class="wrap">
   <a href="https://github.com/giventofly/pixelit" class="btn call github"  rel="nofollow noopener" target="_blank" title="github repository">github</a>
   <a href="https://twitter.com/heyzeto" class="btn call twitter" rel="nofollow noopener" title="twitter" target="_blank">twitter</a>
  </div></section>
  <img src="assets/sky.jpg"  id="pixelitimg" alt="">
  <!--<img style="visibility: hidden;" id="pixlimg" alt="">  -->
  <script>
    "use strict";function _classCallCheck(t,e){if(!(t instanceof e))throw new TypeError("Cannot call a class as a function")}function _defineProperties(t,e){for(var i=0;i<e.length;i++){var a=e[i];a.enumerable=a.enumerable||!1,a.configurable=!0,"value"in a&&(a.writable=!0),Object.defineProperty(t,a.key,a)}}function _createClass(t,e,i){return e&&_defineProperties(t.prototype,e),i&&_defineProperties(t,i),t}var pixelit=function(){function t(){var e=arguments.length>0&&void 0!==arguments[0]?arguments[0]:{};_classCallCheck(this,t),this.drawto=e.to||document.getElementById("pixelitcanvas"),this.drawfrom=e.from||document.getElementById("pixelitimg"),this.hideFromImg(),this.scale=e.scale&&e.scale>0&&e.scale<=50?.01*e.scale:.08,this.palette=e.palette||[[140,143,174],[88,69,99],[62,33,55],[154,99,72],[215,155,125],[245,237,186],[192,199,65],[100,125,52],[228,148,58],[157,48,59],[210,100,113],[112,55,127],[126,196,193],[52,133,157],[23,67,75],[31,14,28]],this.maxHeight=e.maxHeight,this.maxWidth=e.maxWidth,this.ctx=this.drawto.getContext("2d")}return _createClass(t,[{key:"hideFromImg",value:function(){return this.drawfrom.style.visibility="hidden",this.drawfrom.style.position="fixed",this.drawfrom.style.top=0,this.drawfrom.style.left=0,this}},{key:"setFromImgSource",value:function(t){return this.drawfrom.src=t,this}},{key:"setDrawFrom",value:function(t){return this.drawfrom=t,this}},{key:"setDrawTo",value:function(t){return this.drawto=t,this}},{key:"setPalette",value:function(t){return this.palette=t,this}},{key:"setMaxWidth",value:function(t){return this.maxWidth=t,this}},{key:"setMaxHeight",value:function(t){return this.maxHeight=t,this}},{key:"setScale",value:function(t){return this.scale=t>0&&t<=50?.01*t:.08,this}},{key:"getPalette",value:function(){return this.palette}},{key:"colorSim",value:function(t,e){var i,a,h=0;for(i=0,a=t.length;i<a;i++)h+=(t[i]-e[i])*(t[i]-e[i]);return Math.sqrt(h)}},{key:"similarColor",value:function(t){var e=this,i=[],a=this.colorSim(t,this.palette[0]);return this.palette.forEach((function(h){e.colorSim(t,h)<=a&&(i=h,a=e.colorSim(t,h))})),i}},{key:"pixelate",value:function(){this.drawto.width=this.drawfrom.naturalWidth,this.drawto.height=this.drawfrom.naturalHeight;var t=this.drawto.width*this.scale,e=this.drawto.height*this.scale,i=document.createElement("canvas");return(this.drawto.width>800||this.drawto.width>800)&&(this.scale*=.25,t=this.drawto.width*this.scale,e=this.drawto.height*this.scale,i.width=Math.max(t,e)+50,i.height=Math.max(t,e)+50),i.getContext("2d").drawImage(this.drawfrom,0,0,t,e),document.body.appendChild(i),this.ctx.mozImageSmoothingEnabled=!1,this.ctx.webkitImageSmoothingEnabled=!1,this.ctx.imageSmoothingEnabled=!1,this.ctx.drawImage(i,0,0,t,e,0,0,this.drawfrom.naturalWidth,this.drawfrom.naturalHeight),i.remove(),this}},{key:"convertGrayscale",value:function(){for(var t=this.drawto.width,e=this.drawto.height,i=this.ctx.getImageData(0,0,t,e),a=0;a<i.height;a++)for(var h=0;h<i.width;h++){var r=4*a*i.width+4*h,s=(i.data[r]+i.data[r+1]+i.data[r+2])/3;i.data[r]=s,i.data[r+1]=s,i.data[r+2]=s}return this.ctx.putImageData(i,0,0,0,0,i.width,i.height),this}},{key:"convertPalette",value:function(){for(var t=this.drawto.width,e=this.drawto.height,i=this.ctx.getImageData(0,0,t,e),a=0;a<i.height;a++)for(var h=0;h<i.width;h++){var r=4*a*i.width+4*h,s=this.similarColor([i.data[r],i.data[r+1],i.data[r+2]]);i.data[r]=s[0],i.data[r+1]=s[1],i.data[r+2]=s[2]}return this.ctx.putImageData(i,0,0,0,0,i.width,i.height),this}},{key:"resizeImage",value:function(){var t=document.createElement("canvas"),e=t.getContext("2d"),i=1;return this.maxWidth||this.maxHeight?(this.maxWidth&&this.drawto.width>this.maxWidth&&(i=this.maxWidth/this.drawto.width),this.maxHeight&&this.drawto.height>this.maxHeight&&(i=this.maxHeight/this.drawto.height),t.width=this.drawto.width,t.height=this.drawto.height,e.drawImage(this.drawto,0,0),this.drawto.width=this.drawto.width*i,this.drawto.height=this.drawto.height*i,this.ctx.drawImage(t,0,0,t.width,t.height,0,0,this.drawto.width,this.drawto.height),this):0}},{key:"draw",value:function(){return this.drawto.width=this.drawfrom.width,this.drawto.height=this.drawfrom.height,this.ctx.drawImage(this.drawfrom,0,0),this.resizeImage(),this}},{key:"saveImage",value:function(){var t=document.createElement("a");t.download="pxArt.png",t.href=this.drawto.toDataURL("image/png").replace("image/png","image/octet-stream"),document.querySelector("body").appendChild(t),t.click(),document.querySelector("body").removeChild(t)}}]),t}();
  </script>

  <script>
        "use strict";var px=new pixelit({from:document.getElementById("pixelitimg")}),paletteList=[[[13,43,69],[32,60,86],[84,78,104],[141,105,122],[208,129,89],[255,170,94],[255,212,163],[255,236,214]],[[48,0,48],[96,40,120],[248,144,32],[248,240,136]],[[26,28,44],[93,39,93],[177,62,83],[239,125,87],[255,205,117],[167,240,112],[56,183,100],[37,113,121],[41,54,111],[59,93,201],[65,166,246],[115,239,247],[244,244,244],[148,176,194],[86,108,134],[51,60,87]],[[44,33,55],[118,68,98],[237,180,161],[169,104,104]],[[7,5,5],[33,25,25],[82,58,42],[138,107,62],[193,156,77],[234,219,116],[160,179,53],[83,124,68],[66,60,86],[89,111,175],[107,185,182],[251,250,249],[184,170,176],[121,112,126],[148,91,40]],[[140,143,174],[88,69,99],[62,33,55],[154,99,72],[215,155,125],[245,237,186],[192,199,65],[100,125,52],[228,148,58],[157,48,59],[210,100,113],[112,55,127],[126,196,193],[52,133,157],[23,67,75],[31,14,28]],[[94,96,110],[34,52,209],[12,126,69],[68,170,204],[138,54,34],[235,138,96],[0,0,0],[92,46,120],[226,61,105],[170,92,61],[255,217,63],[181,181,181],[255,255,255]],[[21,25,26],[138,76,88],[217,98,117],[230,184,193],[69,107,115],[75,151,166],[165,189,194],[255,245,247]]],currentPalette=3,maxPalette=paletteList.length;document.addEventListener("DOMContentLoaded",(function(){document.getElementById("pixlInput").onchange=function(t){var c=new Image;c.src=URL.createObjectURL(this.files[0]),c.onload=function(){px.setFromImgSource(c.src),e()}};var e=function(){document.querySelector(".loader").classList.toggle("active"),setTimeout((function(){document.querySelector(".loader").classList.toggle("active")}),1500),px.setScale(c.value).setPalette(paletteList[currentPalette]).draw().pixelate(),n.checked&&px.convertGrayscale(),a.checked&&px.convertPalette(),r.value&&px.setMaxHeight(r.value).resizeImage(),o.value&&px.setMaxWidth(o.value).resizeImage()},t=function(){document.querySelector("#palettecolor").innerHTML="",paletteList[currentPalette].forEach((function(e){var t=document.createElement("div");t.classList="colorblock",t.style.backgroundColor="rgba(".concat(e[0],",").concat(e[1],",").concat(e[2],",1)"),document.querySelector("#palettecolor").appendChild(t)}))};t();var c=document.querySelector("#blocksize");c.addEventListener("change",(function(t){document.querySelector("#blockvalue").innerText=this.value,e()}));var n=document.querySelector("#greyscale");n.addEventListener("change",e);var a=document.querySelector("#palette");a.addEventListener("change",e);var r=document.querySelector("#maxheight");r.addEventListener("change",e);var o=document.querySelector("#maxwidth");o.addEventListener("change",e),document.querySelector("#changepalette").addEventListener("click",(function(c){currentPalette>0?currentPalette--:currentPalette=maxPalette-1,t(),a.checked=!0,e()})),document.querySelector("#downloadimage").addEventListener("click",(function(e){px.saveImage()})),e()}));

    </script>

    <!--
      <script src="https://localhost/pixelit/dist/pixelit.js"></script>
      <script src="https://localhost/pixelit/docs/assets/main.js"></script>
    -->
  <!-- loader-->
  <div class="loader">
    <div class="lds-spinner"><div></div><div></div><div></div><div></div><div></div><div></div><div></div><div></div><div></div><div></div><div></div><div></div></div>
  </div>

 </body>
 
</html>
