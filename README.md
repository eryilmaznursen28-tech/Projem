# Projem
<!DOCTYPE html>
<html lang="tr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Aydoğan Genç Doğum Günü</title>
<style>
  body, html {
    margin:0;
    padding:0;
    width:100%;
    height:100%;
    font-family: Arial, sans-serif;
    overflow:hidden;
    background: linear-gradient(to top, #87ceeb, #fdfdfd);
    display:flex;
    justify-content:center;
    align-items:center;
  }
  #startScreen, #balloonScreen, #noteScreen {
    position:absolute;
    width:100%;
    height:100%;
    display:flex;
    justify-content:center;
    align-items:center;
    flex-direction:column;
    transition: all 0.8s;
  }
  #startScreen button {
    padding: 15px 30px;
    font-size: 1.5em;
    border:none;
    border-radius:10px;
    background: #ff4d6d;
    color:white;
    cursor:pointer;
  }
  .balloon {
    position:absolute;
    bottom:-120px;
    width:70px;
    height:90px;
    border-radius:50%;
    display:flex;
    justify-content:center;
    align-items:center;
    font-weight:bold;
    color:white;
    font-size:14px;
    text-align:center;
    pointer-events:none;
  }
  #noteScreen {
    background: linear-gradient(to bottom, #ffe6e6, #ffd6d6);
    display:none;
    flex-direction:column;
    text-align:center;
    padding:20px;
  }
  #noteScreen h2 {
    font-size:2em;
    color:#d6336c;
  }
  #noteScreen p {
    margin-top:20px;
    font-size:1.2em;
    color:#333;
  }
</style>
</head>
<body>

<div id="startScreen">
  <button onclick="startAnimation()">Buraya Bas 🎉</button>
</div>

<div id="balloonScreen"></div>

<div id="noteScreen">
  <h2>🎊 Doğum Günün Kutlu Olsun Aydoğan Genç! 🎂</h2>
  <p>Nice mutlu, sağlıklı, başarı dolu yıllar dilerim! Bu özel gününde kalbinden geçen her şey gerçek olsun. 💖</p>
</div>

<script>
const balloonScreen = document.getElementById('balloonScreen');
const startScreen = document.getElementById('startScreen');
const noteScreen = document.getElementById('noteScreen');

function startAnimation() {
  startScreen.style.display='none';
  balloonScreen.style.display='block';
  
  const messages = "İyi ki doğdun Aydoğan Genç".split(' ');
  const totalBalloons = messages.length;
  let balloons = [];
  
  for(let i=0;i<totalBalloons;i++){
    let b = document.createElement('div');
    b.className='balloon';
    b.style.left = (10 + i*15) + 'vw';
    b.style.background = `hsl(${i*50},70%,60%)`;
    b.innerText = messages[i];
    balloonScreen.appendChild(b);
    balloons.push(b);
  }
  
  let index=0;
  let interval = setInterval(()=>{
    if(index>=balloons.length){
      clearInterval(interval);
      setTimeout(()=>showNote(),1000);
      return;
    }
    animateBalloon(balloons[index]);
    index++;
  }, 600);
}

function animateBalloon(balloon){
  let duration = 8000 + Math.random()*3000;
  balloon.animate([
    {transform: 'translateY(0px)', opacity:1},
    {transform: `translateY(-120vh)`, opacity:0.9}
  ], {duration: duration, easing:'ease-out'});
}

function showNote(){
  balloonScreen.style.display='none';
  noteScreen.style.display='flex';
}
</script>

</body>
</html>
