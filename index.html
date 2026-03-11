<!DOCTYPE html>
<html lang="vi">
<head>
<meta charset="UTF-8">
<title>PhuocKhatNuoc</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<style>
*{box-sizing:border-box;font-family:Arial}
body{
  margin:0;height:100vh;
  background:radial-gradient(circle at top,#1b2a3a,#05080d);
  display:flex;justify-content:center;align-items:center
}
.container{width:360px}
.card{
  position:relative;background:#0f1722;color:#fff;
  border-radius:20px;padding:25px;
  box-shadow:0 0 25px rgba(0,255,255,.4);
  overflow:hidden
}

/* chú ý: canvas sẽ nằm trên nội dung (để tuyết rơi thấy rõ),
   nhưng pointer-events: none để không chặn tương tác */
#snow,#lightning{position:absolute;top:0;left:0;z-index:4;pointer-events:none}
.card>*:not(canvas){position:relative;z-index:2}

#title{text-align:center;font-size:32px;color:#00ffff;text-shadow:0 0 5px #0ff,0 0 20px #09f}
.status{text-align:center;font-weight:bold; margin-bottom: 10px;}
.status.inactive{color:orange}
.status.active{color:#00ff88}

/* CSS cho hệ thống Key */
.key-box{display:flex;gap:10px;margin:10px 0}
.key-box input{flex:1;padding:10px;border-radius:8px;border:none}
.key-box button{padding:10px;border:none;border-radius:8px;background:#00e676;font-weight:bold;cursor:pointer}
.expire{text-align:center;color:#00ff88;font-size:14px; margin-bottom: 10px; min-height: 16px;}

.notify{text-align:center;height:22px;font-weight:bold; margin-bottom: 10px;}

.game-select{display:flex;gap:10px;margin:10px 0 20px 0;}
.game-btn{flex:1;padding:10px;border-radius:10px;background:#222;color:#fff;border:none;cursor:pointer; font-weight:bold;}
.game-btn.active{background:#ff5722;color:#000}

.feature .item{
  display:flex;justify-content:space-between;
  align-items:center;padding:12px;
  background:#151d29;border-radius:12px;margin-bottom:8px;
  transition: 0.3s;
}

/* CSS khi chưa kích hoạt */
.locked .item{opacity:0.4; pointer-events:none;}

.switch{position:relative;width:52px;height:28px}
.switch input{opacity:0}
.slider{position:absolute;inset:0;border-radius:28px;background:#555}
.slider:before{
  content:"";position:absolute;width:22px;height:22px;left:3px;top:3px;
  background:#ccc;border-radius:50%;transition:.3s
}
.switch input:checked+.slider{
  background:linear-gradient(135deg,#00ff88,#00c853);
  box-shadow:0 0 10px rgba(0,255,136,.8)
}
.switch input:checked+.slider:before{transform:translateX(24px);background:#fff}
</style>
</head>

<body>
<div class="container">
  <div class="card" id="card">
    <canvas id="snow"></canvas>
    <canvas id="lightning"></canvas>

    <h1 id="title">PhuocKhatNuoc</h1>
    <p id="status" class="status inactive">Chưa kích hoạt</p>

    <div class="key-box" id="keyBox">
      <input id="keyInput" placeholder="Nhập key...">
      <button onclick="checkKey()">Xác nhận</button>
    </div>
    
    <p id="expireText" class="expire"></p>
    <p id="notify" class="notify"></p>

    <div class="game-select">
      <button class="game-btn active" id="btnNormal" onclick="selectGame('normal')">Free Fire Thường</button>
      <button class="game-btn" id="btnMax" onclick="selectGame('max')">Free Fire Max</button>
    </div>

    <div class="feature locked" id="features">
      <div class="item"><span>🔒 AIMLOCK</span><label class="switch"><input type="checkbox" disabled onchange="toggleFeature(this,'AIMLOCK')"><span class="slider"></span></label></div>
      <div class="item"><span>✔ EXACTLY++</span><label class="switch"><input type="checkbox" disabled onchange="toggleFeature(this,'EXACTLY++')"><span class="slider"></span></label></div>
      <div class="item"><span>⚡ OPTIMIZE</span><label class="switch"><input type="checkbox" disabled onchange="toggleFeature(this,'OPTIMIZE')"><span class="slider"></span></label></div>
      <div class="item"><span>➕ SENSITIVITY PRO</span><label class="switch"><input type="checkbox" disabled onchange="toggleFeature(this,'SENSITIVITY PRO')"><span class="slider"></span></label></div>
      <div class="item"><span>⚙ LEGIT PRO</span><label class="switch"><input type="checkbox" disabled onchange="toggleFeature(this,'LEGIT PRO')"><span class="slider"></span></label></div>
      <div class="item"><span>🛡️ Fix Rung</span><label class="switch"><input type="checkbox" disabled onchange="toggleFeature(this,'Fix Rung')"><span class="slider"></span></label></div>
      <div class="item"><span>🎯 Fix Lố</span><label class="switch"><input type="checkbox" disabled onchange="toggleFeature(this,'Fix Lố')"><span class="slider"></span></label></div>
      <div class="item"><span>🚀 Tối ưu Fps</span><label class="switch"><input type="checkbox" disabled onchange="toggleFeature(this,'Tối ưu Fps')"><span class="slider"></span></label></div>
    </div>
  </div>
</div>

<script>
/* ===== XỬ LÝ HỆ THỐNG KEY (OFFLINE) ===== */
const STORAGE_KEY = "PKN_OFFLINE_KEY";
let countdownTimer = null;

function notify(t, c="#0ff"){
  const n = document.getElementById("notify");
  n.textContent = t; 
  n.style.color = c;
  setTimeout(() => n.textContent = "", 2500);
}

// Mở khóa giao diện
function unlockUI() {
  document.getElementById("status").textContent = "Đã kích hoạt";
  document.getElementById("status").className = "status active";
  document.getElementById("features").classList.remove("locked");
  document.getElementById("keyBox").style.display = "none"; // Ẩn ô nhập key
  document.querySelectorAll("#features input").forEach(i => i.disabled = false);
}

// Khóa giao diện
function lockUI() {
  localStorage.removeItem(STORAGE_KEY);
  clearInterval(countdownTimer);
  document.getElementById("status").textContent = "Chưa kích hoạt";
  document.getElementById("status").className = "status inactive";
  document.getElementById("features").classList.add("locked");
  document.getElementById("keyBox").style.display = "flex"; // Hiện ô nhập key
  document.getElementById("expireText").textContent = "";
  document.querySelectorAll("#features input").forEach(i => { i.checked = false; i.disabled = true; });
}

// Đếm ngược thời gian
function startTimer(expireTime) {
  clearInterval(countdownTimer);
  countdownTimer = setInterval(() => {
    const timeLeft = expireTime - Date.now();
    if (timeLeft <= 0) {
      notify("Key đã hết hạn!", "#ff3333");
      return lockUI();
    }
    const days = Math.floor(timeLeft / (1000 * 60 * 60 * 24));
    const hours = Math.floor((timeLeft % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
    const minutes = Math.floor((timeLeft % (1000 * 60 * 60)) / (1000 * 60));
    const seconds = Math.floor((timeLeft % (1000 * 60)) / 1000);
    
    let timeString = "Còn lại: ";
    if (days > 0) timeString += `${days} ngày `;
    timeString += `${hours}h ${minutes}m ${seconds}s`;
    
    document.getElementById("expireText").textContent = timeString;
  }, 1000);
}

// Kiểm tra key khi bấm Xác nhận
function checkKey() {
  const keyInput = document.getElementById("keyInput").value.trim();
  
  if (!keyInput.startsWith("PhuocKhatNuoc-")) {
    return notify("Key không hợp lệ!", "#ff9800");
  }

  const daysStr = keyInput.split("-")[1];
  const days = parseInt(daysStr);

  // Chỉ chấp nhận 7, 30 hoặc 365
  if (days !== 7 && days !== 30 && days !== 365) {
    return notify("Gói Key không tồn tại!", "#ff9800");
  }

  // Tính thời gian hết hạn: Hiện tại + (Số ngày * 24h * 60p * 60s * 1000ms)
  const expireTime = Date.now() + days * 86400000;
  
  // Lưu vào localStorage
  localStorage.setItem(STORAGE_KEY, JSON.stringify({ key: keyInput, exp: expireTime }));
  
  unlockUI();
  startTimer(expireTime);
  notify("Kích hoạt thành công!", "#00ff88");
}

// Tự động kiểm tra key cũ khi tải trang
function checkSavedKey() {
  const savedData = JSON.parse(localStorage.getItem(STORAGE_KEY) || "null");
  if (savedData && savedData.exp > Date.now()) {
    unlockUI();
    startTimer(savedData.exp);
  } else {
    lockUI();
  }
}

/* ===== Xử lý Nút Chức Năng ===== */
function toggleFeature(cb,name){
  notify((cb.checked?"Bật ":"Tắt ")+name, cb.checked?"#00ff88":"#ff9800");
}

function selectGame(g){
  const btnNormal=document.getElementById("btnNormal");
  const btnMax=document.getElementById("btnMax");
  btnNormal.classList.remove("active");
  btnMax.classList.remove("active");
  (g==="normal"?btnNormal:btnMax).classList.add("active");
  notify("Đã chọn "+(g==="normal"?"Free Fire Thường":"Free Fire Max"),"#00ff88");
}

/* ===== TUYẾT RƠI VÀ SẤM SÉT ===== */
const card = document.getElementById('card');
const snow = document.getElementById('snow');
const lightning = document.getElementById('lightning');
const sx = snow.getContext('2d');
const lx = lightning.getContext('2d');

let flakes = [];
let FL_COUNT = 260; 
let snowW = 360, snowH = 520;

function resizeCanvases(){
  const rect = card.getBoundingClientRect();
  const w = Math.max(200, Math.floor(rect.width)); 
  const h = Math.max(200, Math.floor(rect.height)); 
  snowW = w; snowH = h;
  snow.width = w; snow.height = h;
  lightning.width = w; lightning.height = h;
  initFlakes();
}

function initFlakes(){
  flakes = [];
  for(let i=0;i<FL_COUNT;i++){
    flakes.push({
      x: Math.random()*snowW,
      y: Math.random()*snowH,
      r: Math.random()*3 + 1,
      v: Math.random()*1.8 + 0.6,
      sway: (Math.random()*0.6) + 0.2,
      phase: Math.random()*Math.PI*2
    });
  }
}

function drawSnow(){
  sx.clearRect(0,0,snowW,snowH);
  for(let f of flakes){
    f.phase += 0.01 + f.sway*0.003;
    f.x += Math.sin(f.phase) * f.sway; 
    f.y += f.v;
    if(f.y > snowH + 10){
      f.y = -10;
      f.x = Math.random()*snowW;
      f.v = Math.random()*1.8 + 0.6;
      f.r = Math.random()*3 + 1;
      f.sway = (Math.random()*0.6) + 0.2;
      f.phase = Math.random()*Math.PI*2;
    }
    sx.beginPath();
    sx.arc(f.x, f.y, f.r, 0, Math.PI*2);
    const alpha = 0.6 - (f.r-1)/6;
    sx.fillStyle = `rgba(255,255,255,${alpha})`;
    sx.fill();
  }
  requestAnimationFrame(drawSnow);
}

function lightningPulse(){
  if(Math.random() < 0.6) return; 
  lx.fillStyle = "rgba(255,255,255,0.12)";
  lx.fillRect(0,0,snowW,snowH);
  lx.beginPath();
  let x = snowW/2, y = 0;
  lx.moveTo(x,y);
  const seg = Math.max(6, Math.floor(snowH/60));
  for(let i=0;i<seg;i++){
    x += (Math.random()*40 - 20);
    y += (Math.random()*40 + Math.max(10, snowH/seg));
    lx.lineTo(x, Math.min(y, snowH));
  }
  lx.strokeStyle = "#9ff";
  lx.lineWidth = 2;
  lx.stroke();
  setTimeout(()=>lx.clearRect(0,0,snowW,snowH),120);
}

if (window.ResizeObserver) {
  const ro = new ResizeObserver(() => {
    resizeCanvases();
  });
  ro.observe(card);
} else {
  window.addEventListener('resize', resizeCanvases);
}

// Khởi chạy các hàm
checkSavedKey();
resizeCanvases();
drawSnow();
setInterval(lightningPulse, 2500);
</script>
</body>
</html>
