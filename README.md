<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Romantic Page</title>
<style>
  /* General styles */
  body {
    margin: 0;
    font-family: 'Arial', sans-serif;
    background-color: #ffe6f0;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    overflow: hidden;
  }

  /* Container for everything */
  .container {
    text-align: center;
    position: relative;
  }

  /* Floating hearts animation */
  .heart {
    position: absolute;
    color: #ff4d88;
    font-size: 1.5rem;
    animation: float 5s linear infinite;
    opacity: 0.8;
  }

  @keyframes float {
    0% { transform: translateY(0) scale(1); opacity: 0.8;}
    50% { opacity: 1; }
    100% { transform: translateY(-600px) scale(1.2); opacity: 0; }
  }

  /* Teddy image */
  .teddy {
    width: 150px;
    margin-bottom: 20px;
  }

  /* Main text */
  .text {
    font-size: 2rem;
    color: #ff3366;
    margin-bottom: 30px;
  }

  /* Buttons */
  .btn {
    padding: 12px 25px;
    margin: 0 10px;
    font-size: 1.2rem;
    border: none;
    cursor: pointer;
    transition: all 0.3s ease;
    border-radius: 25px;
  }

  .btn-ah {
    background: linear-gradient(45deg, #ff99cc, #ff3366);
    color: white;
    border: none;
  }

  .btn-la {
    background: none;
    border: 2px solid #ff3366;
    color: #ff3366;
    position: relative;
  }

  /* Hover effect for La button to move */
  .btn-la:hover {
    transform: translateX(calc(50vw - 50%));
  }

  /* Response text */
  .response {
    font-size: 1.8rem;
    color: #ff1a75;
    margin-top: 20px;
  }

  /* Responsive */
  @media(max-width:600px){
    .text { font-size: 1.5rem; }
    .btn { font-size: 1rem; padding: 10px 20px; }
    .teddy { width: 120px; }
  }
</style>
</head>
<body>

<div class="container">
  <!-- Teddy illustration -->
  <img src="https://i.ibb.co/3rXfH9c/teddy.png" alt="Teddy" class="teddy">

  <!-- Main text -->
  <div class="text">wach katbghini?</div>

  <!-- Buttons -->
  <button class="btn btn-ah">Ah</button>
  <button class="btn btn-la">La</button>

  <!-- Response -->
  <div class="response"></div>
</div>

<!-- Floating hearts -->
<script>
  const container = document.querySelector('.container');
  for(let i=0; i<20; i++){
    const heart = document.createElement('div');
    heart.classList.add('heart');
    heart.style.left = Math.random() * window.innerWidth + 'px';
    heart.style.animationDuration = (3 + Math.random() * 3) + 's';
    heart.innerHTML = '❤️';
    container.appendChild(heart);
  }

  // Button interactions
  const btnAh = document.querySelector('.btn-ah');
  const btnLa = document.querySelector('.btn-la');
  const response = document.querySelector('.response');

  btnAh.addEventListener('click', () => {
    response.textContent = 'Ana tanbghik bzzaf❤️';
  });

  // Move "La" button randomly on hover
  btnLa.addEventListener('mouseenter', () => {
    const x = Math.random() * (window.innerWidth - btnLa.offsetWidth);
    const y = Math.random() * (window.innerHeight - btnLa.offsetHeight);
    btnLa.style.transform = `translate(${x - btnLa.offsetLeft}px, ${y - btnLa.offsetTop}px)`;
  });
</script>

</body>
</html># romantics.html
