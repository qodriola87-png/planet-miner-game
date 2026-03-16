<!DOCTYPE html>
<html>
<head>
<title>Planet Miner</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<style>
body {
  margin:0;
  font-family: Arial, sans-serif;
  background:#0b0f2a;
  color:white;
  text-align:center;
}
#top-bar {
  padding:10px;
  background:#1a1f4d;
  display:flex;
  justify-content:space-between;
  align-items:center;
}
#coins { font-size:18px; margin:5px 0; }
#main-screen { position:relative; margin:20px auto; width:90%; max-width:400px; }
#mine-button { width:150px; cursor:pointer; animation:pulse 1s infinite; }
@keyframes pulse { 0%{transform:scale(1)}50%{transform:scale(1.1)}100%{transform:scale(1)} }
.menu { display:flex; justify-content:space-around; margin-top:20px; }
.menu button {
  padding:10px 20px;
  border:none;
  border-radius:8px;
  background:gold;
  color:black;
  font-weight:bold;
  cursor:pointer;
}
#popup { display:none; position:fixed; top:50%; left:50%; transform:translate(-50%,-50%);
         background:#222; padding:20px; border-radius:10px; width:80%; max-width:300px; }
#popup img { width:100%; }
#leaderboard { display:none; background:#111; margin:20px auto; padding:10px; width:90%; max-width:400px; height:200px; overflow-y:scroll; border-radius:10px; text-align:left; }
</style>
</head>
<body>

<div id="top-bar">
  <span id="coins">Coins: 0</span>
  <span id="energy">Energy: 100%</span>
</div>

<div id="main-screen">
  <img src="main_screen.png" width="100%">
  <br>
  <img id="mine-button" src="mine_button.png" onclick="mine()">
</div>

<div class="menu">
  <button onclick="showLeaderboard()">Leaderboard</button>
  <button onclick="showDailyReward()">Daily Reward</button>
  <button onclick="showWithdraw()">Withdraw</button>
</div>

<div id="popup"></div>
<div id="leaderboard">
  <h3>Leaderboard</h3>
  <ul id="leaderboard-list">
    <li>Player1: 500 coins</li>
    <li>Player2: 400 coins</li>
    <li>Player3: 350 coins</li>
  </ul>
</div>

<script>
let coins = 0;

function mine(){
  coins += 10;
  document.getElementById("coins").innerText = "Coins: " + coins;
}

function showDailyReward(){
  const popup = document.getElementById("popup");
  popup.innerHTML = '<h3>Daily Reward</h3><img src="daily_reward_popup.png"><br><button onclick="closePopup()">Claim</button>';
  popup.style.display='block';
}

function showWithdraw(){
  const popup = document.getElementById("popup");
  popup.innerHTML = '<h3>Withdraw</h3><img src="withdraw_screen.png"><br><button onclick="closePopup()">Close</button>';
  popup.style.display='block';
}

function showLeaderboard(){
  const lb = document.getElementById("leaderboard");
  lb.style.display = (lb.style.display==='none')?'block':'none';
}

function closePopup(){
  document.getElementById("popup").style.display='none';
}
</script>

</body>
</html>
