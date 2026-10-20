
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Sri Raghavendra Bhavana</title>
<style>
body{font-family:Arial;margin:0;background:#f6f6f6;color:#222}
header{background:#fc8019;color:white;padding:20px;text-align:center}
.wrap{max-width:850px;margin:auto;padding:14px}
input,button{font-size:16px}
#search{box-sizing:border-box;width:100%;padding:13px;border:1px solid #ddd;border-radius:9px}
.categories{display:flex;gap:8px;overflow:auto;padding:12px 0}
.categories button{border:1px solid #fc8019;background:white;color:#b94e00;border-radius:20px;padding:9px 13px;white-space:nowrap}
.categories button.active{background:#fc8019;color:white}
.item{background:white;padding:15px;margin:10px 0;border-radius:10px;display:flex;justify-content:space-between;align-items:center;gap:10px;box-shadow:0 1px 4px #ddd}
.item small{color:#777}
.qty{display:flex;align-items:center;gap:10px}
.qty button{background:white;border:1px solid #159447;color:#159447;border-radius:6px;padding:7px 12px}
.cart{background:white;padding:16px;border-radius:10px;margin-top:20px}
.order{width:100%;background:#159447;color:white;padding:15px;border:0;border-radius:8px;font-weight:bold}
</style>
</head>
<body>
<header>
<h2>Sri Raghavendra Bhavana</h2>
<p>Fresh food • Easy WhatsApp ordering</p>
</header>
<div class="wrap">
<input id="search" placeholder="Search for dishes..." oninput="render()">
<div class="categories" id="categories"></div>
<div id="menu"></div>
<div class="cart">
<h2>Your Cart</h2>
<div id="cart">Your cart is empty.</div>
<h3 id="total">Total: ₹0</h3>
<input id="customer" placeholder="Your name" style="box-sizing:border-box;width:100%;padding:12px;margin:6px 0">
<input id="address" placeholder="Delivery address or Pickup" style="box-sizing:border-box;width:100%;padding:12px;margin:6px 0">
<button class="order" onclick="orderNow()">Order on WhatsApp</button>
</div>
</div>
<script>
const HOTEL_WHATSAPP="918095004556";

const HOTEL_MENU=[
{id:1,name:"Masala Dosa",price:50,category:"Dosa"},
{id:2,name:"Open Dosa",price:60,category:"Dosa"},
{id:3,name:"Khali Dosa",price:45,category:"Dosa"},
{id:4,name:"Onion Dosa",price:70,category:"Dosa"},
{id:5,name:"Set Dosa",price:50,category:"Dosa"},
{id:6,name:"Poori",price:40,category:"Breakfast"},
{id:7,name:"Upma",price:25,category:"Breakfast"},
{id:8,name:"Kesari Bath",price:25,category:"Breakfast"},
{id:9,name:"Upma Kesari Bath",price:40,category:"Breakfast"},
{id:10,name:"Chitranna",price:40,category:"Rice items"},
{id:11,name:"Curd Rice",price:40,category:"Rice items"},
{id:12,name:"Puliyogare",price:40,category:"Rice items"},
{id:13,name:"Palav",price:40,category:"Rice items"},
{id:14,name:"Idli",price:25,category:"Breakfast"},
{id:15,name:"Idli Vada",price:40,category:"Breakfast"},
{id:16,name:"Chapati plate (2)",price:50,category:"Chapati"},
{id:17,name:"Curd Vada",price:35,category:"Snacks"},
{id:18,name:"Meals",price:80,category:"Meals"},
{id:19,name:"Rice",price:50,category:"Rice items"},
{id:20,name:"Mixture",price:40,category:"Snacks"},
{id:21,name:"Pakoda",price:40,category:"Snacks"},
{id:22,name:"Plate Jilebi",price:25,category:"Sweets"},
{id:23,name:"Jilebi",price:15,category:"Sweets"},
{id:24,name:"Gulab Jamun",price:15,category:"Sweets"},
{id:25,name:"Avalakki Sev",price:40,category:"Snacks"},
{id:26,name:"Mirchi",price:5,category:"Snacks"},
{id:27,name:"Vada",price:15,category:"Snacks"}
];

let cart={};
let category="All";

const categories=["All",...new Set(HOTEL_MENU.map(x=>x.category))];

document.getElementById("categories").innerHTML=categories.map(c=>
`<button class="${c===category?'active':''}" onclick="chooseCategory('${c}')">${c}</button>`
).join("");

function chooseCategory(c){
category=c;
document.querySelectorAll(".categories button").forEach(b=>{
b.classList.toggle("active",b.textContent===c);
});
render();
}

function render(){
const q=document.getElementById("search").value.toLowerCase();
const items=HOTEL_MENU.filter(x=>
(category==="All"||x.category===category)&&x.name.toLowerCase().includes(q)
);
document.getElementById("menu").innerHTML=items.map(x=>`
<div class="item">
<div><strong>${x.name}</strong><br><small>${x.category}</small><br><b>₹${x.price}</b></div>
<div class="qty">
<button onclick="changeQty(${x.id},-1)">−</button>
<span>${cart[x.id]||0}</span>
<button onclick="changeQty(${x.id},1)">+</button>
</div></div>`).join("")||"<p>No dishes found.</p>";
renderCart();
}

function changeQty(id,n){
cart[id]=Math.max(0,(cart[id]||0)+n);
render();
}

function renderCart(){
const items=HOTEL_MENU.filter(x=>cart[x.id]>0);
document.getElementById("cart").innerHTML=items.length?items.map(x=>
`<p>${x.name} × ${cart[x.id]} = ₹${x.price*cart[x.id]}</p>`
).join(""):"Your cart is empty.";
const total=items.reduce((s,x)=>s+x.price*cart[x.id],0);
document.getElementById("total").textContent="Total: ₹"+total;
}

function orderNow(){
const items=HOTEL_MENU.filter(x=>cart[x.id]>0);
if(!items.length){alert("Please select food first.");return;}
const name=document.getElementById("customer").value.trim();
const address=document.getElementById("address").value.trim();
if(!name||!address){alert("Enter your name and address or Pickup.");return;}
let msg="NEW FOOD ORDER - SRI RAGHAVENDRA BHAVANA\n";
msg+="Name: "+name+"\nAddress/Pickup: "+address+"\n\n";
items.forEach(x=>msg+=x.name+" x "+cart[x.id]+" = ₹"+x.price*cart[x.id]+"\n");
msg+="\nTotal: ₹"+items.reduce((s,x)=>s+x.price*cart[x.id],0);
msg+="\nPlease confirm order and delivery charges.";
window.open("https://wa.me/"+HOTEL_WHATSAPP+"?text="+encodeURIComponent(msg),"_blank");
}
render();
</script>
</body>
</html>
