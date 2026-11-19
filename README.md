
<style>
.party-screen{
 position:fixed;inset:0;background:#ffe4ef;
 z-index:9999;display:none;overflow:hidden;
 align-items:center;justify-content:center;
 flex-direction:column;text-align:center;
}
.party-screen.show{display:flex}
.party-cake{font-size:110px;cursor:pointer}
.balloon{
 position:absolute;bottom:-150px;
 width:55px;height:70px;border-radius:50%;
 animation:fly 3s ease-out forwards;
}
.balloon:after{
 content:"";position:absolute;bottom:-22px;
 left:26px;height:25px;border-left:1px solid #bd648a;
}
@keyframes fly{
 to{transform:translateY(-120vh) rotate(20deg)}
}
.confetti{
 position:absolute;top:-20px;width:10px;height:15px;
 animation:fall 3s linear forwards;
}
@keyframes fall{
 to{transform:translateY(110vh) rotate(900deg)}
}
.cut{animation:cutcake 1s forwards}
@keyframes cutcake{
 50%{transform:scale(1.2) rotate(-10deg)}
 100%{transform:scale(.7) translateX(20px)}
}
</style>

<section style="text-align:center">
 <div class="card">
  <h2>🎂 Birthday Party Time!</h2>
  <div style="font-size:85px">🎂</div>
  <p>Baby, ready to cut your birthday cake?</p>
  <button onclick="startParty()">
   CUT THE CAKE 🎂❤️
  </button>
 </div>
</section>

<div class="party-screen" id="party">
 <div style="font-size:55px">🎉🎊🎉</div>
 <h1 style="color:#d63379">Happy Birthday!</h1>
 <h2>My Tiger 🐯❤️</h2>
 <div class="party-cake" id="partyCake">🎂</div>
 <h2>Lots of love from Ashi 💋</h2>
 <p>May your life always be full of happiness! 💗</p>
 <button onclick="closeParty()">One More Hug ❤️</button>
</div>

<script>
function startParty(){
 const party=document.getElementById('party');
 party.classList.add('show');

 const cake=document.getElementById('partyCake');
 cake.innerHTML='🍰';
 cake.classList.add('cut');

 const colors=['#ff4f91','#ffd43b','#8c72ff','#42c9c0','#ff795e'];

 for(let i=0;i<35;i++){
  const b=document.createElement('div');
  b.className='balloon';
  b.style.left=Math.random()*100+'vw';
  b.style.background=colors[i%colors.length];
  b.style.animationDelay=Math.random()*1.5+'s';
  party.appendChild(b);
 }

 for(let i=0;i<100;i++){
  const c=document.createElement('div');
  c.className='confetti';
  c.style.left=Math.random()*100+'vw';
  c.style.background=colors[i%colors.length];
  c.style.animationDelay=Math.random()*2+'s';
  party.appendChild(c);
 }
}
function closeParty(){
 document.getElementById('party').classList.remove('show');
 document.getElementById('partyCake').innerHTML='🎂';
 document.getElementById('partyCake').classList.remove('cut');
}
</script>
