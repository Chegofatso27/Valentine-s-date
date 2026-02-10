
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Be My Valentine?</title>
  <style>
    body {
      margin: 0;
      height: 100vh;
      overflow: hidden;
      display: flex;
      justify-content: center;
      align-items: center;
      background: linear-gradient(135deg, #ff4d6d, #ff9a9e);
      font-family: Arial, sans-serif;
      text-align: center;
    }

    .card {
      background: white;
      padding: 35px;
      border-radius: 25px;
      box-shadow: 0 15px 40px rgba(0,0,0,0.25);
      width: 90%;
      max-width: 360px;
      z-index: 2;
    }

    h1 {
      color: #ff4d6d;
      margin-bottom: 15px;
    }

    p {
      font-size: 20px;
      margin-bottom: 30px;
    }

    button {
      padding: 14px 30px;
      font-size: 18px;
      border: none;
      border-radius: 40px;
      cursor: pointer;
      position: absolute;
    }

    #yes {
      background: #ff4d6d;
      color: white;
      position: relative;
    }

    #no {
      background: #eee;
      color: #666;
      top: 20px;
      left: 20px;
      animation: shake 0.15s infinite;
    }

    @keyframes shake {
      0% { transform: translate(0); }
      25% { transform: translate(3px, -3px); }
      50% { transform: translate(-3px, 3px); }
      75% { transform: translate(3px, 3px); }
      100% { transform: translate(-3px, -3px); }
    }

    .heart {
      position: fixed;
      bottom: -20px;
      color: red;
      font-size: 20px;
      animation: floatUp linear infinite;
      opacity: 0.8;
      z-index: 1;
    }

    @keyframes floatUp {
      from {
        transform: translateY(0) scale(1);
        opacity: 1;
      }
      to {
        transform: translateY(-110vh) scale(1.5);
        opacity: 0;
      }
    }
  </style>
</head>
<body>

  <div class="card">
    <h1>Hey Khuthadzo ❤️</h1>
    <p>May I be your Valentine?</p>
    <button id="yes">Yes 😍</button>
  </div>

  <button id="no">No 🙄</button>

  <script>
    const noBtn = document.getElementById("no");

    function moveNoButton() {
      const x = Math.random() * (window.innerWidth - 100);
      const y = Math.random() * (window.innerHeight - 60);
      noBtn.style.left = x + "px";
      noBtn.style.top = y + "px";
    }

    noBtn.addEventListener("mouseover", moveNoButton);
    noBtn.addEventListener("touchstart", moveNoButton);
    noBtn.addEventListener("click", moveNoButton);

    document.getElementById("yes").addEventListener("click", () => {
      document.body.innerHTML = `
        <div style="
          height:100vh;
          display:flex;
          justify-content:center;
          align-items:center;
          flex-direction:column;
          background:linear-gradient(135deg,#ff4d6d,#ff9a9e);
          color:white;
          font-family:Arial;
          text-align:center;">
          <h1>YAY!!! 💖🥰</h1>
          <p style="font-size:22px;">
            You’re officially my Valentine ❤️<br>
            Best YES ever 😘
          </p>
        </div>
      `;
    });

    // Floating hearts generator
    function createHeart() {
      const heart = document.createElement("div");
      heart.classList.add("heart");
      heart.innerHTML = "❤️";
      heart.style.left = Math.random() * 100 + "vw";
      heart.style.fontSize = Math.random() * 20 + 15 + "px";
      heart.style.animationDuration = Math.random() * 3 + 4 + "s";

      document.body.appendChild(heart);

      setTimeout(() => {
        heart.remove();
      }, 7000);
    }

    setInterval(createHeart, 300);
  </script>

</body>
</html>

