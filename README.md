>Benito Cafe</title> <script src=" https://telegram.org/js/telegram-web-app.js"></script> <style> :root{--bg:#121512;--card:#1d221d;--green:#6f8f5f;--text:#f2f2ee;--muted:#9aa396} *{box-sizing:border-box;-webkit-tap-highlight-color:transparent} body{margin:0;background:var(--bg);color:var(--text);font-family:system-ui,-apple-system,Roboto,sans-serif;padding-bottom:90px} sarlavha{text-align:center;padding:14px 0 6px;font-weight:800;letter-spacing:6px;font-size:22px;color:var(--green)} sarlavha kichik {display:block;shrift-size:11px;letter-spacing:3px;color:var(--muted);shrift-weight:400} nav {position:sticky;top:0;background:var(--bg);display:flex;gap:8px;overflow-x:auto;padding:10px 12px;z-index:5} navigatsiya tugmasi {flex:none;border:0;background:var(--card);color:var(--text);padding:9px 14px;border-radius:20px;shrift-size:14px} h2 {margin:14px 14px 8px;font-size:18px;scroll-margin-top:62px} .grid {display:grid;grid-template-columns:1fr 1fr;gap:10px;padding:0 12px} .card{background:var(--card);border-radius:16px;padding:12px;display:flex;flex-direction:column;justify-content:space-between;min-height:140px} .emo{shrift-size:34px;matn-align:center} .nm{shrift-size:14px;chegara:6px 0 2px} .pr{color:var(--green);shrift-weight:700;shrift-size:14px} .row{chegara-top:8px} .add{border:0;background:var(--green);color:#10140f;width:100%;padding:9px;border-radius:12px;shrift-weight:700;shrift-size:14px} .step{display:flex;align-items:center;justify-content:space-between;width:100%} .step tugmasi{border:0;background:var(--green);color:#10140f;width:38px;height:34px;border-radius:10px;font-size:20px;font-weight:700} .step span{font-weight:700} #bar{position:fixed;left:0;right:0;bottom:0;padding:10px 12px 14px;background:linear-gradient(transparent,var(--bg) 30%)} #bar button{width:100%;border:0;background:var(--green);color:#10140f;padding:15px;border-radius:16px;font-size:16px;font-weight:800} #bar button.off{opacity:.4} #varaq{pozitsiya:fixed;left:0;right:0;top:0;bottom:0;background:rgba(0,0,0,.65);display:none;align-items:flex-end;z-index:10} #varaq.show{display:flex} .pane{background:var(--bg);width:100%;max-height:85vh;overflow:auto;border-radius:20px 20px 0 0;padding:16px} .line{display:flex;justify-content:space-between;align-items:center;padding:10px 0;border-bottom:1px qattiq #2a302a;gap:10px} .line .l{flex:1;shrift-size:14px;color:var(--muted)} .line .lb{display:block;color:var(--text)} .sum{display:flex;justify-content:space-between;padding:6px 0;color:var(--muted)} .sum.t{color:var(--text);shrift-weight:800;shrift-size:17px} .sec{display:flex;gap:10px;margin-top:14px} .sec button{flex:1;border:0;border-radius:14px;padding:14px;shrift-size:15px;shrift-weight:700} .b1{background:var(--card);color:var(--text)} .b2{background:var(--green);color:#10140f} </style> BENITOFAMILY KAFE
Savat bo'sh
<script> var tg = window.Telegram && window.Telegram.WebApp; if (tg) { tg.ready(); tg.expand(); } var YETKAZIB BERISH = 5000; var MENU = [ {n:"Hot-dog", e:"🌭", items:[["Canada",14000],["Shoxona",20000],["Retro",18000],["Qazili",32000],["Qozili kichik",26000],[",Qazi[0"assor kichik",24000],["Go'shtli",25000],["Xalapeno",20000]]}, {n:"Lavash", e:"🌯", buyumlar:[["Original",34000],["Pishloqli",37000],["Qalampir",34000],["Super",38000],["Kichik",23000]]}, {n:"Burger", e:"🍔", mahsulotlar:[["Tovuqli burger",25000],["Gam burger",25000],["Pishloqli burger",28000],["Double burger",34000],["Double cheeseburger",38000]]}, {n:"🥇", {n:"Bosh buyumlar:[["Toster",30000],["Donar",45000],["Nonkabob",35000],["Nonkabob kichik",26000],["Club sendwich",35000],["Sezar salat",30000],["Kartoshka"00ar0shka,["Kartoshka"00ar0shka,[5K] kichik",9000]]}, {n:"Nagetto", e:"🍗", elementlar:[["Nagetto" 6 talik",15000],["Nagetto 8 talik",18000],["Nagetto 18 talik",38000]]}, {n:"Choy va kofe", e:"☕", itemlar:[["Ko'k choy",4000],["Qora choy",4000],["Ko'ra choy",4000],["Limon choyi qora",8000],["Kofe malochniy",8000]]}, {n:"Ichimliklar", e:"🥤", itemlar:[["Tabiiy sharbat",15000],["Flavis katta",12000],["Flavis kichik",8000],["Family 0.0]var,["Flavis kichik",8000],["Family 0.0]var =,]4S; {}, sheetOpen = false; MENU.forEach(function(c, ci){ c.items.forEach(function(it){ ITEMS.push({n:it[0], p:it[1], e:ce}); }); }); }); }
funktsiya som(n){ return String(n).replace(/\B(?=(\d{3})+(?!\d))/g, " ") + " so'm"; }

function ctl(i){ var q = cart[ITEMS[i].n] || 0; agar (!q) '+ Qo'shish' ni qaytarsa; ' ni qaytarsa

− ' + q + ' +
'; }
var nav = document.getElementById("nav"), html = "", idx = 0; MENU.forEach(function(c, ci){ var b = document.createElement("tugma"); b.textContent = ce + "" + cn; b.onclick = function(){ document.getElementById("cat" + ci).scrollIntoView({behavior:"smooth"}); }; nav.appendChild(b); html += '

' + ce + ' ' + cn + '
'; c.items.forEach(function(it){ html += '
' + ce + '
'+ it[0] + '
' + som(it[1]) + '
'+ ctl(idx) + '
'; idx++; }); html += '
'; }); document.getElementById("menyu").innerHTML = html;
function jamul(){ var c = 0, t = 0; ITEMS.forEach(function(it){ var q = cart[it.n] || 0; c += q; t += q * it.p; }); return {c:c, t:t}; } function bar(){ var s = jamul(), b = document.getElementById("cartBtn"); if (!sc){ b.className = "off"; b.textContent = "Savat bo'sh"; } else { b.className = ""; b.textContent = "🧺 Savat · " + sc + " ta · " + som(st); } } function changed(i){ document.getElementById("c" + i).innerHTML = ctl(i); bar(); if (sheetOpen){ if (totals().c) openCart(); else closeCart(); } } funktsiya add(i){ var n = ITEMS[i].n; cart[n] = (cart[n] || 0) + 1; changed(i); } funktsiya sub(i){ var n = ITEMS[i].n; if (!cart[n]) return; cart[n]--; if (cart[n] <= 0) delete cart[n]; changed(i); }

openCart() funksiyasi { var s = jami(); agar (!sc) return; varaqOpen = rost; var h = '

🧺 Savatingiz
'; ITEMS.forEach(function(it, i){ var q = cart[it.n] || 0; agar (!q) qaytarsa; h += '
' + it.n + ' ' + som(it.p * q) + '
− ' + q + ' +
'; }); h += '
Taomlar ' + som(st) + '
'; h += '
Yetkazish ' + som(DELVERY) + '
'; h += '
Jami ' + som(st + YETKAZI) + '
'; h += '
To'lov Naqd pul
'; h += '
⬅️ Menyuga✅ Buyurtma berish
'; document.getElementById("panel").innerHTML = h; document.getElementById("varaq").className = "show"; } funktsiya closeCart(){ varaqOpen = false; document.getElementById("varaq").className = ""; } document.getElementById("cartBtn").onclick = openCart; document.getElementById("varaq").onclick = function(e){ if (e.target === this) closeCart(); };
function order(){ var items = []; Object.keys(cart).forEach(function(n){ items.push([n, cart[n]]); }); if (!items.length) return; var data = JSON.stringify({i: items}); if (tg && tg.initData) { tg.sendData(data); } else { alert("Signal rejimi (Telegramdan tashqarida):\n" + data); } } </script>
