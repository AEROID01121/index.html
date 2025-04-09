<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Generator Angka PUBG Style</title>
  <link href="https://fonts.googleapis.com/css2?family=Oswald:wght@500&display=swap" rel="stylesheet">
  <style>
    body {
      margin: 0;
      background: black url('https://i.ibb.co/SDsqxzsK/404485214-1819370638475724-5901598681794553050-n-2-1024x576.jpg') no-repeat center center fixed;
      background-size: cover;
      font-family: 'Oswald', sans-serif;
      color: #FFD700;
    }

    .overlay {
      background: rgba(0, 0, 0, 0.7);
      position: absolute;
      width: 100%;
      height: 100%;
      top: 0;
      left: 0;
      z-index: 0;
    }

    .container {
      position: relative;
      text-align: center;
      padding: 100px 20px 20px;
      z-index: 1;
    }

    h1 {
      font-size: 48px;
      margin-bottom: 20px;
      text-shadow: 0 0 20px #FFD700;
      text-transform: uppercase;
    }

    .btn {
      background: #FFD700;
      border: 2px solid #000;
      padding: 20px 40px;
      font-size: 24px;
      color: #000;
      border-radius: 8px;
      cursor: pointer;
      box-shadow: 0 0 20px #FFD700;
      transition: 0.2s ease;
    }
    .btn:hover {
      background: #fff200;
      box-shadow: 0 0 25px #fff200;
    }

    .history {
      margin-top: 40px;
      display: flex;
      justify-content: center;
      flex-wrap: wrap;
      gap: 20px;
    }

    .history-card {
      background: rgba(0, 0, 0, 0.5);
      backdrop-filter: blur(6px);
      -webkit-backdrop-filter: blur(6px);
      padding: 20px;
      border-radius: 10px;
      width: 220px;
      box-shadow: 0 0 10px #FFD700;
      color: #FFD700;
      font-size: 20px;
    }

    .history-card .name {
      background-color: white;
      color: black;
      padding: 14px;
      border-radius: 8px;
      font-weight: bold;
      text-align: center;
      margin-bottom: 12px;
      box-shadow: inset 0 -1px 0 #ccc;
      text-transform: uppercase;
      font-size: 24px;
    }

    #smokeEffect {
      position: absolute;
      width: 100px;
      height: 100px;
      background: url('https://i.ibb.co/yFz9VTD/smoke.png') no-repeat center center;
      background-size: contain;
      opacity: 0;
      pointer-events: none;
      z-index: 99;
    }

    .bullet {
      position: absolute;
      width: 20px;
      height: 50px;
      background: url('https://i.ibb.co/6cQZgKj/pngwing-com.png') no-repeat center center;
      background-size: contain;
      animation: bulletFall 1s forwards;
      opacity: 1;
      z-index: 99;
      pointer-events: none;
    }

    .m416 {
      position: absolute;
      bottom: 50px;
      left: 50px;
      width: 200px;
      z-index: 1000;
      animation: gunFlash 0.5s infinite alternate;
      display: none;
    }

    .loading-bar {
      position: absolute;
      bottom: 20px;
      left: 50px;
      width: 200px;
      height: 20px;
      background: #333;
      border: 2px solid #FFD700;
      border-radius: 10px;
      overflow: hidden;
      display: none;
    }
    .loading-fill {
      height: 100%;
      width: 0%;
      background: #FFD700;
      transition: width 0.1s linear;
    }

    .sexy-girl {
      position: absolute;
      bottom: 0;
      right: 0;
      width: 250px;
      z-index: 1;
    }

    .menu-pasaran {
      position: absolute;
      top: 20px;
      left: 20px;
      z-index: 999;
    }

    .menu-pasaran select {
      padding: 12px;
      border-radius: 12px;
      border: none;
      font-size: 16px;
      font-weight: bold;
      box-shadow: 0 0 10px #FFD700;
      background: white;
      color: black;
      cursor: pointer;
    }

    @keyframes smokeAnimation {
      0% { opacity: 0; transform: scale(0.5); }
      50% { opacity: 0.5; transform: scale(1.2); }
      100% { opacity: 0; transform: scale(1.5); }
    }

    @keyframes bulletFall {
      0% { opacity: 1; transform: translateY(-100px); }
      100% { opacity: 0; transform: translateY(500px); }
    }

    @keyframes gunFlash {
      0% { filter: brightness(1); }
      100% { filter: brightness(1.5); }
    }
  </style>
