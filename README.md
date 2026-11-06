<!DOCTYPE html>
<html lang="uz">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no">
<title>Benito Cafe</title>
<script src="https://telegram.org/js/telegram-web-app.js"></script>
<style>
:root{--bg:#121512;--card:#1d221d;--green:#6f8f5f;--text:#f2f2ee;--muted:#9aa396}
*{box-sizing:border-box;-webkit-tap-highlight-color:transparent}
body{margin:0;background:var(--bg);color:var(--text);font-family:system-ui,-apple-system,Roboto,sans-serif;padding-bottom:90px}
header{text-align:center;padding:14px 0 6px;font-weight:800;letter-spacing:6px;font-size:22px;color:var(--green)}
header small{display:block;font-size:11px;letter-spacing:3px;color:var(--muted);font-weight:400}
nav{position:sticky;top:0;background:var(--bg);display:flex;gap:8px;overflow-x:auto;padding:10px 12px;z-index:5}
nav button{flex:none;border:0;background:var(--card);color:var(--text);padding:9px 14px;border-radius:20px;font-size:14px}
h2{margin:14px 14px 8px;font-size:18px;scroll-margin-top:62px}
.grid{display:grid;grid-template-columns:1fr 1fr;gap:10px;padding:0 12px}
.card{background:var(--card);border-radius:16px;padding:12px;display:flex;flex-direction:column;justify-content:space-between;min-height:140px}
.emo{font-size:34px;text-align:center}
.nm{font-size:14px;margin:6px 0 2px}
.pr{color:var(--green);font-weight:700;font-size:14px}
.row{margin-top:8px}
.add{border:0;background:var(--green);color:#10140f;width:100%;padding:9px;border-radius:12px;font-weight:700;font-size:14px}
.step{display:flex;align-items:center;justify-content:space-between;width:100%}
.step button{border:0;background:var(--green);color:#10140f;width:38px;height:34px;border-radius:10px;font-size:20px;font-weight:700}
.step span{font-weight:700}
#bar{position:fixed;left:0;right:0;bottom:0;padding:10px 12px 14px;background:linear-gradient(transparent,var(--bg) 30%)}
#bar button{width:100%;border:0;background:var(--green);color:#10140f;padding:15px;border-radius:16px;font-size:16px;font-weight:800}
#bar button.off{opacity:.4}
#sheet{position:fixed;left:0;right:0;top:0;bottom:0;background:rgba(0,0,0,.65);display:none;align-items:flex-end;z-index:10}
#sheet.show{display:flex}
.pane{background:var(--bg);width:100%;max-height:85vh;overflow:auto;border-radius:20px 20px 0 0;padding:16px}
.line{display:flex;justify-content:space-between;align-items:center;padding:10px 0;border-bottom:1px solid #2a302a;gap:10px}
.line .l{flex:1;font-size:14px;color:var(--muted)}
.line .l b{display:block;color:var(--text)}
.sum{display:flex;justify-content:space-between;padding:6px 0;color:var(--muted)}
.sum.t{color:var(--text);font-weight:800;font-size:17px}
.sec{display:flex;gap:10px;margin-top:14px}
.sec button{flex:1;border:0;border-radius:14px;padding:14px;font-size:15px;font-weight:700}
.b1{background:var(--card);color:var(--text)}
.b2{background:var(--green);color:#10140f}
</style>
</head>
<body>
<header>BENITO<small>FAMILY CAFE</small></header>
<nav id="nav"></nav>
<div id="menu"></div>
<div id="bar"><button id="cartBtn" class="off">Savat bo'sh</button></div>
<div id="sheet"><div class="pane" id="pane"></div></div>
<script>
var tg = window.Telegram && window.Telegram.WebApp;
if (tg) { tg.ready(); tg.expand(); }
var DELIVERY = 5000;
var MENU = [
 {n:"Hot-dog", e:"🌭", items:[["Canada",14000],["Shoxona",20000],["Retro",18000],["Qazili",32000],["Qazili kichik",26000],["Qazi assorti",30000],["Qazi assorti kichik",24000],["Go'shtli",25000],["Xalapeno",20000]]},
 {n:"Lavash", e:"🌯", items:[["Original",34000],["Pishloqli",37000],["Qalampir",34000],["Super",38000],["Kichik",23000]]},
 {n:"Burger", e:"🍔", items:[["Chicken burger",25000],["Gam burger",25000],["Cheese burger",28000],["Double burger",34000],["Double cheeseburger",38000]]},
 {n:"Boshqa", e:"🥪", items:[["Toster",30000],["Donar",45000],["Nonkabob",35000],["Nonkabob kichik",26000],["Club sandwich",35000],["Sezar salat",30000],["Kartoshka fri katta",15000],["Kartoshka fri kichik",9000]]},
 {n:"Nagetto", e:"🍗", items:[["Nagetto 6 talik",15000],["Nagetto 8 talik",18000],["Nagetto 18 talik",38000]]},
 {n:"Choy va kofe", e:"☕", items:[["Ko'k choy",4000],["Qora choy",4000],["Limon choy",6000],["Kofe qora",8000],["Kofe malochniy",8000]]},
 {n:"Ichimliklar", e:"🥤", items:[["Tabiiy sharbat",15000],["Flavis katta",12000],["Flavis kichik",8000],["Family 0.5",4000]]}
];
var ITEMS = [], cart = {}, sheetOpen = false;
MENU.forEach(function(c, ci){ c.items.forEach(function(it){ ITEMS.push({n:it[0], p:it[1], e:c.e}); }); });

function som(n){ return String(n).replace(/\B(?=(\d{3})+(?!\d))/g, " ") + " so'm"; }

function ctl(i){
  var q = cart[ITEMS[i].n] || 0;
  if (!q) return '<button class="add" onclick="add(' + i + ')">+ Qo\'shish</button>';
  return '<div class="step"><button onclick="sub(' + i + ')">−</button><span>' + q + '</span><button onclick="add(' + i + ')">+</button></div>';
}

var nav = document.getElementById("nav"), html = "", idx = 0;
MENU.forEach(function(c, ci){
  var b = document.createElement("button");
  b.textContent = c.e + " " + c.n;
  b.onclick = function(){ document.getElementById("cat" + ci).scrollIntoView({behavior:"smooth"}); };
  nav.appendChild(b);
  html += '<h2 id="cat' + ci + '">' + c.e + ' ' + c.n + '</h2><div class="grid">';
  c.items.forEach(function(it){
    html += '<div class="card"><div class="emo">' + c.e + '</div><div><div class="nm">' + it[0] + '</div><div class="pr">' + som(it[1]) + '</div></div><div class="row" id="c' + idx + '">' + ctl(idx) + '</div></div>';
    idx++;
  });
  html += '</div>';
});
document.getElementById("menu").innerHTML = html;

function totals(){
  var c = 0, t = 0;
  ITEMS.forEach(function(it){ var q = cart[it.n] || 0; c += q; t += q * it.p; });
  return {c:c, t:t};
}
function bar(){
  var s = totals(), b = document.getElementById("cartBtn");
  if (!s.c){ b.className = "off"; b.textContent = "Savat bo'sh"; }
  else { b.className = ""; b.textContent = "🧺 Savat · " + s.c + " ta · " + som(s.t); }
}
function changed(i){
  document.getElementById("c" + i).innerHTML = ctl(i);
  bar();
  if (sheetOpen){ if (totals().c) openCart(); else closeCart(); }
}
function add(i){ var n = ITEMS[i].n; cart[n] = (cart[n] || 0) + 1; changed(i); }
function sub(i){ var n = ITEMS[i].n; if (!cart[n]) return; cart[n]--; if (cart[n] <= 0) delete cart[n]; changed(i); }

function openCart(){
  var s = totals();
  if (!s.c) return;
  sheetOpen = true;
  var h = '<h2 style="margin:0 0 8px">🧺 Savatingiz</h2>';
  ITEMS.forEach(function(it, i){
    var q = cart[it.n] || 0;
    if (!q) return;
    h += '<div class="line"><div class="l"><b>' + it.n + '</b>' + som(it.p * q) + '</div><div style="width:120px"><div class="step"><button onclick="sub(' + i + ')">−</button><span>' + q + '</span><button onclick="add(' + i + ')">+</button></div></div></div>';
  });
  h += '<div class="sum"><span>Taomlar</span><span>' + som(s.t) + '</span></div>';
  h += '<div class="sum"><span>Yetkazish</span><span>' + som(DELIVERY) + '</span></div>';
  h += '<div class="sum t"><span>Jami</span><span>' + som(s.t + DELIVERY) + '</span></div>';
  h += '<div class="sum"><span>To\'lov</span><span>Naqd pul</span></div>';
  h += '<div class="sec"><button class="b1" onclick="closeCart()">⬅️ Menyuga</button><button class="b2" onclick="order()">✅ Buyurtma berish</button></div>';
  document.getElementById("pane").innerHTML = h;
  document.getElementById("sheet").className = "show";
}
function closeCart(){ sheetOpen = false; document.getElementById("sheet").className = ""; }
document.getElementById("cartBtn").onclick = openCart;
document.getElementById("sheet").onclick = function(e){ if (e.target === this) closeCart(); };

function order(){
  var items = [];
  Object.keys(cart).forEach(function(n){ items.push([n, cart[n]]); });
  if (!items.length) return;
  var data = JSON.stringify({i: items});
  if (tg && tg.initData) { tg.sendData(data); }
  else { alert("Sinov rejimi (Telegramdan tashqarida):\n" + data); }
}
</script>
</body>
</html>
