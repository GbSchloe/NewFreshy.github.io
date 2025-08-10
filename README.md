<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Freshy.Services</title>
<style>
  /* Base & Reset */
  * {
    box-sizing: border-box;
  }
  body, html {
    margin: 0; padding: 0;
    height: 100%;
    background: #0a0a14;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    color: #ccc;
    overflow-x: hidden;
    position: relative;
  }

  /* Background floating particles */
  #particles {
    position: fixed;
    top: 0; left: 0;
    width: 100vw;
    height: 100vh;
    pointer-events: none;
    z-index: 0;
  }

  /* Header */
  h1 {
    font-size: 3.5rem;
    margin-top: 2rem;
    text-align: center;
    color: #a64dff;
    text-shadow:
      0 0 10px #a64dff,
      0 0 20px #9147ff,
      0 0 30px #7a39ff,
      0 0 40px #6e2fff;
    animation: pulseGlow 3s ease-in-out infinite;
    user-select: none;
  }

  @keyframes pulseGlow {
    0%, 100% {
      text-shadow:
        0 0 10px #a64dff,
        0 0 20px #9147ff,
        0 0 30px #7a39ff,
        0 0 40px #6e2fff;
      color: #a64dff;
    }
    50% {
      text-shadow:
        0 0 20px #c27aff,
        0 0 30px #b06eff,
        0 0 40px #9c65ff,
        0 0 50px #9147ff;
      color: #c27aff;
    }
  }

  /* Store container */
  .store {
    max-width: 1100px;
    margin: 3rem auto 5rem;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 30px;
    padding: 0 1rem;
    position: relative;
    z-index: 1;
  }

  /* Each product card */
  .item {
    background: #1a1a2e;
    border-radius: 15px;
    width: 280px;
    padding: 25px 20px 35px;
    box-shadow:
      0 0 15px #9147ff88,
      0 0 40px #a64dffbb;
    border: 2px solid #7a39ff;
    color: #eee;
    opacity: 0;
    transform: translateY(40px);
    transition: box-shadow 0.3s ease;
  }

  .item.visible {
    opacity: 1;
    transform: translateY(0);
    transition: opacity 0.7s ease, transform 0.7s ease;
  }

  .item:hover {
    box-shadow:
      0 0 25px #c27affcc,
      0 0 60px #c27affdd;
    cursor: pointer;
  }

  .item h2 {
    font-size: 1.8rem;
    margin-bottom: 10px;
    color: #ffcc00;
    text-shadow:
      0 0 8px #ffd966,
      0 0 14px #ffeb3b;
    user-select: none;
  }

  .item p {
    font-size: 1rem;
    line-height: 1.4;
    color: #ddd;
    min-height: 60px;
    user-select: none;
  }

  /* Buy Now button */
  .buy-btn {
    margin-top: 20px;
    background: linear-gradient(45deg, #9147ff, #c27aff);
    border: none;
    border-radius: 8px;
    padding: 12px 30px;
    font-size: 1.1rem;
    font-weight: 600;
    color: white;
    text-shadow: 0 0 8px #b66cff;
    box-shadow:
      0 0 10px #9147ff,
      0 0 20px #c27aff;
    cursor: pointer;
    transition:
      transform 0.25s ease,
      box-shadow 0.6s ease;
    user-select: none;
  }

  .buy-btn:hover {
    transform: scale(1.1);
    box-shadow:
      0 0 20px #ffaeff,
      0 0 35px #d497ff,
      0 0 50px #ff9eff;
  }

  /* Responsive adjustments */
  @media (max-width: 900px) {
    .item {
      width: 80vw;
    }
  }

  /* Footer */
  footer {
    text-align: center;
    color: #666;
    font-size: 14px;
    margin-bottom: 25px;
    user-select: none;
    position: relative;
    z-index: 1;
  }
</style>
</head>
<body>

<h1>Freshy.Services</h1>

<div class="store" id="store">
  <div class="item">
    <h2>Vector</h2>
    <p>High-Quallity undetected external, made perfectly for major games such as fallen survival. </p>
    <button class="buy-btn" onclick="window.location.href='https://www.paypal.com/checkoutnow?placeholder'">Buy Now</button>
  </div>
  <div class="item">
    <h2>Matrix</h2>
    <p>Full Undetected external so many working features for all games.</p>
    <button class="buy-btn" onclick="window.location.href='https://www.paypal.com/checkoutnow?placeholder'">Buy Now</button>
  </div>
  <div class="item">
    <h2>Fallen Account Legit</h2>
    <p>High-quality fully legit fallen alt accounts.</p>
    <button class="buy-btn" onclick="window.location.href='https://www.paypal.com/checkoutnow?placeholder'">Buy Now</button>
  </div>
</div>

<footer>&copy; 2025 Freshy.Services — All rights reserved.</footer>

<canvas id="particles"></canvas>

<script>
  // Scroll-triggered animation for product cards
  const items = document.querySelectorAll('.item');

  const observer = new IntersectionObserver(entries => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.classList.add('visible');
      }
    });
  }, {
    threshold: 0.3
  });

  items.forEach(item => observer.observe(item));

  // Floating glowing particles background
  const canvas = document.getElementById('particles');
  const ctx = canvas.getContext('2d');
  let width, height;
  let particlesArray;

  function init() {
    resize();
    particlesArray = [];
    const particleCount = 80;

    for (let i = 0; i < particleCount; i++) {
      particlesArray.push(new Particle());
    }

    animate();
  }

  function resize() {
    width = window.innerWidth;
    height = window.innerHeight;
    canvas.width = width;
    canvas.height = height;
  }

  window.addEventListener('resize', () => {
    resize();
  });

  class Particle {
    constructor() {
      this.x = Math.random() * width;
      this.y = Math.random() * height;
      this.size = 1 + Math.random() * 2;
      this.speedX = (Math.random() - 0.5) * 0.3;
      this.speedY = (Math.random() - 0.5) * 0.3;
      this.alpha = 0.1 + Math.random() * 0.3;
      this.color = `rgba(198, 115, 255, ${this.alpha})`;
      this.life = 0;
      this.maxLife = 300 + Math.random() * 200;
    }

    update() {
      this.x += this.speedX;
      this.y += this.speedY;
      this.life++;

      if (this.life > this.maxLife) {
        this.x = Math.random() * width;
        this.y = Math.random() * height;
        this.life = 0;
        this.alpha = 0.1 + Math.random() * 0.3;
        this.color = `rgba(198, 115, 255, ${this.alpha})`;
      }

      // wrap around screen edges
      if (this.x < 0) this.x = width;
      if (this.x > width) this.x = 0;
      if (this.y < 0) this.y = height;
      if (this.y > height) this.y = 0;
    }

    draw() {
      ctx.beginPath();
      ctx.shadowColor = '#c473ff';
      ctx.shadowBlur = 12;
      ctx.fillStyle = this.color;
      ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
      ctx.fill();
    }
  }

  function animate() {
    ctx.clearRect(0, 0, width, height);
    particlesArray.forEach(p => {
      p.update();
      p.draw();
    });
    requestAnimationFrame(animate);
  }

  init();
</script>

</body>
</html>
