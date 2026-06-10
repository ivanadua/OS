# OS
#Snoopsawg's personalised OS
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Display Webcam Stream</title>
    <style>
      @font-face {
        font-family: "Headfont";
        src: url("/Users/moana/Downloads/pixelated-elegance-font/PixelatedEleganceRegular-ovawB.ttf") format("opentype");
      }

      body {
        background-color: #000000;
        background-image: radial-gradient(circle at top, rgba(28, 32, 64, 0.35), rgba(0, 0, 0, 0.95) 60%);
        color: rgb(255, 255, 255);
        font-family: "Headfont", Arial, sans-serif;
        text-align: left;
        position: absolute;
        left: 20px;
        top: 2px;
      }

      #container {
        margin: 0px auto;
        width: 700px;
        height: 500px;
         border: 5px solid rgba(107, 132, 255, 0.9);
         box-shadow: 0 0 18px rgba(107, 132, 255, 0.78), 0 0 44px rgba(53, 77, 255, 0.42), inset 0 0 24px rgba(0, 0, 0, 0.75);
        position: relative;
      }

      #videoElement {
        width: 700px;
        height: 500px;
        background-color: #000000;
         filter: saturate(4.4) contrast(2.1) hue-rotate(250deg) brightness(1.03) grayscale(0.12) drop-shadow(0 0 10px rgba(105, 145, 255, 0.48));
      }

      #overlay {
        position: absolute;
        inset: 0;
        background:
          linear-gradient(rgba(0, 0, 0, 0.18) 50%, rgba(255, 255, 255, 0.04) 50%),
          linear-gradient(90deg, rgba(40, 50, 120, 0.10), rgba(70, 95, 235, 0.07), rgba(10, 10, 10, 0.16));
        background-size: 100% 6px, 100% 100%;
        mix-blend-mode: screen;
        opacity: 0.7;
        pointer-events: none;
      }

      #overlay::before {
        content: "";
        position: absolute;
        inset: 0;
        background:
          radial-gradient(circle at 20% 20%, rgba(95, 130, 255, 0.38), transparent 24%),
          radial-gradient(circle at 80% 30%, rgba(70, 105, 240, 0.30), transparent 22%),
          radial-gradient(circle at 50% 75%, rgba(190, 210, 255, 0.16), transparent 26%);
        mix-blend-mode: screen;
      }
    </style>
  </head>
  <body>
    <h1 style="color: rgb(147, 120, 244); font-size: 5em;">Robosnoop</h1>
    <p style="position:absolute; left: 20px; top: 125px;">visualising project handy</p>

    <div id="container">
      <video autoplay playsinline id="videoElement"></video>
      <div id="overlay"></div>
    </div>

    <script>
      const video = document.querySelector("#videoElement");

      navigator.mediaDevices
        .getUserMedia({ video: true })
        .then(function (stream) {
          video.srcObject = stream;
        })
        .catch(function (error) {
          console.error("Whoopsie:", error);
        });
    </script>
  </body>
</html>
