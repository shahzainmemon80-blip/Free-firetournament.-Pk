<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>FF Tournaments 2026 - Sukkur</title>
<style>
  *{margin:0;padding:0;box-sizing:border-box;font-family:'Poppins',sans-serif}
  body{background: linear-gradient(135deg,#000,#001f3f,#003366); color:#fff; line-height:1.6; min-height:100vh}
  header{background:rgba(0,0,0,0.8); padding:20px; text-align:center; border-bottom:3px solid #00aaff; display:flex; justify-content:space-between; align-items:center; flex-wrap:wrap}
.logo{width:180px; height:auto; filter: drop-shadow(0 0 15px #FFD700)}
  header h1{font-size:2rem; color:#00aaff; text-shadow:2px 2px #000}
 .user-info{font-size:0.9rem; color:#00ff88}
.container{max-width:1100px; margin:auto; padding:20px}
.card{background:rgba(0,0,0,0.5); padding:20px; border-radius:15px; margin:20px 0; border:1px solid #00aaff; backdrop-filter:blur(10px)}
.btn{display:inline-block; background:#0077ff; color:#fff; padding:12px 25px; border-radius:8px; text-decoration:none; font-weight:bold; transition:0.3s; border:none; cursor:pointer; width:100%}
.btn:hover{background:#00aaff; color:#000}
.btn-danger{background:#ff3333}
.btn-danger:hover{background:#ff5555}
.btn:disabled{background:#555; cursor:not-allowed}
  form input, form select{width:100%; padding:12px; margin:8px 0; border-radius:8px; border:1px solid #0077ff; outline:none; background:#111; color:#fff}
.prize{font-size:1.8rem; color:#00aaff; font-weight:bold}
.payment-box{display:grid; grid-template-columns:repeat(auto-fit,minmax(200px,1fr)); gap:15px; margin-top:15px}
.payment-card{background:#000; padding:15px; border-radius:10px; border:2px solid #0077ff; text-align:center}
.account{font-size:1.2rem; color:#00ff88; font-weight:bold}
.help{font-size:0.85rem; opacity:0.8; margin-top:5px}
.room-box{background:#000; padding:20px; border-radius:10px; border:2px dashed #00aaff; text-align:center; margin-top:10px}
.blink{animation: blink 1s infinite}
  @keyframes blink{0%,50%,100%{opacity:1} 25%,75%{opacity:0.3}}
.wallet-check{background:#000; padding:20px; border-radius:15px; border:2px solid #00ff88; margin:20px 0}
.balance-box{display:grid; grid-template-columns:repeat(3,1fr); gap:10px; text-align:center; margin-top:15px}
.bal-card{background:#111; padding:15px; border-radius:10px; border:1px solid #0077ff}
.bal-card h3{color:#00aaff; font-size:0.9rem}
.bal-card p{color:#00ff88; font-size:1.5rem; font-weight:bold}
.admin-panel{background:rgba(255,215,0,0.1); border:2px solid #FFD700}
.reg-list table{width:100%; border-collapse:collapse; margin-top:15px}
.reg-list th,.reg-list td{border:1px solid #0077ff; padding:8px; text-align:center; font-size:0.9rem}
.reg-list th{background:#0077ff; color:#000}
.auth-box{max-width:450px; margin:50px auto}
.tab-buttons{display:flex; gap:10px; margin-bottom:20px}
.tab-btn{flex:1; background:#222; border:2px solid #0077ff}
.tab-btn.active{background:#0077ff}
.error{color:#ff3333; margin-top:10px; display:none}
.success{color:#00ff88; margin-top:10px; display:none}
.hidden{display:none}
  @media(max-width:768px){.balance-box{grid-template-columns:1fr};.reg-list table{font-size:0.7rem}; header{flex-direction:column; gap:10px}}
</style>
</head>
<body>

<header>
  <div>
    <img src="logo.png" alt="FF Tournament Logo" class="logo">
    <h1>🔥 FF CHAMPIONSHIP 2026 🔥</h1>
    <p>Sukkur, Sindh</p>
  </div>
  <div id="userHeader" class="hidden">
    <p class="user-info">Welcome: <span id="userName"></span></p>
    <button class="btn btn-danger" onclick="logout()" style="width:auto; padding:8px 20px; margin-top:5px">Logout</button>
  </div>
</header>

<div class="container">

  <!-- AUTH SECTION -->
  <div id="authSection">
    <div class="card auth-box">
      <div class="tab-buttons">
        <button class="btn tab-btn active" onclick="showTab('login')">Login</button>
        <button class="btn tab-btn" onclick="showTab('register')">Create Account</button>
      </div>

      <!-- LOGIN FORM -->
      <div id="loginTab">
        <h2>🔒 Login</h2>
        <input type="email" id="loginEmail" placeholder="Gmail" required>
        <input type="password" id="loginPassword" placeholder="Password" required>
        <button class="btn" onclick="login()">Login</button>
        <p class="error" id="loginError">غلط Gmail یا Password!</p>
      </div>

      <!-- REGISTER FORM -->
      <div id="registerTab" class="hidden">
        <h2>📝 Create Account</h2>
        <input type="text" id="regName" placeholder="Full Name" required>
        <input type="email" id="regEmail" placeholder="Gmail" required>
        <input type="text" id="regWhatsApp" placeholder="WhatsApp Number" required>
        <input type="password" id="regPassword" placeholder="Password" required>
        <input type="password" id="regConfirmPassword" placeholder="Confirm Password" required>
        <button class="btn" onclick="register()">Account بنائیں</button>
        <p class="error" id="regError"></p>
        <p class="success" id="regSuccess">اکاؤنٹ بن گیا! اب Login کریں</p>
      </div>
    </div>
  </div>

  <!-- MAIN SITE - LOGIN کے بعد شو ہوگا -->
  <div id="mainSite" class="hidden">

    <!-- ADMIN ROOM PANEL -->
    <div class="card admin-panel">
      <h2>⚙️ Admin: Room Details Update</h2>
      <input type="text" id="roomIdInput" placeholder="Room ID ڈالیں">
      <input type="text" id="roomPassInput" placeholder="Room Password ڈالیں">
      <button class="btn" onclick="updateRoom()">Room Details Update کریں</button>
      <p class="help">یہ صرف آپ کے لیے ہے۔ Update کے بعد سب کو شو ہو جائے گا</p>
    </div>

    <!-- WALLET BALANCE SECTION -->
    <div class="card wallet-check">
      <h2>💰 اپنا Wallet Balance چیک کریں</h2>
      <p class="help">اپنا WhatsApp نمبر ڈالیں اور Balance دیکھیں</p>
      <input type="text" id="checkNumber" placeholder="مثال: 03160000001">
      <button class="btn" onclick="checkBalance()">Balance Check کریں</button>
      <div id="balanceResult" style="display:none">
        <div class="balance-box">
          <div class="bal-card"><h3>کل ڈپازٹ</h3><p id="totalDeposit">0 PKR</p></div>
          <div class="bal-card"><h3>کل خرچ</h3><p id="totalSpent" style="color:#ff4500">0 PKR</p></div>
          <div class="bal-card"><h3>بقیہ بیلنس</h3><p id="remainingBal">0 PKR</p></div>
        </div>
      </div>
    </div>

    <!-- 50 PLAYER TOURNAMENT -->
    <div class="card">
      <h2>🔥 50 PLAYERS SOLO TOURNAMENT 🔥</h2>
      <p class="prize">Entry Fee: 50 PKR</p>
      <p>کل سلاٹس: 50 | <b style="color:#00ff88">بقیہ سلاٹس: <span id="slotsLeft">50</span></b></p>
      <p style="color:#00ff88; margin-top:10px">Total Prize Pool: 2,000 PKR</p>
      <ul style="margin-top:10px">
        <li>🥇 1st Place: 1000 PKR</li>
        <li>🥈 2nd Place: 750 PKR</li>
        <li>🥉 3rd Place: 250 PKR</li>
      </ul>
    </div>

    <div class="card" id="room">
      <h2 class="blink">🎮 ROOM DETAILS</h2>
      <div class="room-box" id="roomDisplay">
        <p style="font-size:1.3rem; color:#00aaff; font-weight:bold">Room ID: <span id="roomId">Wait...</span></p>
        <p style="font-size:1.3rem; color:#00aaff; font-weight:bold">Password: <span id="roomPass">Wait...</span></p>
        <p style="font-size:1.1rem; margin-top:10px; color:#ffaa00">Admin اپڈیٹ کا انتظار کریں</p>
      </div>
    </div>

    <div class="card">
      <h2>💳 Payment - EasyPaisa</h2>
      <div class="payment-box">
        <div class="payment-card">
          <h3>EasyPaisa</h3>
          <p class="account">03160374038</p>
          <p>Account Name: Muhammad Farooque</p>
        </div>
      </div>
    </div>

    <div class="card" id="register">
      <h2>📝 Team/Player Registration</h2>
      <form onsubmit="sendToWhatsApp(); return false;">
        <input type="text" id="team" placeholder="Team Name / Player Name" required>
        <input type="text" id="captain" placeholder="Captain Name" required>
        <input type="text" id="whatsapp" placeholder="WhatsApp Number" required>

        <select id="wallettype" required>
          <option value="">Prize Wallet Type</option>
          <option value="EasyPaisa">EasyPaisa</option>
        </select>
        <input type="text" id="wallet" placeholder="Your EasyPaisa Wallet Number" required>
        <p class="help">جیتنے پر prize اسی نمبر پر بھیجا جائے گا</p>

        <select id="pmethod" required>
          <option value="">Payment Method</option>
          <option value="EasyPaisa">EasyPaisa</option>
        </select>
        <input type="number" id="amount" placeholder="Deposit Amount - 50" value="50" min="50" max="50" readonly required>
        <input type="url" id="screenshot" placeholder="Payment Screenshot Link" required>
        <input type="text" id="p1" placeholder="Player 1 UID + IGN" required>
        <input type="text" id="p2" placeholder="Player 2 UID + IGN">
        <input type="text" id="p3" placeholder="Player 3 UID + IGN">
        <input type="text" id="p4" placeholder="Player 4 UID + IGN">
        <button class="btn" type="submit" id="submitBtn">50 PKR Pay کر کے Register کریں</button>
      </form>
    </div>

    <!-- REGISTRATION LIST -->
    <div class="card reg-list">
      <h2>📋 Registered Teams List</h2>
      <table id="regTable">
        <thead>
          <tr><th>#</th><th>Team Name</th><th>Captain</th><th>WhatsApp</th></tr>
        </thead>
        <tbody id="regBody"></tbody>
      </table>
    </div>

  </div>
</div>

<script>
// DATA STORAGE
let users = JSON.parse(localStorage.getItem('users')) || [];
let currentUser = JSON.parse(localStorage.getItem('currentUser')) || null;
let walletData = JSON.parse(localStorage.getItem('walletData')) || {
  "03160000001": {deposit: 1000, spent: 0}, "03160000002": {deposit: 1000, spent: 0},
  "03160000003": {deposit: 1000, spent: 0}, "03160000004": {deposit: 1000, spent: 0},
  "03160000005": {deposit: 1000, spent: 0}
};
let slotsLeft = parseInt(localStorage.getItem('slotsLeft')) || 50;
let registrations = JSON.parse(localStorage.getItem('registrations')) || [];
let roomDetails = JSON.parse(localStorage.getItem('roomDetails')) || {id: "Wait...", pass: "Wait..."};

// ON LOAD
checkAuthState();
document.getElementById('slotsLeft').innerText = slotsLeft;
document.getElementById('roomId').innerText = roomDetails.id;
document.getElementById('roomPass').innerText = roomDetails.pass;
loadRegList();

// AUTH FUNCTIONS
function showTab(tab){
  document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
  document.getElementById('loginTab').classList.add('hidden');
  document.getElementById('registerTab').classList.add('hidden');

  if(tab === 'login'){
    document.querySelector('.tab-btn').classList.add('active');
    document.getElementById('loginTab').classList.remove('hidden');
  } else {
    document.querySelectorAll('.tab-btn')[1].classList.add('active');
    document.getElementById('registerTab').classList.remove('hidden');
  }
}

function register(){
  let name = document.getElementById('regName').value;
  let email = document.getElementById('regEmail').value;
  let whatsapp = document.getElementById('regWhatsApp').value;
  let pass = document.getElementById('regPassword').value;
  let confirmPass = document.getElementById('regConfirmPassword').value;

  document.getElementById('regError').style.display = 'none';

  if(pass!== confirmPass){
    document.getElementById('regError').innerText = "Password match نہیں کر رہا!";
    document.getElementById('regError').style.display = 'block';
    return;
  }

  if(users.find(u => u.email === email)){
    document.getElementById('regError').innerText = "یہ Gmail پہلے سے رجسٹر ہے!";
    document.getElementById('regError').style.display = 'block';
    return;
  }

  users.push({name, email, whatsapp, password: pass});
  localStorage.setItem('users', JSON.stringify(users));

  document.getElementById('regSuccess').style.display = 'block';
  document.getElementById('registerTab').querySelector('form')?.reset();
  setTimeout(() => showTab('login'), 1500);
}

function login(){
  let email = document.getElementById('loginEmail').value;
  let pass = document.getElementById('loginPassword').value;

  let user = users.find(u => u.email === email && u.password === pass);

  if(user){
    currentUser = user;
    localStorage.setItem('currentUser', JSON.stringify(user));
    checkAuthState();
  } else {
    document.getElementById('loginError').style.display = 'block';
  }
}

function logout(){
  currentUser = null;
  localStorage.removeItem('currentUser');
  checkAuthState();
}

function checkAuthState(){
  if(currentUser){
    document.getElementById('authSection').classList.add('hidden');
    document.getElementById('mainSite').classList.remove('hidden');
    document.getElementById('userHeader').classList.remove('hidden');
    document.getElementById('userName').innerText = currentUser.name;
  } else {
    document.getElementById('authSection').classList.remove('hidden');
    document.getElementById('mainSite').classList.add('hidden');
    document.getElementById('userHeader').classList.add('hidden');
  }
}

// TOURNAMENT FUNCTIONS
function updateRoom(){
  let rid = document.getElementById('roomIdInput').value;
  let rpass = document.getElementById('roomPassInput').value;
  if(rid && rpass){
    roomDetails = {id: rid, pass: rpass};
    localStorage.setItem('roomDetails', JSON.stringify(roomDetails));
    document.getElementById('roomId').innerText = rid;
    document.getElementById('roomPass').innerText = rpass;
    alert("Room Details Update ہو گئیں!");
  } else {
    alert("Room ID اور Password دونوں ڈالیں");
  }
}

function checkBalance(){
  let num = document.getElementById('checkNumber').value;
  let data = walletData[num];
  if(data){
    let remaining = data.deposit - data.spent;
    document.getElementById('totalDeposit').innerText = data.deposit + " PKR";
    document.getElementById('totalSpent').innerText = data.spent + " PKR";
    document.getElementById('remainingBal').innerText = remaining + " PKR";
    document.getElementById('balanceResult').style.display = 'block';
  } else {
    alert("یہ نمبر ہمارے ریکارڈ میں نہیں ملا!");
  }
}

function loadRegList(){
  let tbody = document.getElementById('regBody');
  tbody.innerHTML = "";
  registrations.forEach((reg, i) => {
    tbody.innerHTML += `<tr><td>${i+1}</td><td>${reg.team}</td><td>${reg.captain}</td><td>${reg.whatsapp}</td></tr>`;
  });
}

function sendToWhatsApp(){
  if(slotsLeft <= 0){
    alert("سوری! 50 سلاٹس فل ہو چکے ہیں۔");
    return;
  }

  let team = document.getElementById('team').value;
  let captain = document.getElementById('captain').value;
  let num = document.getElementById('whatsapp').value;
  let amount = parseInt(document.getElementById('amount').value);

  // Balance Check اور Deduct
  if(walletData[num]){
    let remaining = walletData[num].deposit - walletData[num].spent;
    if(remaining < amount){
      alert("آپ کے Wallet میں Balance کم ہے! 50 PKR چاہیے۔");
      return;
    }
    walletData[num].spent += amount;
    localStorage.setItem('walletData', JSON.stringify(walletData));
  } else {
    alert("یہ نمبر Wallet میں نہیں ہے۔ پہلے Balance add کروائیں: 03160374038");
    return;
  }

  // Slot کم کرو
  slotsLeft--;
  localStorage.setItem('slotsLeft', slotsLeft);
  document.getElementById('slotsLeft').innerText = slotsLeft;

  // Registration List میں ایڈ کرو
  registrations.push({team, captain, whatsapp: num});
  localStorage.setItem('registrations', JSON.stringify(registrations));
  loadRegList();

  let wallettype = document.getElementById('wallettype').value;
  let wallet = document.getElementById('wallet').value;
  let pmethod = document.getElementById('pmethod').value;
  let screenshot = document.getElementById('screenshot').value;
  let p1 = document.getElementById('p1').value;
  let p2 = document.getElementById('p2').value;
  let p3 = document.getElementById('p3').value;
  let p4 = document.getElementById('p4').value;

  let message = `🔥 NEW 50P REGISTRATION 🔥%0A%0A` +
                `By: ${currentUser.name} - ${currentUser.email}%0A` +
                `Team: ${team}%0A` +
                `Captain: ${captain}%0A` +
                `WhatsApp: ${num}%0A` +
                `Prize Wallet: ${wallettype} - ${wallet}%0A` +
                `Payment: ${pmethod} - ${amount} PKR%0A` +
                `Screenshot: ${screenshot}%0A%0A` +
                `Players:%0A1. ${p1}%0A2. ${p2}%0A3. ${p3}%0A4. ${p4}`;

  let adminNumber = "923160374038";
  window.open(`https://wa.me/${adminNumber}?text=${message}`, '_blank');
  alert(`Registration ہو گئی! 50 PKR آپ کے Balance سے کٹ گئے۔ بقیہ سلاٹس: ${slotsLeft}`);

  document.getElementById('register').querySelector('form').reset();
  document.getElementById('amount').value = 50;

  if(slotsLeft == 0){
    document.getElementById('submitBtn').disabled = true;
    document.getElementById('submitBtn').innerText = "Slots Full";
  }
}
</script>

</body>
</html>