</head>
<body>
  <div class="overlay"></div>
  <div id="smokeEffect"></div>
  <div id="bulletContainer"></div>
  <img src="https://i.ibb.co/MDP0WzQh/df88fue-4edc011e-423d-47dc-a70d-82d9d5c69b59.png" alt="m416" class="m416" id="m416Image">
  <div class="loading-bar" id="loadingBar"><div class="loading-fill" id="loadingFill"></div></div>
  <img src="https://i.ibb.co/7xHfv8jk/bear-dance.gif" alt="cewek seksi" class="sexy-girl">

  <div class="menu-pasaran">
    <select id="pasaranMenu" onchange="refreshPasaran(this)">
      <option selected disabled value="">MENU PASARAN</option>
      <option value="SYDNEY LOTTO">SYDNEY LOTTO</option>
      <option value="CHINA">CHINA</option>
      <option value="JAPAN">JAPAN</option>
      <option value="SINGAPORE">SINGAPORE</option>
      <option value="TAIWAN">TAIWAN</option>
      <option value="CAIRO 1">CAIRO 1</option>
      <option value="CAIRO 2">CAIRO 2</option>
    </select>
  </div>

  <div class="container">
    <h1 id="judulPasaran">GENERATOR TERPERCAYA</h1>
    <button class="btn" id="generateButton">GENERATE</button>
    <div class="history" id="history"></div>
  </div>

  <script>
    const playerNames = [
      'RAMADHAN SYAH',
      'ABDUL SETIAWAN',
      'JULIET ZEUS',
      'ADYA BRISON',
      'ALDI SIONG'
    ];

    let pasaranDipilih = false;
    let loading = false;

    function refreshPasaran(select) {
      const pasaran = select.value;
      const judul = document.getElementById('judulPasaran');
      const m416 = document.getElementById('m416Image');
      const loadingBar = document.getElementById('loadingBar');
      const loadingFill = document.getElementById('loadingFill');

      pasaranDipilih = true;
      loading = true;
      judul.innerText = `GENERATOR TERPERCAYA ${pasaran}`;
      m416.style.display = 'block';
      loadingBar.style.display = 'block';
      document.getElementById('history').innerHTML = '';

      let percent = 0;
      loadingFill.style.width = '0%';
      const interval = setInterval(() => {
        percent += 2;
        loadingFill.style.width = percent + '%';
        if (percent >= 100) {
          clearInterval(interval);
          m416.style.display = 'none';
          loadingBar.style.display = 'none';
          loading = false;
        }
      }, 40);
    }

    function showSmokeEffect(x, y) {
      const smoke = document.getElementById('smokeEffect');
      smoke.style.left = `${x - 50}px`;
      smoke.style.top = `${y - 50}px`;
      smoke.style.opacity = 1;
      smoke.style.animation = 'smokeAnimation 1s forwards';
      setTimeout(() => { smoke.style.opacity = 0; }, 1000);
    }

    function dropBullets() {
      const container = document.getElementById('bulletContainer');
      for (let i = 0; i < 5; i++) {
        const bullet = document.createElement('div');
        bullet.className = 'bullet';
        bullet.style.left = `${Math.random() * window.innerWidth}px`;
        bullet.style.top = `-50px`;
        bullet.style.animationDelay = `${i * 0.1}s`;
        container.appendChild(bullet);
        setTimeout(() => bullet.remove(), 1500);
      }
    }

    function generateNumber() {
      if (!pasaranDipilih) {
        alert('Silakan pilih pasaran terlebih dahulu!');
        return;
      }

      if (loading) {
        alert('Sedang memuat pasaran, harap tunggu...');
        return;
      }

      let historyHTML = '';
      playerNames.forEach(name => {
        const nums = Array.from({length: 4}, () => Math.floor(Math.random() * 10));
        historyHTML += `
          <div class="history-card">
            <div class="name">${name}</div>
            <div class="numbers">${nums.join(' - ')}</div>
          </div>`;
      });
      document.getElementById('history').innerHTML = historyHTML;
    }

    document.getElementById('generateButton').addEventListener('click', function(e) {
      generateNumber();
      const rect = e.target.getBoundingClientRect();
      const x = rect.left + rect.width / 2;
      const y = rect.top + rect.height / 2;
      showSmokeEffect(x, y);
      dropBullets();
    });
  </script>
</body>
</html>
