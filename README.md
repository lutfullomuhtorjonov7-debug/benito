<!DOCTYPE html>
<html lang="uz">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="theme-color" content="#121512">

<title>Benito Cafe</title>

<script src="https://telegram.org/js/telegram-web-app.js"></script>

<style>
:root {
  --bg:#121512;
  --card:#1d221d;
  --green:#8da878;
  --text:#f2f2ee;
  --muted:#9aa396;
  --border:#303830;
}

* {
  box-sizing:border-box;
  -webkit-tap-highlight-color:transparent;
}

body {
  margin:0;
  background:var(--bg);
  color:var(--text);
  font-family:system-ui,Arial,sans-serif;
  padding-bottom:100px;
}

header {
  text-align:center;
  padding:24px 10px 15px;
}

.logo {
  font-size:28px;
  font-weight:900;
  letter-spacing:6px;
  color:var(--green);
}

.subtitle {
  font-size:10px;
  letter-spacing:4px;
  color:var(--muted);
  margin-top:5px;
}

.banner {
  margin:10px 12px 18px;
  padding:20px;
  border-radius:18px;
  background:linear-gradient(135deg,#293529,#172018);
  border:1px solid var(--border);
}

.banner h2 {
  margin:0 0 7px;
  font-size:21px;
}

.banner p {
  color:var(--muted);
  font-size:13px;
  margin:0;
}

nav {
  position:sticky;
  top:0;
  z-index:5;
  display:flex;
  gap:8px;
  overflow-x:auto;
  padding:12px;
  background:var(--bg);
  scrollbar-width:none;
}

nav button {
  flex:none;
  border:1px solid var(--border);
  background:var(--card);
  color:var(--text);
  padding:10px 15px;
  border-radius:20px;
  font-size:13px;
}

nav button.active {
  background:var(--green);
  color:#10140f;
}

h2.category {
  margin:20px 14px 12px;
  font-size:19px;
  scroll-margin-top:70px;
}

.grid {
  display:grid;
  grid-template-columns:repeat(2,minmax(0,1fr));
  gap:11px;
  padding:0 12px;
}

.card {
  background:var(--card);
  border:1px solid var(--border);
  border-radius:17px;
  overflow:hidden;
  min-width:0;
}

.food-image {
  height:115px;
  display:flex;
  align-items:center;
  justify-content:center;
  font-size:65px;
  background:linear-gradient(135deg,#293329,#202720);
}

.food-info {
  padding:11px;
}

.food-name {
  font-size:14px;
  font-weight:700;
  min-height:38px;
}

.price {
  color:var(--green);
  font-size:15px;
  font-weight:800;
  margin:7px 0;
}

.add {
  width:100%;
  border:0;
  border-radius:11px;
  padding:10px 5px;
  background:var(--green);
  color:#10140f;
  font-weight:800;
  font-size:13px;
}

.counter {
  display:flex;
  justify-content:space-between;
  align-items:center;
  gap:8px;
}

.counter button {
  border:0;
  width:35px;
  height:34px;
  border-radius:10px;
  background:var(--green);
  color:#10140f;
  font-size:20px;
  font-weight:800;
}

.counter span {
  font-weight:800;
}

#bar {
  position:fixed;
  bottom:0;
  left:0;
  right:0;
  padding:12px;
  background:linear-gradient(transparent,var(--bg) 25%);
  z-index:8;
}

#cartBtn {
  width:100%;
  border:0;
  border-radius:15px;
  padding:16px;
  background:var(--green);
  color:#10140f;
  font-size:16px;
  font-weight:900;
}

#cartBtn.off {
  opacity:.45;
}

#modal {
  position:fixed;
  inset:0;
  background:#000a;
  display:none;
  align-items:flex-end;
  z-index:20;
}

#modal.show {
  display:flex;
}

.panel {
  width:100%;
  max-height:88vh;
  overflow-y:auto;
  background:var(--bg);
  border-radius:22px 22px 0 0;
  padding:20px 15px 30px;
}

.panel h2 {
  margin:0 0 15px;
}

.cart-item {
  display:flex;
  align-items:center;
  justify-content:space-between;
  gap:10px;
  padding:12px 0;
  border-bottom:1px solid var(--border);
}

.cart-item-name {
  flex:1;
  font-size:14px;
  font-weight:600;
}

.cart-item-price {
  color:var(--green);
  font-size:13px;
}

.cart-controls {
  display:flex;
  align-items:center;
  gap:9px;
}

.cart-controls button {
  width:30px;
  height:30px;
  border:0;
  border-radius:8px;
  background:var(--green);
  font-weight:900;
}

.summary {
  margin-top:18px;
}

.summary div {
  display:flex;
  justify-content:space-between;
  padding:7px 0;
  color:var(--muted);
}

.summary .total {
  color:var(--text);
  font-size:19px;
  font-weight:900;
  border-top:1px solid var(--border);
  margin-top:8px;
  padding-top:14px;
}

