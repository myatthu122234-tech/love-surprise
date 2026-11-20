
<!DOCTYPE html>
<html lang="my">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>For My Love 💗</title>
<style>
*{box-sizing:border-box}
body{
 margin:0;min-height:100vh;overflow:hidden;
 display:flex;align-items:center;justify-content:center;
 text-align:center;font-family:sans-serif;color:#fff;
 background:linear-gradient(135deg,#ff8fbd,#b84d91,#663c83);
}
.card{
 width:90%;max-width:410px;padding:30px 18px;
 border:1px solid #ffffff66;border-radius:30px;
 background:#ffffff25;backdrop-filter:blur(12px);
 box-shadow:0 10px 40px #5b174e55;
 z-index:2;animation:appear .8s;
}
@keyframes appear{
 from{opacity:0;transform:scale(.75)}
 to{opacity:1;transform:scale(1)}
}
.heart{font-size:65px;animation:beat 1s infinite}
@keyframes beat{50%{transform:scale(1.2)}}
h1{font-size:27px;color:#fff0f7}
p{font-size:18px;line-height:1.8}
.buttons{
 display:flex;justify-content:center;align-items:center;
 gap:12px;margin-top:25px;min-height:65px;
}
button{
 border:0;border-radius:30px;padding:13px 25px;
 font-size:18px;font-weight:bold;cursor:pointer;
 transition:transform .3s;
}
.yes{background:#ff287f;color:white;box-shadow:0 5px 20px #ff287f77}
.no{background:#fff;color:#b84d91}
#final{display:none}
#final h1{font-size:30px}
.kiss{font-size:32px;line-height:1.8;animation:appear 1s}
.floating{
 position:fixed;bottom:-40px;pointer-events:none;
 animation:float linear forwards;z-index:1;
}
@keyframes float{
 to{transform:translateY(-115vh) rotate(360deg);opacity:0}
}
</style>
</head>
<body>

<div class="card" id="card">
 <div class="heart">💗</div>
 <h1 id="title">မမရေ ❤️</h1>
 <p id="question">မမရေ မောင့်ကို ချစ်လား။ 🥺</p>
 <div class="buttons">
  <button class="yes" id="yes" onclick="chooseYes()">YES ❤️</button>
  <button class="no" id="no" onclick="chooseNo()">NO 💔</button>
 </div>
</div>

<div class="card" id="final">
 <div class="heart">💖</div>
 <h1>ချစ်တယ်နော် မရေ ❤️</h1>
 <p>မောင့်ကို လက်ခံပေးလို့ ကျေးဇူးတင်ပါတယ်။</p>
 <p>မမနဲ့အတူ အမှတ်တရလေးတွေ အများကြီး ဖန်တီးချင်တယ်။ 💍</p>
 <div class="kiss">😘😘😘😘😘<br>😘 အာဘွား 😘<br>😘😘😘😘😘</div>
 <h2>မောင် ❤️ မမ</h2>
</div>

<script>
let step=0;
let yesSize=1;
const questions=[
 "မမရေ မောင့်ကို ချစ်လား။ 🥺",
 "မောင့်ကို ယူမှာလား မမရေ။ 💍",
 "မောင့်ကို ယူဖို့ အခု YES လေးနှိပ်ရင် အတည်ဖြစ်ပါပြီနော်။ 💗"
];

function chooseNo(){
 yesSize=Math.min(yesSize+0.22,2.5);
 document.getElementById("yes").style.transform=
 "scale("+yesSize+")";
 const no=document.getElementById("no");
 no.style.transform="scale("+Math.max(.25,1-step*.18)+")";
 no.innerText=["NO 🙈","တကယ်လား 🥺","ဟင့်အင်း 😭","မနှိပ်နဲ့တော့နော် 💗"][Math.min(step,3)];
}

function chooseYes(){
 step++;
 if(step<3){
  document.getElementById("question").innerText=questions[step];
  yesSize=1;
  document.getElementById("yes").style.transform="scale(1)";
  document.getElementById("no").style.transform="scale(1)";
  document.getElementById("no").innerText="NO 💔";
 }else{
  document.getElementById("card").style.display="none";
  document.getElementById("final").style.display="block";
  for(let i=0;i<35;i++)setTimeout(createHeart,i*100);
 }
}

function createHeart(){
 const h=document.createElement("div");
 h.className="floating";
 h.innerText=["💗","💕","😘","💖","🌸"][Math.floor(Math.random()*5)];
 h.style.left=Math.random()*100+"vw";
 h.style.fontSize=(20+Math.random()*25)+"px";
 h.style.animationDuration=(4+Math.random()*4)+"s";
 document.body.appendChild(h);
 setTimeout(()=>h.remove(),8500);
}
setInterval(createHeart,500);
</script>
</body>
</html>
