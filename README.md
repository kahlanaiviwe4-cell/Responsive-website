<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Pick n Cheaper | Cheap Supermarket Cape Town - Free Delivery</title>
<meta name="description" content="Affordable groceries on Long Street, Cape Town. Fresh fruit & veg from R79.99, bulk rice & oil, free delivery over R500.">
<style>
*{box-sizing:border-box;margin:0;padding:0}
body{font-family:Arial,sans-serif;line-height:1.6;color:#333}
header{background:#0a7a0a;color:white;padding:1rem;text-align:center;position:relative}
nav{background:#044404;display:flex;justify-content:center;flex-wrap:wrap;position:sticky;top:0;z-index:10}
nav a{color:white;padding:14px 20px;text-decoration:none;font-weight:bold}
#cartCount{background:#ff0;color:#000;padding:2px 7px;border-radius:50%;margin-left:5px}
.container{width:92%;max-width:1100px;margin:auto;padding:20px 0}
.hero{background:#e8f5e9;padding:40px 20px;text-align:center;border-radius:12px}
.btn{background:#0a7a0a;color:white;padding:12px 24px;border:none;border-radius:25px;font-weight:bold;cursor:pointer;margin:5px}
.products{display:flex;flex-direction:column;gap:20px;margin-top:20px}
.card{border:1px solid #ddd;border-radius:12px;padding:15px;background:white}
.price{color:#c00;font-weight:bold;font-size:1.2rem}
input,textarea,select{width:100%;padding:10px;margin:8px 0;border:1px solid #ccc;border-radius:6px}
.error{color:red;font-size:0.8rem;display:none}
#toast{position:fixed;bottom:20px;right:20px;background:#0a7a0a;color:white;padding:15px 20px;border-radius:8px;display:none}
@media(min-width:600px){.products{flex-direction:row;flex-wrap:wrap}.card{width:48%}}
@media(min-width:900px){.card{width:31%}}
</style>
</head>
<body>
<header>
<h1>Pick n Cheaper</h1>
<p>123 Long Street, Cape Town - Quality Groceries, Cheaper Prices <span id="cartCount">0</span> in cart</p>
</header>
<nav>
<a href="#home">Home</a>
<a href="#specials">Specials</a>
<a href="#contact">Contact</a>
</nav>
<main class="container">
<section id="home" class="hero">
<h2>Cape Town's Freshest Shouldn't Cost More</h2>
<p>We partner with local farms for <strong>cheap supermarket Cape Town</strong> deals - 20-40% less than chains.</p>
<button class="btn" onclick="showToast('Specials loaded! Scroll down')">See Today's Specials</button>
<p style="margin-top:10px">Open 7 Days 8am-8pm | Free Delivery >R500</p>
</section>
<section id="specials" style="margin-top:30px">
<h2 style="color:#0a7a0a;text-align:center">🔥 This Week's Best Sellers</h2>
<label>Filter: <select id="filter" onchange="filterProducts()">
<option value="all">All</option><option value="veg">Fruit & Veg</option><option value="bulk">Bulk</option>
</select></label>
<div class="products" id="productList">
<div class="card" data-cat="veg">
<h3>Fresh Fruit & Veg Combo</h3><p>Local seasonal mix</p><p class="price">R79.99</p>
<button class="btn" onclick="addToCart('Veg Combo')">Add to Cart</button>
</div>
<div class="card" data-cat="bulk">
<h3>Bread & Milk Daily Deal</h3><p>Fresh bakery + 2L milk</p><p class="price">R45.99</p>
<button class="btn" onclick="addToCart('Bread & Milk')">Add to Cart</button>
</div>
<div class="card" data-cat="bulk">
<h3>Pantry Bulk Savers</h3><p>5kg Rice, 2L Oil, 2.5kg Sugar</p><p class="price">R199.99</p>
<button class="btn" onclick="addToCart('Bulk Savers')">Add to Cart</button>
</div>
</div>
</section>
<section id="contact" style="margin-top:40px;background:#f5f5f5;padding:20px;border-radius:12px">
<h2 style="color:#0a7a0a">Lead Generation - Get 10% Off</h2>
<form id="leadForm" onsubmit="return validateForm()">
<input type="text" id="name" placeholder="Your Name - e.g. Thandi">
<span class="error" id="nameError">Name must be 3+ letters</span>
<input type="email" id="email" placeholder="Email for voucher">
<span class="error" id="emailError">Enter valid email</span>
<input type="tel" id="phone" placeholder="WhatsApp 082...">
<textarea id="message" placeholder="What do you need? Bulk order?"></textarea>
<button type="submit" class="btn" style="width:100%">Get My Voucher + Free Delivery Info</button>
</form>
<p id="formSuccess" style="display:none;color:green;font-weight:bold;margin-top:10px">✅ Thanks! Check your email - voucher sent. We will WhatsApp you.</p>
<iframe src="https://maps.google.com/maps?q=Long%20Street%20Cape%20Town&t=&z=14&output=embed" width="100%" height="220" style="border:0;border-radius:10px;margin-top:15px"></iframe>
</section>
</main>
<div id="toast"></div>
<script>
// JAVASCRIPT FUNDAMENTALS + DOM + EVENTS
let cart = 0;
function addToCart(item){
 cart++;
 document.getElementById('cartCount').innerText = cart;
 showToast(item + ' added! Cart: ' + cart);
}
function showToast(msg){
 const t = document.getElementById('toast');
 t.innerText = msg; t.style.display='block';
 setTimeout(()=>t.style.display='none',3000);
}
function filterProducts(){
 let val = document.getElementById('filter').value;
 document.querySelectorAll('.card').forEach(c=>{
   c.style.display = (val==='all' || c.dataset.cat===val) ? 'block' : 'none';
 });
}
function validateForm(){
 let valid = true;
 let name = document.getElementById('name').value;
 let email = document.getElementById('email').value;
 if(name.length < 3){document.getElementById('nameError').style.display='block'; valid=false}
 else{document.getElementById('nameError').style.display='none'}
 if(!email.includes('@')){document.getElementById('emailError').style.display='block'; valid=false}
 else{document.getElementById('emailError').style.display='none'}
 if(valid){document.getElementById('formSuccess').style.display='block'; document.getElementById('leadForm').reset()}
 return false; // prevents page reload
}
</script>
</body>
</html>
