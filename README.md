<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8" />
  <title>Включение камеры</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      margin-top: 50px;
    }
    video {
      border: 2px solid #4a90e2;
      border-radius: 10px;
      width: 80%;
      max-width: 600px;
    }
    button {
      padding: 10px 20px;
      font-size: 18px;
      margin-top: 20px;
      cursor: pointer;
      border-radius: 8px;
      border: none;
      background-color: #4a90e2;
      color: white;
    }
  </style>
</head>
<body>

<h1>Включить камеру</h1>
<video id="video" autoplay playsinline></video>
<br />
<button id="startBtn">Включить камеру</button>

<script>
  const video = document.getElementById('video');
  const startBtn = document.getElementById('startBtn');

  startBtn.addEventListener('click', async () => {
    try {
      const stream = await navigator.mediaDevices.getUserMedia({ video: true, audio: false });
      video.srcObject = stream;
      startBtn.style.display = 'none';
    } catch (err) {
      alert('Ошибка доступа к камере: ' + err.message);
    }
  });
</script>

</body>
</html>
