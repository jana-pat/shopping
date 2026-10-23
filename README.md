<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>The Local Shop – Fresh Finds, Best Prices</title>
<meta name="description" content="The Local Shop – Fresh Finds, Best Prices. Order online and we'll confirm by phone.">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Bricolage+Grotesque:wght@600;800&family=DM+Sans:wght@400;500;700&display=swap" rel="stylesheet">
<style>
  :root{
    --bg:#F3F6F4; --surface:#FFFFFF; --ink:#12231D; --muted:#5B6B65;
    --brand:#1B7A4B; --brand-dark:#135A37; --tag:#FFD23F; --line:#DCE5E0; --danger:#B3261E;
    --display:"Bricolage Grotesque","Trebuchet MS",sans-serif;
    --body:"DM Sans",system-ui,-apple-system,"Segoe UI",sans-serif;
  }
  *{box-sizing:border-box;margin:0;padding:0}
  html{scroll-behavior:smooth}
  body{font-family:var(--body);background:var(--bg);color:var(--ink);line-height:1.5;-webkit-font-smoothing:antialiased}
  img{max-width:100%;display:block}
  button{font:inherit;cursor:pointer}
  :focus-visible{outline:3px solid var(--tag);outline-offset:2px}
  @media (prefers-reduced-motion:reduce){html{scroll-behavior:auto}*{transition:none!important;animation:none!important}}

  /* Top bar */
  .topbar{position:fixed;top:0;left:0;right:0;z-index:30;display:flex;align-items:center;justify-content:space-between;padding:12px 18px;color:#fff;transition:background .25s,box-shadow .25s}
  .topbar.solid{background:var(--ink);box-shadow:0 2px 12px rgba(0,0,0,.2)}
  .logo{font-family:var(--display);font-weight:800;font-size:1.2rem;letter-spacing:-.01em;color:#fff;text-decoration:none}
  .topbar nav a{color:#fff;text-decoration:none;font-weight:500;margin-left:18px;font-size:.95rem}
  .topbar nav a:hover{text-decoration:underline}

  /* Hero */
  .hero{position:relative;min-height:100svh;display:flex;align-items:flex-end;color:#fff;background:#12231D url("https://i.ibb.co/bR8R0BvV/IMG-0895.jpg") center/cover no-repeat}
  .hero::before{content:"";position:absolute;inset:0;background:linear-gradient(to top,rgba(10,22,17,.88) 8%,rgba(10,22,17,.35) 55%,rgba(10,22,17,.5))}
  .hero-inner{position:relative;width:100%;max-width:1100px;margin:0 auto;padding:0 20px 12vh}
  .hero h1{font-family:var(--display);font-weight:800;font-size:clamp(2.8rem,11vw,6.5rem);line-height:.95;letter-spacing:-.03em;max-width:12ch}
  .hero p{margin-top:16px;font-size:clamp(1.05rem,3.4vw,1.4rem);max-width:30ch;opacity:.95}
  .btn{display:inline-block;border:0;border-radius:999px;padding:14px 28px;font-weight:700;font-size:1rem;background:var(--tag);color:var(--ink);text-decoration:none;transition:transform .15s,background .15s}
  .btn:hover{transform:translateY(-2px);background:#FFE06E}
  .hero .btn{margin-top:28px}

  /* Products */
  section{scroll-margin-top:60px}
  .products{padding:64px 0 48px}
  .wrap{max-width:1100px;margin:0 auto;padding:0 20px}
  .section-head{display:flex;align-items:end;justify-content:space-between;gap:16px;margin-bottom:22px}
  h2{font-family:var(--display);font-size:clamp(1.8rem,6vw,2.8rem);letter-spacing:-.02em;line-height:1.05}
  .section-head p{color:var(--muted);margin-top:6px}
  .arrows{display:none;gap:8px}
  .arrows button{width:44px;height:44px;border-radius:50%;border:1.5px solid var(--ink);background:transparent;color:var(--ink);font-size:1.2rem}
  .arrows button:hover{background:var(--ink);color:#fff}
  @media(min-width:700px){.arrows{display:flex}}

  .carousel{display:flex;gap:16px;overflow-x:auto;scroll-snap-type:x mandatory;padding:4px 20px 20px;scrollbar-width:thin;-webkit-overflow-scrolling:touch}
  .carousel::before,.carousel::after{content:"";flex:0 0 max(0px,calc((100vw - 1100px)/2 - 20px))}
  .card{flex:0 0 min(78vw,270px);scroll-snap-align:start;background:var(--surface);border-radius:18px;overflow:hidden;border:1px solid var(--line);display:flex;flex-direction:column}
  .card .img{position:relative;aspect-ratio:1/1;background:#E4ECE8}
  .card img{width:100%;height:100%;object-fit:cover}
  .price{position:absolute;left:12px;bottom:12px;background:var(--tag);color:var(--ink);font-weight:800;padding:5px 12px;border-radius:8px;font-size:1rem;transform:rotate(-2deg)}
  .card .body{padding:14px 16px 16px;display:flex;flex-direction:column;gap:12px;flex:1;justify-content:space-between}
  .card h3{font-family:var(--display);font-size:1.2rem;line-height:1.2}
  .add{width:100%;border:0;border-radius:12px;padding:12px;background:var(--brand);color:#fff;font-weight:700;transition:background .15s}
  .add:hover{background:var(--brand-dark)}
  .add.done{background:var(--ink)}

  /* About / contact */
  .about{padding:40px 0 90px}
  .about-box{background:var(--ink);color:#fff;border-radius:24px;padding:32px 24px;display:grid;gap:18px}
  .about-box p{max-width:52ch;opacity:.9}
  .about-box a{color:var(--tag)}
  footer{text-align:center;color:var(--muted);font-size:.9rem;padding:0 20px 100px}

  /* Floating buttons */
  .fab{position:fixed;z-index:40;width:58px;height:58px;border-radius:50%;border:0;display:grid;place-items:center;box-shadow:0 6px 18px rgba(0,0,0,.28);transition:transform .15s}
  .fab:hover{transform:scale(1.07)}
  .fab svg{width:28px;height:28px}
  .cart-fab{right:18px;bottom:90px;background:var(--tag);color:var(--ink)}
  .wa-fab{right:18px;bottom:18px;background:#25D366;color:#fff;text-decoration:none}
  .badge{position:absolute;top:-4px;right:-4px;min-width:24px;height:24px;padding:0 6px;border-radius:12px;background:var(--danger);color:#fff;font-size:.8rem;font-weight:700;display:grid;place-items:center}
  .badge.bump{animation:bump .3s}
  @keyframes bump{50%{transform:scale(1.4)}}

  /* Drawer */
  .overlay{position:fixed;inset:0;background:rgba(10,20,15,.55);opacity:0;pointer-events:none;transition:opacity .25s;z-index:50}
  .overlay.open{opacity:1;pointer-events:auto}
  .drawer{position:fixed;top:0;right:0;bottom:0;width:min(100%,440px);background:var(--surface);z-index:60;transform:translateX(100%);transition:transform .3s;display:flex;flex-direction:column}
  .drawer.open{transform:none}
  .drawer-head{display:flex;justify-content:space-between;align-items:center;padding:16px 20px;border-bottom:1px solid var(--line)}
  .drawer-head h2{font-size:1.5rem}
  .close{background:none;border:0;font-size:2rem;line-height:1;color:var(--ink);width:44px;height:44px}
  .drawer-body{flex:1;overflow-y:auto;padding:16px 20px}
  .empty{color:var(--muted);text-align:center;padding:36px 0}
  .line-item{display:grid;grid-template-columns:56px 1fr auto;gap:12px;align-items:center;padding:10px 0;border-bottom:1px solid var(--line)}
  .line-item img{width:56px;height:56px;object-fit:cover;border-radius:10px;background:#E4ECE8}
  .line-item .name{font-weight:700;font-size:.95rem;line-height:1.25}
  .line-item .sub{color:var(--muted);font-size:.85rem}
  .qty{display:flex;align-items:center;gap:6px;margin-top:4px}
  .qty button{width:30px;height:30px;border-radius:8px;border:1px solid var(--line);background:var(--bg);font-weight:700}
  .qty span{min-width:22px;text-align:center;font-weight:700}
  .remove{background:none;border:0;color:var(--danger);font-size:.85rem;text-decoration:underline}
  .total{display:flex;justify-content:space-between;font-weight:700;font-size:1.15rem;padding:16px 0 4px}
  form{display:grid;gap:12px;margin-top:14px}
  label{font-weight:700;font-size:.9rem;display:grid;gap:5px}
  input,textarea{font:inherit;padding:12px 14px;border-radius:10px;border:1.5px solid var(--line);background:#fff;color:var(--ink);width:100%}
  input:focus,textarea:focus{outline:none;border-color:var(--brand)}
  textarea{resize:vertical;min-height:70px}
  .send{width:100%;border:0;border-radius:12px;padding:15px;background:var(--brand);color:#fff;font-weight:700;font-size:1.05rem}
  .send:hover:not(:disabled){background:var(--brand-dark)}
  .send:disabled{opacity:.6;cursor:not-allowed}
  .status{padding:12px 14px;border-radius:10px;font-size:.93rem;display:none}
  .status.ok{display:block;background:#DDF3E6;color:#0F4D2C}
  .status.err{display:block;background:#FBE4E2;color:var(--danger)}
</style>
</head>
<body>

<!-- ================= TOP BAR ================= -->
<header class="topbar" id="topbar">
  <a class="logo" href="#top">The Local Shop</a>
  <nav><a href="#products">Products</a><a href="#contact">Contact</a></nav>
</header>

<!-- ================= HERO ================= -->
<main id="top">
  <section class="hero" aria-label="Welcome">
    <div class="hero-inner">
      <h1>Fresh Finds, Best Prices</h1>
      <p>Everyday essentials from your neighbourhood shop. Order online, we confirm by phone.</p>
      <a class="btn" href="#products" id="shopNow">Shop Now</a>
    </div>
  </section>

  <!-- ================= PRODUCTS ================= -->
  <section class="products" id="products">
    <div class="wrap section-head">
      <div>
        <h2>This week on the shelf</h2>
        <p>Swipe to browse. Tap Add to Cart to start your order.</p>
      </div>
      <div class="arrows">
        <button type="button" id="prev" aria-label="Previous products">&#8592;</button>
        <button type="button" id="next" aria-label="Next products">&#8594;</button>
      </div>
    </div>
    <div class="carousel" id="carousel" tabindex="0" aria-label="Product carousel"></div>
  </section>

  <!-- ================= CONTACT ================= -->
  <section class="about" id="contact">
    <div class="wrap">
      <div class="about-box">
        <h2>How ordering works</h2>
        <p>Add what you like to the cart, enter your name and phone number, and send the order. The shop owner gets it by email and calls you to confirm the details and delivery or pickup.</p>
        <p>Prefer to chat? <a href="#" class="wa-link" target="_blank" rel="noopener">Message us on WhatsApp</a>.</p>
      </div>
    </div>
  </section>
</main>

<footer>&copy; <span id="year"></span> The Local Shop. All rights reserved.</footer>

<!-- ================= FLOATING BUTTONS ================= -->
<button class="fab cart-fab" id="cartBtn" aria-label="Open cart">
  <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true"><circle cx="9" cy="21" r="1"/><circle cx="20" cy="21" r="1"/><path d="M1 1h4l2.7 13.4a2 2 0 0 0 2 1.6h9.7a2 2 0 0 0 2-1.6L23 6H6"/></svg>
  <span class="badge" id="badge">0</span>
</button>
<a class="fab wa-fab wa-link" href="#" target="_blank" rel="noopener" aria-label="Chat on WhatsApp">
  <svg viewBox="0 0 24 24" fill="currentColor" aria-hidden="true"><path d="M20.5 3.5A11.8 11.8 0 0 0 12 0C5.4 0 .1 5.3.1 11.9c0 2.1.5 4.1 1.6 5.9L0 24l6.4-1.7a11.9 11.9 0 0 0 5.6 1.4c6.6 0 11.9-5.3 11.9-11.9 0-3.2-1.2-6.2-3.4-8.3zM12 21.7c-1.8 0-3.5-.5-5-1.4l-.4-.2-3.8 1 1-3.7-.2-.4a9.8 9.8 0 0 1-1.5-5.2C2.1 6.4 6.5 2 12 2c2.6 0 5.1 1 6.9 2.9a9.7 9.7 0 0 1 2.9 6.9c0 5.4-4.4 9.9-9.8 9.9zm5.4-7.4c-.3-.1-1.8-.9-2-1-.3-.1-.5-.1-.7.1l-1 1.2c-.2.2-.4.2-.7.1a8 8 0 0 1-4-3.5c-.3-.5.3-.5.9-1.6.1-.2 0-.4 0-.5l-.9-2.2c-.2-.6-.5-.5-.7-.5h-.6c-.2 0-.5.1-.8.4-.3.3-1 1-1 2.5s1.1 2.9 1.2 3.1c.1.2 2.100 3.200 5.100 4.500 1.900.8 2.600.9 3.500.7.600-.1 1.800-.7 2-1.400.3-.7.3-1.300.2-1.400-.1-.2-.3-.3-.6-.4z"/></svg>
</a>

<!-- ================= CART DRAWER ================= -->
<div class="overlay" id="overlay"></div>
<aside class="drawer" id="drawer" aria-label="Shopping cart" aria-hidden="true">
  <div class="drawer-head">
    <h2>Your cart</h2>
    <button class="close" id="closeCart" aria-label="Close cart">&times;</button>
  </div>
  <div class="drawer-body">
    <div id="cartItems"></div>
    <div class="total" id="totalRow" hidden><span>Total</span><span id="total">₹0</span></div>

    <form id="orderForm" hidden>
      <label>Your name
        <input type="text" name="customer_name" id="custName" required autocomplete="name" placeholder="e.g. Ravi Kumar">
      </label>
      <label>Phone number
        <input type="tel" name="customer_phone" id="custPhone" required autocomplete="tel" inputmode="tel" pattern="[0-9+\-\s]{7,15}" placeholder="e.g. 98765 43210">
      </label>
      <label>Address or note (optional)
        <textarea name="customer_note" id="custNote" placeholder="Delivery address, or 'I'll pick up'"></textarea>
      </label>
      <button class="send" type="submit" id="sendBtn">Send Order</button>
      <div class="status" id="status" role="status" aria-live="polite"></div>
    </form>
  </div>
</aside>

<!-- EmailJS SDK -->
<script src="https://cdn.jsdelivr.net/npm/@emailjs/browser@4/dist/email.min.js"></script>
<script>
/* =====================================================================
   CONFIGURATION – edit these values
   ===================================================================== */
const CONFIG = {
  // Owner email (EmailJS sends the order here; also set it as "To Email" in your EmailJS template)
  OWNER_EMAIL: "janardhanpatil821@gmail.com",   // or "thelocalshop@gmail.com"

  // EmailJS credentials (free account at https://www.emailjs.com)
  EMAILJS_PUBLIC_KEY: "veRbMBQ0QHI5iGiKG",
  EMAILJS_SERVICE_ID: "service_e3ckogg",
  EMAILJS_TEMPLATE_ID: "template_hcfzvu5",

  // WhatsApp number: country code + number, digits only (e.g. India: 919876543210)
  WHATSAPP_NUMBER: "918277116752",

  CURRENCY: "₹"
};

/* Products – change names and prices here */
const PRODUCTS = [
  { id: 1, name: "Wireless Mouse",     price: 499,  img: "https://i.ibb.co/HprmQ94B/Mouse.jpg"  },
  { id: 2, name: "Bluetooth Earbuds",  price: 1299, img: "https://i.ibb.co/B5CGdzyM/earbuds.jpg" },
  { id: 3, name: "Yoga Mat",           price: 699,  img: "https://i.ibb.co/ZzwQVXhc/Mat.jpg"     },
  { id: 4, name: "Water Bottle",       price: 349,  img: "https://i.ibb.co/LGQZXqb/Bottle.jpg"   },
  { id: 5, name: "Everyday Bag",       price: 899,  img: "https://i.ibb.co/rGy1xT9M/Bag.jpg"     }
];

/* =====================================================================
   HELPERS
   ===================================================================== */
const $ = id => document.getElementById(id);
const money = n => CONFIG.CURRENCY + n.toLocaleString("en-IN");
const esc = s => String(s).replace(/[&<>"']/g, c => ({"&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;","'":"&#39;"}[c]));
const FALLBACK_IMG = "data:image/svg+xml;utf8," + encodeURIComponent('<svg xmlns="http://www.w3.org/2000/svg" width="200" height="200"><rect width="200" height="200" fill="#E4ECE8"/><text x="100" y="108" font-size="16" text-anchor="middle" fill="#5B6B65" font-family="sans-serif">No image</text></svg>');

/* =====================================================================
   CART STATE
   ===================================================================== */
let cart = [];
try { cart = JSON.parse(localStorage.getItem("tls_cart") || "[]"); } catch(e) { cart = []; }
const saveCart = () => { try { localStorage.setItem("tls_cart", JSON.stringify(cart)); } catch(e) {} };

/* =====================================================================
   RENDER PRODUCTS
   ===================================================================== */
const carousel = $("carousel");
carousel.innerHTML = PRODUCTS.map(p => `
  <article class="card">
    <div class="img">
      <img src="${esc(p.img)}" alt="${esc(p.name)}" loading="lazy" onerror="this.onerror=null;this.src='${FALLBACK_IMG}'">
      <span class="price">${money(p.price)}</span>
    </div>
    <div class="body">
      <h3>${esc(p.name)}</h3>
      <button class="add" data-id="${p.id}">Add to Cart</button>
    </div>
  </article>`).join("");

carousel.addEventListener("click", e => {
  const btn = e.target.closest(".add");
  if (!btn) return;
  addToCart(Number(btn.dataset.id));
  btn.textContent = "Added ✓";
  btn.classList.add("done");
  setTimeout(() => { btn.textContent = "Add to Cart"; btn.classList.remove("done"); }, 1200);
});

/* Carousel arrows + gentle auto-slide (pauses on touch/hover/focus) */
const step = () => (carousel.querySelector(".card").offsetWidth + 16);
$("next").onclick = () => scrollCarousel(1);
$("prev").onclick = () => scrollCarousel(-1);
function scrollCarousel(dir){
  const max = carousel.scrollWidth - carousel.clientWidth;
  if (dir > 0 && carousel.scrollLeft >= max - 10) carousel.scrollTo({left:0,behavior:"smooth"});
  else if (dir < 0 && carousel.scrollLeft <= 10) carousel.scrollTo({left:max,behavior:"smooth"});
  else carousel.scrollBy({left:dir*step(),behavior:"smooth"});
}
let auto = null;
const reduceMotion = matchMedia("(prefers-reduced-motion: reduce)").matches;
const startAuto = () => { if (reduceMotion) return; stopAuto(); auto = setInterval(() => scrollCarousel(1), 3500); };
const stopAuto = () => { clearInterval(auto); auto = null; };
["mouseenter","touchstart","focusin"].forEach(ev => carousel.addEventListener(ev, stopAuto, {passive:true}));
["mouseleave","touchend","focusout"].forEach(ev => carousel.addEventListener(ev, startAuto, {passive:true}));
startAuto();

/* =====================================================================
   CART LOGIC
   ===================================================================== */
function addToCart(id){
  const p = PRODUCTS.find(x => x.id === id);
  const line = cart.find(x => x.id === id);
  if (line) line.qty++; else cart.push({ id:p.id, name:p.name, price:p.price, img:p.img, qty:1 });
  saveCart(); renderCart();
  const b = $("badge"); b.classList.remove("bump"); void b.offsetWidth; b.classList.add("bump");
}
function changeQty(id, delta){
  const line = cart.find(x => x.id === id);
  if (!line) return;
  line.qty += delta;
  if (line.qty <= 0) cart = cart.filter(x => x.id !== id);
  saveCart(); renderCart();
}
function removeItem(id){ cart = cart.filter(x => x.id !== id); saveCart(); renderCart(); }
const cartTotal = () => cart.reduce((s, i) => s + i.price * i.qty, 0);
const cartCount = () => cart.reduce((s, i) => s + i.qty, 0);

function renderCart(){
  $("badge").textContent = cartCount();
  const box = $("cartItems");
  if (!cart.length){
    box.innerHTML = '<p class="empty">Your cart is empty.<br>Add something from the shelf.</p>';
    $("totalRow").hidden = true; $("orderForm").hidden = true;
    return;
  }
  box.innerHTML = cart.map(i => `
    <div class="line-item">
      <img src="${esc(i.img)}" alt="" onerror="this.onerror=null;this.src='${FALLBACK_IMG}'">
      <div>
        <div class="name">${esc(i.name)}</div>
        <div class="sub">${money(i.price)} each</div>
        <div class="qty">
          <button type="button" data-act="dec" data-id="${i.id}" aria-label="Decrease quantity of ${esc(i.name)}">−</button>
          <span>${i.qty}</span>
          <button type="button" data-act="inc" data-id="${i.id}" aria-label="Increase quantity of ${esc(i.name)}">+</button>
        </div>
      </div>
      <div style="text-align:right">
        <strong>${money(i.price * i.qty)}</strong><br>
        <button type="button" class="remove" data-act="rm" data-id="${i.id}">Remove</button>
      </div>
    </div>`).join("");
  $("total").textContent = money(cartTotal());
  $("totalRow").hidden = false; $("orderForm").hidden = false;
}
$("cartItems").addEventListener("click", e => {
  const b = e.target.closest("button[data-act]");
  if (!b) return;
  const id = Number(b.dataset.id);
  if (b.dataset.act === "inc") changeQty(id, 1);
  if (b.dataset.act === "dec") changeQty(id, -1);
  if (b.dataset.act === "rm") removeItem(id);
});

/* Drawer open / close */
function openCart(){ $("drawer").classList.add("open"); $("overlay").classList.add("open"); $("drawer").setAttribute("aria-hidden","false"); }
function closeCart(){ $("drawer").classList.remove("open"); $("overlay").classList.remove("open"); $("drawer").setAttribute("aria-hidden","true"); }
$("cartBtn").onclick = openCart;
$("closeCart").onclick = closeCart;
$("overlay").onclick = closeCart;
document.addEventListener("keydown", e => { if (e.key === "Escape") closeCart(); });

/* =====================================================================
   SEND ORDER (EmailJS)
   ===================================================================== */
const status = $("status");
function setStatus(type, msg){ status.className = "status " + type; status.textContent = msg; }

$("orderForm").addEventListener("submit", async e => {
  e.preventDefault();
  if (!cart.length) return;

  if (CONFIG.EMAILJS_PUBLIC_KEY.startsWith("YOUR_")){
    setStatus("err", "Email is not set up yet. The shop owner needs to add EmailJS keys in the page settings.");
    return;
  }

  const name = $("custName").value.trim();
  const phone = $("custPhone").value.trim();
  const note = $("custNote").value.trim();
  if (!name || !phone){ setStatus("err", "Please enter your name and phone number."); return; }

  const itemsText = cart.map((i, n) =>
    `${n + 1}. ${i.name}  x ${i.qty}  =  ${money(i.price * i.qty)}`).join("\n");

  const params = {
    to_email: CONFIG.OWNER_EMAIL,
    customer_name: name,
    customer_phone: phone,
    customer_note: note || "None",
    order_items: itemsText,
    order_total: money(cartTotal()),
    order_id: "TLS-" + Date.now().toString().slice(-6)
  };

  const btn = $("sendBtn");
  btn.disabled = true; btn.textContent = "Sending…"; status.className = "status";
  try {
    emailjs.init({ publicKey: CONFIG.EMAILJS_PUBLIC_KEY });
    await emailjs.send(CONFIG.EMAILJS_SERVICE_ID, CONFIG.EMAILJS_TEMPLATE_ID, params);
    setStatus("ok", `Thank you, ${name}! Your order ${params.order_id} was sent. We will call you on ${phone} to confirm.`);
    cart = []; saveCart(); renderCart();
    $("orderForm").hidden = false; $("orderForm").reset();
    // keep success message visible while cart is cleared
    $("cartItems").innerHTML = '<p class="empty">Order sent. Thank you!</p>';
    $("sendBtn").hidden = true;
    setTimeout(() => { $("sendBtn").hidden = false; $("orderForm").hidden = true; status.className = "status"; }, 8000);
  } catch (err) {
    console.error(err);
    setStatus("err", "Could not send the order. Check your internet and try again, or message us on WhatsApp.");
  } finally {
    btn.disabled = false; btn.textContent = "Send Order";
  }
});

/* =====================================================================
   MISC
   ===================================================================== */
document.querySelectorAll(".wa-link").forEach(a => {
  a.href = "https://wa.me/" + CONFIG.WHATSAPP_NUMBER + "?text=" + encodeURIComponent("Hi, I'd like to know more about your products.");
});
$("year").textContent = new Date().getFullYear();
const topbar = $("topbar");
const onScroll = () => topbar.classList.toggle("solid", window.scrollY > window.innerHeight * 0.6);
window.addEventListener("scroll", onScroll, {passive:true}); onScroll();
renderCart();
</script>
</body>
</html>
