<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    body {
      margin: 0;
      overflow: hidden;
      background-color: #f8c7e5; /* Soft pink background color */
    }

    #container {
      position: relative;
      width: 100vw;
      height: 100vh;
    }

    #image {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      width: 400px; /* Initial width */
      height: auto; /* Maintain aspect ratio */
      border-radius: 20px; /* Add some curves to the image */
      transition: width 0.5s ease; /* Add smooth transition effect */
    }

    #text {
      position: absolute;
      top: 130px; /* Adjust the top position */
      left: 50%;
      transform: translateX(-50%);
      font-size: 50px; /* Adjust the font size */
      color: #68025c;
    }

    .button {
      position: absolute;
      padding: 25px;
      cursor: pointer;
      background-color: #8d65ff; /* Purple background color */
      color: #fff; /* Text color */
    }

    #button1 {
      top: 80%;
      left: 40%;
      transform: translate(-50%, -50%);
    }

    #button2 {
      top: 80%;
      left: 60%;
      transform: translate(-50%, -50%);
    }
  </style>
</head>
<body>
  <div id="container">
    <div id="text">Beni seviyor musun?</div>
    <img id="image" src="C:\Users\bilge\OneDrive\Masaüstü\Screenshot 2024-01-14 195114.png" alt="Your Image">
    <div id="button1" class="button" onclick="showLove()">Evet</div>
    <div id="button2" class="button" onclick="moveButton()">Hayır</div>
  </div>

  <script>
    const image = document.getElementById('image');
    const button2 = document.getElementById('button2');

    function moveButton() {
      const maxX = window.innerWidth - button2.clientWidth;
      const maxY = window.innerHeight - button2.clientHeight;

      const newX = Math.floor(Math.random() * maxX);
      const newY = Math.floor(Math.random() * maxY);

      button2.style.left = `${newX}px`;
      button2.style.top = `${newY}px`;
    }

    function showLove() {
      // Make the image bigger
      image.style.width = '500px';

      // Create a heart emoji
      const heart = document.createElement('div');
      heart.innerHTML = '❤️';
      heart.style.position = 'absolute';
      heart.style.top = '50%';
      heart.style.left = '50%';
      heart.style.fontSize = '200px'; /* Make the heart bigger */
      heart.style.transform = 'translate(-50%, -50%)';
      heart.style.color = '#ff0000'; // Red color
      heart.style.transition = 'font-size 0.5s ease'; // Add smooth transition effect
      document.body.appendChild(heart);

      // Add the specified text
      const loveText = document.createElement('div');
      loveText.innerHTML = "BEN DE SENİ ÇOK SEVİYORUM!!";
      loveText.style.position = 'absolute';
      loveText.style.top = '65%';
      loveText.style.backgroundColor = '#fff';
      loveText.style.left = '50%';
      loveText.style.transform = 'translate(-50%, 0)';
      loveText.style.fontSize = '30px';
      loveText.style.color = '#19005e';
      document.body.appendChild(loveText);

      // Reset image size and remove the heart and text after 2 seconds
      setTimeout(() => {
        image.style.width = '400px';
        document.body.removeChild(heart);
        document.body.removeChild(loveText);
      }, 2000);
    }

    document.addEventListener('mousemove', (e) => {
      const distance = Math.hypot(e.clientX - button2.offsetLeft - button2.clientWidth / 2, e.clientY - button2.offsetTop - button2.clientHeight / 2);

      if (distance < 50) {
        moveButton();
      }
    });
  </script>
</body>
</html>
