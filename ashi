<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>For My Husband ❤️</title>
<style>
*{box-sizing:border-box}
html{scroll-behavior:smooth}
body{
 margin:0;font-family:Georgia,serif;
 background:linear-gradient(135deg,#fff0f5,#ffe0ec,#fff);
 color:#a83262;text-align:center;overflow-x:hidden;
}
section{
 min-height:100vh;padding:65px 20px;
 display:flex;flex-direction:column;
 justify-content:center;align-items:center;
}
.hero{min-height:100vh}
h1{font-size:clamp(40px,9vw,70px);margin:15px}
h2{font-size:32px}
p{line-height:1.8;font-size:17px}
button{
 background:#e75480;color:white;border:0;
 border-radius:30px;padding:14px 25px;
 font-size:16px;cursor:pointer;margin:10px;
 transition:.3s;
}
button:hover{background:#c83267;transform:scale(1.05)}
.heart{font-size:45px;animation:beat 1s infinite}
@keyframes beat{50%{transform:scale(1.3)}}
.card{
 background:#ffffffd9;padding:28px;border-radius:25px;
 max-width:650px;width:100%;margin:20px auto;
 box-shadow:0 8px 30px #e7548030;
}
.cake{font-size:110px;margin:20px}
#secret{display:none;font-size:22px;padding:20px}
.float{
 position:fixed;bottom:-30px;
 animation:rise 6s linear forwards;
 pointer-events:none;z-index:10;
}
@keyframes rise{
 to{transform:translateY(-110vh) rotate(360deg);opacity:0}
}
.balloon{
 position:fixed;bottom:-100px;
 width:45px;height:58px;border-radius:50%;
 z-index:20;pointer-events:none;
 animation:fly 4s ease-out forwards;
}
@keyframes fly{
 to{transform:translateY(-120vh) rotate(20deg);opacity:0}
}
.confetti{
 position:fixed;top:-20px;width:10px;height:14px;
 z-index:30;pointer-events:none;
 animation:fall 4s linear forwards;
}
@keyframes fall{
 to{transform:translateY(110vh) rotate(800deg)}
}
#partyMessage{
 display:none;font-size:26px;
 font-weight:bold;animation:beat 1s infinite;
}
footer{padding:30px}
</style>
</head>
<body>

<section class="hero" id="page1">
 <div class="heart">💗</div>
 <p>A LITTLE SURPRISE FOR YOU</p>
 <h1>Happy Birthday<br>My Husband ❤️</h1>
 <h2>My Baby, My Happiness ❤️</h2>
 <p>Made with endless love by your wife Ashi 💍</p>
 <button onclick="nextPage('page2')">
 Open Your Surprise 💌
 </button>
</section>

<section id="page2">
 <h2>Hey My Husband! 🥹❤️</h2>
 <div class="card">
  <div class="heart">💕</div>
  <p>Today is not an ordinary day...</p>
  <p>Because today, the most special person in my life was born!</p>
  <p>Baby, this little world is just for you. Every word and every heart is filled with my love. 💗</p>
 </div>
 <button onclick="nextPage('page3')">Next Surprise 💗 ➜</button>
</section>

<section id="page3">
 <h2>🎂 Happy Birthday Baby!</h2>
 <div class="card">
  <div class="cake" id="cake">🎂</div>
  <p>Make a wish, my love!</p>
  <button onclick="cutCake()">Cut The Cake 🎂❤️</button>
  <p id="cakeMessage"></p>
  <div id="partyMessage">🎉 HAPPY BIRTHDAY MY HUSBAND! 🎉</div>
 </div>
 <button onclick="nextPage('page4')">Next Surprise 💌 ➜</button>
</section>

<section id="page4">
 <h2>💌 A Letter For My Husband</h2>
 <div class="card">
  <div class="heart">💗</div>
  <h3>Dear My Husband,</h3>
  <p>
   Happy Birthday, my love! ❤️
   Aap meri life ka woh beautiful part ho
   jise main kabhi khona nahi chahti.
   Aapki smile meri favourite hai aur
   aapka saath meri sabse khoobsurat feeling.
  </p>
  <p>
   Main chahti hoon aapki life hamesha
   khushiyon se bhari rahe. Aapke saare
   dreams poore hon aur aap hamesha haste raho.
  </p>
  <p>
   Har birthday par main aapke saath rahun
   aur aapki har smile ki wajah banu.
  </p>
  <h3>Forever yours, Your Wife Ashi 💗</h3>
 </div>
 <button onclick="nextPage('page5')">One More Surprise 💍 ➜</button>
</section>

<section id="page5">
 <h2>💍 My Forever Promise</h2>
 <div class="card">
  <div class="heart">❤️</div>
  <p>I promise to stand beside you in every situation.</p>
  <p>To celebrate your happiness, support your dreams and hold your hand through every chapter of life.</p>
  <h3>Two Hearts, One Forever 💗</h3>
 </div>
 <button onclick="nextPage('page6')">Last Surprise 🎁 ➜</button>
</section>

<section id="page6">
 <h2>🎁 One Last Surprise!</h2>
 <div class="card">
  <p>Baby, I have something special to tell you...</p>
  <button onclick="reveal()">Open Your Secret Message ❤️</button>
  <div id="secret">
   <div class="heart">🥹❤️</div>
   You are my favourite person,
   my happiest thought and my sweetest blessing.
   <br><br>
   I LOVE YOU SO MUCH, MY HUSBAND!
   <br><br>
   Forever & Always... 💗
   <br><br>
   Yours lovingly,<br>
   YOUR WIFE ASHI 💋
  </div>
 </div>
 <button onclick="nextPage('page1')">Watch Again ❤️</button>
</section>

<footer>
 Made with ❤️ by Ashi<br>
 For her one and only Husband 💍
</footer>

<script>
function nextPage(id){
 document.getElementById(id).scrollIntoView({
  behavior:'smooth'
 });
}

function hearts(){
 const h=document.createElement('div');
 h.className='float';
 h.innerHTML=['❤️','💗','💕','🌸','💖'][
  Math.floor(Math.random()*5)
 ];
 h.style.left=Math.random()*100+'vw';
 h.style.fontSize=(15+Math.random()*25)+'px';
 document.body.appendChild(h);
 setTimeout(()=>h.remove(),6000);
}
setInterval(hearts,650);

function cutCake(){
 const cake=document.getElementById('cake');
 cake.innerHTML='🍰';
 document.getElementById('cakeMessage').innerHTML=
 'Cake cut ho gaya! Lots of love, my Husband! ❤️';
 document.getElementById('partyMessage').style.display='block';

 const colors=['#ff4f91','#ffd43b','#9b72ff',
 '#42c9c0','#ff795e','#ffb6d9'];

 for(let i=0;i<35;i++){
  const b=document.createElement('div');
  b.className='balloon';
  b.style.left=Math.random()*100+'vw';
  b.style.background=colors[i%colors.length];
  b.style.animationDelay=Math.random()*2+'s';
  document.body.appendChild(b);
  setTimeout(()=>b.remove(),6500);
 }

 for(let i=0;i<100;i++){
  const c=document.createElement('div');
  c.className='confetti';
  c.style.left=Math.random()*100+'vw';
  c.style.background=colors[i%colors.length];
  c.style.animationDelay=Math.random()*2+'s';
  document.body.appendChild(c);
  setTimeout(()=>c.remove(),6000);
 }
}

function reveal(){
 document.getElementById('secret').style.display='block';
 for(let i=0;i<25;i++)hearts();
}
</script>

</body>
</html>
