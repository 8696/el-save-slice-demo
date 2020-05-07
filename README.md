# el-save-slice-demo

将指定元素保存为图片Demo

```html
<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport"
          content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title></title>
</head>
<body>

<div id="test"
     style="width: 600px;border: 1px solid #006c9d;display: flex;flex-direction: column;align-items: center;justify-content: center">
    <h1>content item 1</h1>
    <h2>content item 2</h2>
    <h3>content item 3</h3>
    <h4>content item 4</h4>
    <img src="./img.png" alt="" style="margin-bottom: 20px">
</div>
<div id="download">
    <button>Save</button>
</div>
</body>
<script src="./js/jquery.min.js"></script>
<script src="./js/canvas2image.js"></script>
<script src="./js/html2canvas.min.js"></script>
<script type="text/javascript">


  document.querySelector('#download button').addEventListener('click', function () {
    // 指定 #test 元素
    html2canvas(document.querySelector('#test'), {
      scale: 2
      // dpi: 1024
    }).then(canvas => {

      let imgData = Canvas2Image.saveAsPNG(canvas, true).getAttribute('src');
      saveFile(imgData, new Date().getTime());

    }).catch(err => {
      alert(err.toString());
    });

  });

  function saveFile(data, saveFileName) {
    let saveLink = document.createElementNS('http://www.w3.org/1999/xhtml', 'a');
    saveLink.href = data;
    saveLink.download = saveFileName;
    let event = document.createEvent('MouseEvents');
    event.initMouseEvent('click', true, false, window, 0, 0, 0, 0, 0, false, false, false, false, 0, null);
    saveLink.dispatchEvent(event);
  }

</script>
</html>

```
