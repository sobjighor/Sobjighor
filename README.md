<!DOCTYPE html>
<html lang="bn">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>SobjiGhor</title>

<style>
body{
font-family:Arial;
margin:0;
background:#f2f2f2;
}

header{
background:green;
color:white;
text-align:center;
padding:15px;
}

.container{
width:95%;
margin:auto;
}

.product{
background:white;
padding:10px;
margin:10px 0;
border-radius:10px;
box-shadow:0 0 5px #ccc;
}

button{
background:green;
color:white;
border:none;
padding:10px;
width:100%;
border-radius:5px;
margin-top:5px;
}

.cart{
background:white;
padding:10px;
margin-top:15px;
border-radius:10px;
}

input, select{
width:100%;
padding:10px;
margin-top:8px;
}
</style>
</head>

<body>

<header>
<h1>🥬 SobjiGhor</h1>
<p>তাজা সবজি ঘরে বসেই কিনুন</p>
</header>

<div class="container">

<h2>🛒 পণ্য তালিকা</h2>

<div class="product">
<h3>🥔 আলু - ৫০৳/kg</h3>
<button onclick="addToCart('Alu',50)">Add to Cart</button>
</div>

<div class="product">
<h3>🍅 টমেটো - ৮০৳/kg</h3>
<button onclick="addToCart('Tomato',80)">Add to Cart</button>
</div>

<div class="product">
<h3>🍆 বেগুন - ৭০৳/kg</h3>
<button onclick="addToCart('Begun',70)">Add to Cart</button>
</div>

<div class="cart">
<h2>🛒 Cart</h2>
<div id="cart"></div>
<h3>Total: ৳<span id="total">0</span></h3>
</div>

<div class="cart">
<h2>📦 Checkout</h2>

<input type="text" id="name" placeholder="আপনার নাম">
<input type="text" id="phone" placeholder="মোবাইল নম্বর">
<input type="text" id="address" placeholder="ঠিকানা">

<h3>💳 Payment</h3>

<select id="payment">
<option>Cash on Delivery</option>
<option>bKash</option>
<option>Nagad</option>
<option>Rocket</option>
</select>

<input type="text" id="trx" placeholder="Transaction ID (যদি থাকে)">

<button onclick="placeOrder()">অর্ডার করুন</button>
</div>

</div>

<script>

let cart = [];
let total = 0;

function addToCart(name, price){
cart.push({name, price});
total += price;
updateCart();
}

function updateCart(){
let html = "";
cart.forEach((item,i)=>{
html += item.name + " - " + item.price + "৳<br>";
});
document.getElementById("cart").innerHTML = html;
document.getElementById("total").innerText = total;
}

function placeOrder(){

let name = document.getElementById("name").value;
let phone = document.getElementById("phone").value;
let address = document.getElementById("address").value;
let payment = document.getElementById("payment").value;
let trx = document.getElementById("trx").value;

if(name=="" || phone=="" || address==""){
alert("সব তথ্য পূরণ করুন");
return;
}

let msg = `New Order (SobjiGhor)%0A
Name: ${name}%0A
Phone: ${phone}%0A
Address: ${address}%0A
Payment: ${payment}%0A
Transaction ID: ${trx}%0A
Total: ${total}৳`;

let whatsapp = "https://wa.me/8801XXXXXXXXX?text=" + msg;

window.open(whatsapp, "_blank");
}

</script>

</body>
</html>