.payment {
  margin-top:20px;
  padding:14px;
  background:var(--card);
  border:1px solid var(--border);
  border-radius:13px;
}

.payment label {
  font-size:14px;
}

.actions {
  display:flex;
  gap:10px;
  margin-top:20px;
}

.actions button {
  flex:1;
  padding:15px 5px;
  border:0;
  border-radius:13px;
  font-weight:800;
  font-size:14px;
}

.back {
  background:var(--card);
  color:var(--text);
}

.order {
  background:var(--green);
  color:#10140f;
}

.empty {
  text-align:center;
  padding:35px 10px;
  color:var(--muted);
}

footer {
  text-align:center;
  padding:30px 10px;
  color:var(--muted);
  font-size:12px;
}
</style>
</head>

<body>

<header>
  <div class="logo">BENITO</div>
  <div class="subtitle">FAMILY CAFE</div>
</header>

<div class="banner">
  <h2>Benito Cafe'ga xush kelibsiz! 🍔</h2>
  <p>Sevimli taomlaringizni tanlang va buyurtma bering.</p>
</div>

<nav id="nav"></nav>

<main id="menu"></main>

<footer>
  BENITO FAMILY CAFE<br>
  Mazali taomlar — yaxshi kayfiyat!
</footer>

<div id="bar">
  <button id="cartBtn" class="off">🧺 Savat bo'sh</button>
</div>

<div id="modal">
  <div class="panel" id="panel"></div>
</div>

<script>

// TELEGRAM
const tg = window.Telegram?.WebApp;

if (tg) {
  tg.ready();
  tg.expand();
}

// SOZLAMALAR
const DELIVERY = 5000;

// MAHSULOTLAR
const MENU = [

{
 name:"Hot-dog",
 emoji:"🌭",
 items:[
  ["Kanada",14000],
  ["Shoxona",20000],
  ["Retro",18000],
  ["Qazili",32000],
  ["Qozili kichik",26000],
  ["Go'shtli",25000],
  ["Xalapeno",20000]
 ]
},

{
 name:"Lavash",
 emoji:"🌯",
 items:[
  ["Original",34000],
  ["Pishloqli",37000],
  ["Qalampir",34000],
  ["Super",38000],
  ["Kichik",23000]
 ]
},

{
 name:"Burger",
 emoji:"🍔",
 items:[
  ["Tovuqli burger",25000],
  ["Gam burger",25000],
  ["Pishloqli burger",28000],
  ["Double burger",34000],
  ["Double cheeseburger",38000]
 ]
},

{
 name:"Bosh taomlar",
 emoji:"🍽️",
 items:[
  ["Toster",30000],
  ["Donar",45000],
  ["Nonkabob",35000],
  ["Nonkabob kichik",26000],
  ["Club sandwich",35000],
  ["Sezar salat",30000],
  ["Kartoshka fri",12000],
  ["Kartoshka fri kichik",9000]
 ]
},

{
 name:"Nagget",
 emoji:"🍗",
 items:[
  ["Nagget 6 talik",15000],
  ["Nagget 8 talik",18000],
  ["Nagget 18 talik",38000]
 ]
},

{
 name:"Choy va kofe",
 emoji:"☕",
 items:[
  ["Ko'k choy",4000],
  ["Qora choy",4000],
  ["Limon choyi qora",8000],
  ["Kofe malochniy",8000]
 ]
},

{
 name:"Ichimliklar",
 emoji:"🥤",
 items:[
  ["Tabiiy sharbat",15000],
  ["Flavis katta",12000],
  ["Flavis kichik",8000]
 ]
}

];

// MAHSULOTLAR RO'YXATI
const PRODUCTS = [];

MENU.forEach((category,index)=>{
 category.items.forEach((item)=>{
  PRODUCTS.push({
   name:item[0],
   price:item[1],
   emoji:category.emoji,
   category:index
  });
 });
});

// SAVAT
let cart = {};
let sheetOpen = false;

// SO'M FORMAT
function money(number){
 return number.toLocaleString("uz-UZ")+" so'm";
}

// SAVAT MIQDORI
function quantity(name){
 return cart[name] || 0;
}

// HISOBLASH
function totals(){
 let count=0;
 let subtotal=0;

 PRODUCTS.forEach(item=>{
  let q=quantity(item.name);
  count+=q;
  subtotal+=q*item.price;
 });

 return {
  count,
  subtotal,
  total:subtotal+(count>0?DELIVERY:0)
 };
}

// MAHSULOT TUGMASI
function productButton(item){

 let q=quantity(item.name);

 if(!q){
  return `<button class="add" onclick="addItem('${escapeName(item.name)}')">+ Qo'shish</button>`;
 }

 return `
 <div class="counter">
  <button onclick="removeItem('${escapeName(item.name)}')">−</button>
  <span>${q}</span>
  <button onclick="addItem('${escapeName(item.name)}')">+</button>
 </div>
 `;
}

