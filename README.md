
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>My Tiger ❤️ | From Ashi</title>
<style>
*{box-sizing:border-box}
body{
 margin:0;text-align:center;
 font-family:Georgia,serif;
 color:#a52d61;
 background:linear-gradient(145deg,#fff5fa,#ffd9e9,#fff0f6);
 overflow-x:hidden;
}
section{padding:65px 18px;min-height:65vh}
.hero{min-height:100vh;display:flex;flex-direction:column;
justify-content:center;align-items:center}
h1{font-size:clamp(40px,10vw,68px);margin:15px 0}
h2{font-size:30px}
p{line-height:1.8;font-size:17px}
.card{
 max-width:600px;margin:20px auto;padding:28px;
 background:#ffffffc9;border:1px solid white;
 border-radius:25px;
 box-shadow:0 8px 30px #d65c9020;
}
button{
 background:#e84d88;color:white;border:0;
 padding:14px 25px;border-radius:30px;
 font-size:16px;cursor:pointer;margin:12px;
}
button:hover{background:#bc3169}
.heart{font-size:55px;animation:beat 1s infinite}
@keyframes beat{50%{transform:scale(1.2)}}
.cake{font-size:100px}
#secret{display:none;font-size:20px}
.float{
 position:fixed;bottom:-40px;pointer-events:none;
 animation:up 7s linear forwards;z-index:5
}
@keyframes up{
 to{transform:translateY(-110vh) rotate(360deg);opacity:0}
}
footer{padding:30px}
</style>
</head>
<body>

<section class="hero">
 <div class="heart">💗</div>
 <p>A SPECIAL SURPRISE FOR MY LOVE</p>
 <h1>Happy Birthday<br>My Tiger 🐯</h1>
 <h2>My Baby, My Husband, My Forever ❤️</h2>
 <p>With endless love, Your Wife Ashi 💍</p>
 <button onclick="document.getElementById('welcome').scrollIntoView({behavior:'smooth'})">
 Open Your Surprise 💌
 </button>
</section>

<section id="welcome">
 <h2>Hey My Love! 🥹</h2>
 <div class="card">
  <p>Welcome to your little birthday world, Tiger!</p>
  <p>Today is all about you. I made this little surprise with so much love, just for my favourite person. ❤️</p>
  <p>You are my happiness, my smile and my forever.</p>
 </div>
</section>

<section>
 <h2>🎂 Happy Birthday Baby!</h2>
 <div class="card">
  <div class="cake" id="cake">🎂</div>
  <p>Close your eyes, make a wish and blow your candles!</p>
  <button onclick="celebrate()">Blow The Candles 🕯️</button>
  <p id="wish"></p>
 </div>
</section>

<section>
 <h2>💌 A Letter From Your Wife</h2>
 <div class="card">
  <h3>Dear My Tiger ❤️</h3>
  <p>
   Happy Birthday, my baby!
   Tum meri life ka sabse beautiful part ho.
   Tumhari smile meri favourite hai aur
   tumhara saath meri sabse pyari feeling.
  </p>
  <p>
   Main chahti hoon tumhari life hamesha
   khushiyon se bhari rahe. Tumhare har
   sapne poore hon aur tum kabhi udaas na ho.
  </p>
  <p>
   Main har janam mein tumhari hi Ashi
   banna chahti hoon. Tum mere aaj bhi ho
   aur mere har aane wale kal bhi. 💗
  </p>
  <h3>Forever Yours,<br>Your Wife Ashi 💍</h3>
 </div>
</section>

<section>
 <h2>🌸 Our Love Story</h2>
 <div class="card">
  <h3>Two Hearts, One Forever ❤️</h3>
  <p>Some people become a beautiful part of life...</p>
  <p>And some become the whole world.</p>
  <p>You are my whole world, Tiger. 🐯</p>
  <div class="heart">💕</div>
 </div>
</section>

<section>
 <h2>🎶 A Song For You</h2>
 <div class="card">
  <p>Choose a song that reminds you of us.</p>
  <input type="file" id="music" accept="audio/*">
  <br>
  <audio id="player" controls style="width:100%;margin-top:15px"></audio>
 </div>
</section>

<section>
 <h2>🎁 Your Last Surprise</h2>
 <div class="card">
  <p>Baby, there is one thing I want you to know...</p>
  <button onclick="showLove()">Open My Heart ❤️</button>
  <div id="secret">
   <div class="heart">💗</div>
   My Tiger, you are my favourite person,
   my biggest happiness and my forever love.
   <br><br>
   I want to hold your hand through every
   season of life.
   <br><br>
   Har janam mein tumhari Ashi banna hai.
   <br><br>
   I LOVE YOU SO MUCH, MY HUSBAND! 💍
   <br><br>
   Forever & Always,<br>
   YOUR WIFE ASHI 💋
  </div>
 </div>
</section>

<footer>
 Made with infinite love ❤️<br>
 ASHI ♡ TIGER<br>
 Forever & Always 💍
</footer>

<script>
function celebrate(){
 document.getElementById('cake').innerHTML='🍰✨';
 document.getElementById('wish').innerHTML=
 'Happy Birthday, My Tiger! 🎉❤️ May all your dreams come true!';
 for(let i=0;i<20;i++) hearts();
}
function showLove(){
 document.getElementById('secret').style.display='block';
 for(let i=0;i<15;i++)hearts();
}
function hearts(){
 const h=document.createElement('div');
 h.className='float';
 h.innerHTML=['💗','💕','❤️','🌸','💖'][Math.floor(Math.random()*5)];
 h.style.left=Math.random()*100+'vw';
 h.style.fontSize=(20+Math.random()*25)+'px';
 document.body.appendChild(h);
 setTimeout(()=>h.remove(),7000);
}
setInterval(hearts,900);
document.getElementById('music').addEventListener('change',function(){
 if(this.files[0]){
  const p=document.getElementById('player');
  p.src=URL.createObjectURL(this.files[0]);
  p.play();
 }
});
</script>
</body>
</html>
