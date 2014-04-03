CORSCanvas
==========

Promosie Based~~!

```js
function getImg(url) {
  return new Promise(function(resolve, reject) {
    var img = new Image();
    img.onload = function() {
        resolve(img);
    };
    img.onerror = function() {
      reject(Error("Network Error"));
    };
    img.src = url;
  });
}

function makeCanvas(img){
  var canvas = document.createElement('canvas');
  canvas.width = img.width;
  canvas.height = img.height;
  
  return [canvas,img];
  //return Promise.resolve([canvas,img]);
}

function drawCanvas(data){
  var canvas = data[0];
  var img = data[1];
  var ctx=canvas.getContext("2d");
  ctx.drawImage(img,0,0);
  
  return canvas;
}

function showCanvas(canvas){
  document.body.appendChild(canvas);
}


var url = "http://upload.wikimedia.org/wikipedia/commons/9/9c/Image-Porkeri_001.jpg";


Promise.resolve(url)
 .then(getImg)
 .then(makeCanvas)
 .then(drawCanvas)
 .then(showCanvas)

;


```