// MATNNI XAVFSIZ UZATISH
function escapeName(name){
 return name.replace(/\\/g,"\\\\").replace(/'/g,"\\'");
}

// MENYUNI CHIZISH
function renderMenu(){

 const nav=document.getElementById("nav");
 const menu=document.getElementById("menu");

 nav.innerHTML="";
 menu.innerHTML="";

 MENU.forEach((category,index)=>{

  let button=document.createElement("button");
  button.textContent=category.emoji+" "+category.name;

  button.onclick=()=>{
   document.getElementById("cat"+index)
   .scrollIntoView({behavior:"smooth"});
  };

  nav.appendChild(button);

  let html=`
  <h2 class="category" id="cat${index}">
   ${category.emoji} ${category.name}
  </h2>
  <div class="grid">
  `;

  category.items.forEach(item=>{

   const product=PRODUCTS.find(p=>p.name===item[0]);

   html+=`
   <div class="card">
    <div class="food-image">${category.emoji}</div>

    <div class="food-info">
     <div class="food-name">${product.name}</div>
     <div class="price">${money(product.price)}</div>
     <div id="btn-${PRODUCTS.indexOf(product)}">
      ${productButton(product)}
     </div>
    </div>
   </div>
   `;

  });

  html+="</div>";

  menu.innerHTML+=html;

 });

}

// SAVAT TUGMASI
function updateButtons(){

 PRODUCTS.forEach((item,index)=>{
  let element=document.getElementById("btn-"+index);

  if(element){
   element.innerHTML=productButton(item);
  }
 });

 updateBar();
}

// SAVAT PANELI
function updateBar(){

 const t=totals();
 const btn=document.getElementById("cartBtn");

 if(t.count===0){
  btn.className="off";
  btn.textContent="🧺 Savat bo'sh";
 }else{
  btn.className="";
  btn.textContent=
   "🧺 Savat · "+t.count+" ta · "+money(t.total);
 }

}

// QO'SHISH
function addItem(name){

 cart[name]=(cart[name]||0)+1;

 updateButtons();

 if(sheetOpen) openCart();
}

// KAMAYTIRISH
function removeItem(name){

 if(!cart[name]) return;

 cart[name]--;

 if(cart[name]<=0){
  delete cart[name];
 }

 updateButtons();

 if(sheetOpen) openCart();
}

// SAVATNI OCHISH
function openCart(){

 const t=totals();

 if(!t.count) return;

 sheetOpen=true;

 let html=`
 <h2>🧺 Savatingiz</h2>
 `;

 PRODUCTS.forEach(item=>{

  const q=quantity(item.name);

  if(!q) return;

  html+=`
  <div class="cart-item">

   <div>
    <div class="cart-item-name">${item.name}</div>
    <div class="cart-item-price">${money(item.price*q)}</div>
   </div>

   <div class="cart-controls">
    <button onclick="removeItem('${escapeName(item.name)}')">−</button>
    <span>${q}</span>
    <button onclick="addItem('${escapeName(item.name)}')">+</button>
   </div>

  </div>
  `;

 });

 html+=`
 <div class="summary">

  <div>
   <span>Taomlar</span>
   <span>${money(t.subtotal)}</span>
  </div>

  <div>
   <span>Yetkazib berish</span>
   <span>${money(DELIVERY)}</span>
  </div>

  <div class="total">
   <span>Jami</span>
   <span>${money(t.total)}</span>
  </div>

 </div>

 <div class="payment">
  <label>💵 To'lov turi: <b>Naqd pul</b></label>
 </div>

 <div class="actions">
  <button class="back" onclick="closeCart()">⬅️ Menyu</button>
  <button class="order" onclick="sendOrder()">Buyurtma berish ✅</button>
 </div>
 `;

 document.getElementById("panel").innerHTML=html;
 document.getElementById("modal").classList.add("show");

}

// SAVATNI YOPISH
function closeCart(){

 sheetOpen=false;

 document.getElementById("modal")
 .classList.remove("show");

}

// BUYURTMA YUBORISH
function sendOrder(){

 const t=totals();

 if(!t.count) return;

 const items=PRODUCTS
 .filter(item=>quantity(item.name)>0)
 .map(item=>({
  name:item.name,
  price:item.price,
  quantity:quantity(item.name)
 }));

 const order={
  type:"benito_order",
  payment:"Naqd pul",
  delivery:DELIVERY,
  subtotal:t.subtotal,
  total:t.total,
  items:items
 };

 const data=JSON.stringify(order);

 if(tg && tg.initData){

  tg.sendData(data);

 }else{

  alert(
   "Telegram orqali ochilmagan!\n\n"+
   "Buyurtma ma'lumoti:\n"+data
  );

 }

}

// MODAL
document.getElementById("modal").onclick=function(e){

 if(e.target===this){
  closeCart();
 }

};

document.getElementById("cartBtn").onclick=openCart;

// ISHGA TUSHIRISH
renderMenu();
updateBar();

</script>

</body>
</html>
