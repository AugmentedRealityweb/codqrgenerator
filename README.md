<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Cod QR din HTML</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
      margin: 0;
    }
    #qr-container {
      margin-top: 20px;
      display: none; /* Ascuns inițial */
    }
    button {
      padding: 10px 20px;
      font-size: 16px;
      cursor: pointer;
    }
  </style>
</head>
<body>
  <h1>Generare Cod QR</h1>
  <button id="generate-btn">Apasă</button>
  <div id="qr-container">
    <h3>Scanează codul QR:</h3>
    <canvas id="qrcode"></canvas>
  </div>

  <script src="https://cdn.jsdelivr.net/npm/qrcode/build/qrcode.min.js"></script>
  <script>
    // Referințe la elemente
    const generateBtn = document.getElementById('generate-btn');
    const qrContainer = document.getElementById('qr-container');
    const qrCodeCanvas = document.getElementById('qrcode');

    // Funcția care generează codul QR
    generateBtn.addEventListener('click', () => {
      const currentURL = window.location.href; // Link-ul paginii curente
      qrCodeCanvas.innerHTML = ''; // Golește canvas-ul pentru a regenera codul QR
      QRCode.toCanvas(qrCodeCanvas, currentURL, { width: 200 }, (error) => {
        if (error) {
          console.error('Eroare la generarea codului QR:', error);
        } else {
          qrContainer.style.display = 'block'; // Afișează codul QR
        }
      });
    });
  </script>
</body>
</html>
