<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Pick n Cheaper | Cheap Supermarket Cape Town - Free Delivery</title>
<meta name="description" content="Affordable groceries on Long Street, Cape Town. Fresh fruit & veg from R79.99, bulk rice & oil, free delivery over R500.">
<style>
*{box-sizing:border-box;margin:0;padding:0}
body{font-family:Arial,sans-serif;color:#333;background:#f8fdf8;line-height:1.6}
header{background:#0a7a0a;color:white;padding:12px 20px;display:flex;justify-content:space-between;align-items:center;position:sticky;top:0;z-index:100}
.logo{display:flex;align-items:center;gap:10px;font-weight:900;font-size:1.4rem}
.logo img{width:40px;height:40px;border-radius:50%;background:white;padding:5px}
nav{background:#044404;display:flex;justify-content:center;flex-wrap:wrap;position:sticky;top:56px;z-index:90}
nav a{color:white;padding:12px 18px;text-decoration:none;font-weight:bold}
#cartBtn{background:#ffeb3b;color:#000;padding:6px 14px;border-radius:20px;border:none;font-weight:bold;cursor:pointer;margin:8px}
.hero{height:70vh;background:linear-gradient(rgba(0,0,0,0.55),rgba(0,0,0,0.55)), url('https://images.unsplash.com/photo-1542838132-92c53300491e?w=1200');background-size:cover;background-position:center;display:flex;align-items:center;justify-content:center;text-align:center;color:white;padding:20px}
.hero h1{font-size:2.6rem}
.btn{background:#0a7a0a;color:white;padding:12px 24px;border:none;border-radius:30px;font-weight:bold;cursor:pointer;margin:5px}
.btn-yellow{background:#ffeb3b;color:#000}
.container{width:92%;max-width:1200px;margin:auto;padding:25px 0}
.products{display:grid;grid-template-columns:1fr;gap:20px;margin-top:20px}
.card{background:white;border-radius:16px;overflow:hidden;box-shadow:0 4px 12px rgba(0,0,0,0.1);cursor:pointer;transition:0.2s}
.card:hover{transform:translateY(-5px)}
.card img{width:100%;height:180px;object-fit:cover}
.card-body{padding:15px}
.price{color:#c00;font-weight:900;font-size:1.25rem}
.oldPrice{text-decoration:line-through;color:#888;margin-left:6px;font-size:0.9rem}
select,input,textarea{width:100%;padding:11px;margin:6px 0;border:1px solid #ccc;border-radius:8px}
.error{color:red;font-size:0.8rem;display:none}
#productModal{position:fixed;top:0;left:0;width:100%;height:100%;background:rgba(0,0,0,0.75);display:none;align-items:center;justify-content:center;z-index:200;padding:20px}
.modal-content{background:white;border-radius:16px;max-width:420px;width:100%;overflow:hidden;position:relative}
.modal-content img{width:100%;height:240px;object-fit:cover}
.modal-body{padding:20px}
.close{position:absolute;top:10px;right:15px;font-size:32px;cursor:pointer;color:white;background:rgba(0,0,0,0.5);width:35px;height:35px;border-radius:50%;display:flex;align-items:center;justify-content:center}
#toast{position:fixed;bottom:20px;right:20px;background:#0a7a0a;color:white;padding:15px 20px;border-radius:10px;display:none;z-index:300}
@media(min-width:650px){.products{grid-template-columns:1fr 1fr}}
@media(min-width:1000px){.products{grid-template-columns:1fr 1fr 1fr}.hero h1{font-size:3.2rem}}
</style>
</head>
<body>
<header>
<div class="logo"><img src="https://cdn-icons-png.flaticon.com/512/3081/3081967.png" alt="Pick n Cheaper Logo"> Pick n Cheaper</div>
<button id="cartBtn" onclick="showCart()">🛒 <span id="cartCount">0</span> in cart</button>
</header>
<nav>
<a href="#home">Home</a>
<a href="#specials">Specials</a>
<a href="#contact">Contact</a>
</nav>
<section id="home" class="hero">
<div>
<h1>Cape Town's Freshest<br>Shouldn't Cost More</h1>
<p>123 Long Street - 20-40% less than chains - Open 7 Days 8am-8pm</p>
<button class="btn btn-yellow" onclick="document.getElementById('specials').scrollIntoView({behavior:'smooth'})">Check Today's Prices ↓</button>
<p style="margin-top:12px;font-size:0.95rem">Free Delivery > R500 in City Bowl</p>
</div>
</section>
<main class="container">
<section id="specials">
<h2 style="text-align:center;color:#0a7a0a">🔥 This Week's Best Sellers - Click Picture To Check Price</h2>
<div style="text-align:center;margin:15px 0">
<label>Filter Products:
<select id="filter" onchange="filterProducts()" style="width:auto;display:inline-block;padding:8px 15px">
<option value="all">All Products</option>
<option value="veg">Fruit & Veg</option>
<option value="bulk">Bulk & Pantry</option>
<option value="meat">Meat</option>
</select>
</label>
</div>
<div class="products" id="productList">
<div class="card" data-cat="veg" onclick="openProduct('Fresh Fruit & Veg Combo','https://images.unsplash.com/photo-1610832958506-aa56368176cf?w=600','R79.99','R120.00','Local seasonal mix 5kg - potatoes, tomatoes, onions, apples, bananas. Save R40 vs Pick n Pay.')">
<img src="https://images.unsplash.com/photo-1610832958506-aa56368176cf?w=600" alt="Fruit and veg combo cheap supermarket Cape Town">
<div class="card-body"><h3>Fresh Fruit & Veg Combo</h3><p>Local farm fresh</p><p class="price">R79.99 <span class="oldPrice">R120</span></p><button class="btn" style="width:100%;margin-top:8px" onclick="event.stopPropagation(); addToCart('Veg Combo')">Add to Cart</button></div>
</div>
<div class="card" data-cat="bulk" onclick="openProduct('Bread & Milk Daily Deal','https://images.unsplash.com/photo-1509440159596-0249088772ff?w=600','R45.99','R65.00','Fresh bakery bread + 2L full cream milk. Baked daily at Long Street.')">
<img src="https://images.unsplash.com/photo-1509440159596-0249088772ff?w=600" alt="Bread and milk Long Street grocery">
<div class="card-body"><h3>Bread & Milk Daily Deal</h3><p>Fresh this morning</p><p class="price">R45.99 <span class="oldPrice">R65</span></p><button class="btn" style="width:100%;margin-top:8px" onclick="event.stopPropagation(); addToCart('Bread & Milk')">Add to Cart</button></div>
</div>
<div class="card" data-cat="bulk" onclick="openProduct('Pantry Bulk Savers','https://images.unsplash.com/photo-1586201375761-83865001e31c?w=600','R199.99','R280.00','5kg Rice, 2L Oil, 2.5kg Sugar - 1 month family supply. Best bulk rice and oil Cape Town deal.')">
<img src="https://images.unsplash.com/photo-1586201375761-83865001e31c?w=600" alt="Bulk rice and oil Cape Town">
<div class="card-body"><h3>Pantry Bulk Savers</h3><p>Family month pack</p><p class="price">R199.99 <span class="oldPrice">R280</span></p><button class="btn" style="width:100%;margin-top:8px" onclick="event.stopPropagation(); addToCart('Bulk Savers')">Add to Cart</button></div>
</div>
<div class="card" data-cat="meat" onclick="openProduct('Meat Combo Special','https://images.unsplash.com/photo-1607623814075-e51df1bdc82f?w=600','R149.99','R210.00','2kg Chicken, 1kg Beef stew, 1kg Boerewors. Halal certified, fresh from local butcher.')">
<img src="https://images.unsplash.com/photo-1607623814075-e51df1bdc82f?w=600" alt="Meat combo affordable groceries City Bowl">
<div class="card-body"><h3>Meat Combo Special</h3><p>Halal & fresh</p><p class="price">R149.99 <span class="oldPrice">R210</span></p><button class="btn" style="width:100%;margin-top:8px" onclick="event.stopPropagation(); addToCart('Meat Combo')">Add to Cart</button></div>
</div>
</div>
</section>
<section id="contact" style="margin-top:50px;background:white;padding:25px;border-radius:16px;box-shadow:0 4px 15px rgba(0,0,0,0.08)">
<h2 style="color:#0a7a0a">Lead Generation - Get 10% Off Voucher</h2>
<p>Get free delivery info + voucher on WhatsApp</p>
<form id="leadForm" onsubmit="return validateForm()" style="margin-top:15px">
<input type="text" id="name" placeholder="Your Name - e.g. Thandi"><span class="error" id="nameError">Name must be 3+ letters</span>
<input type="email" id="email" placeholder="Email for voucher"><span class="error" id="emailError">Enter valid email</span>
<input type="tel" id="phone" placeholder="WhatsApp 082...">
<textarea id="message" placeholder="Bulk order? What do you need?" rows="3"></textarea>
<button type="submit" class="btn" style="width:100%">Get My Voucher + Free Delivery Info</button>
</form>
<p id="formSuccess" style="display:none;color:green;font-weight:bold;margin-top:12px">✅ Thanks! Voucher sent. We will WhatsApp you.</p>
<iframe src="https://maps.google.com/maps?q=Long%20Street%20Cape%20Town&t=&z=14&output=embed" width="100%" height="220" style="border:0;border-radius:12px;margin-top:20px" loading="lazy"></iframe>
</section>
</main>
<!-- CLICK TO CHECK PRICE MODAL -->
<div id="productModal" onclick="if(event.target===this)closeModal()">
<div class="modal-content">
<span class="close" onclick="closeModal()">&times;</span>
<img id="modalImg" src="" alt="Product">
<div class="modal-body">
<h2 id="modalTitle"></h2>
<p id="modalDesc" style="margin:10px 0;color:#555"></p>
<p style="font-size:1.9rem" class="price"><span id="modalPrice"></span> <span class="oldPrice" id="modalOld"></span></p>
<p style="color:green;font-weight:bold;margin-top:5px">✅ In Stock - Long Street Store</p>
<button class="btn" style="width:100%;margin-top:15px" onclick="addToCartFromModal()">Add to Cart</button>
<button class="btn" style="width:100%;margin-top:8px;background:#eee;color:#333" onclick="closeModal()">Continue Shopping</button>
</div>
</div>
</div>
<div id="toast"></div>
<script>
// MIXED JS - Old + New
let cart=0, currentItem='';
function addToCart(item){ cart++; document.getElementById('cartCount').innerText=cart; showToast(item+' added! Cart: '+cart); }
function addToCartFromModal(){ addToCart(currentItem); closeModal(); }
function showToast(msg){ const t=document.getElementById('toast'); t.innerText=msg; t.style.display='block'; setTimeout(()=>t.style.display='none',3000); }
function openProduct(title,img,price,old,desc){
 currentItem=title; document.getElementById('modalTitle').innerText=title; document.getElementById('modalImg').src=img;
 document.getElementById('modalPrice').innerText=price; document.getElementById('modalOld').innerText=old;
 document.getElementById('modalDesc').innerText=desc; document.getElementById('productModal').style.display='flex';
}
function closeModal(){ document.getElementById('productModal').style.display='none'; }
function showCart(){ showToast('You have '+cart+' items. WhatsApp 082 123 4567 to checkout'); }
function filterProducts(){
 let val=document.getElementById('filter').value;
 document.querySelectorAll('.card').forEach(c=>{ c.style.display=(val==='all'||c.dataset.cat===val)?'block':'none'; });
}
function validateForm(){
 let name=document.getElementById('name').value, email=document.getElementById('email').value, valid=true;
 if(name.length<3){document.getElementById('nameError').style.display='block'; valid=false}else{document.getElementById('nameError').style.display='none'}
 if(!email.includes('@')){document.getElementById('emailError').style.display='block'; valid=false}else{document.getElementById('emailError').style.display='none'}
 if(valid){document.getElementById('formSuccess').style.display='block'; document.getElementById('leadForm').reset();}
 return false;
}
</script>
</body>
</html>
