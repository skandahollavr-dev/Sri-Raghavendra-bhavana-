<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <title>Sri Raghavendra Bhavana | Order Online</title>

  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      font-family: Arial, sans-serif;
      background: #f7f7f7;
      color: #222;
      padding-bottom: 90px;
    }

    /* HEADER */
    header {
      position: sticky;
      top: 0;
      z-index: 1000;
      background: white;
      padding: 14px 18px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      box-shadow: 0 2px 10px rgba(0,0,0,.08);
    }

    .brand {
      display: flex;
      align-items: center;
      gap: 10px;
    }

    .logo {
      width: 45px;
      height: 45px;
      border-radius: 50%;
      background: #111;
      color: #d4af37;
      display: flex;
      align-items: center;
      justify-content: center;
      font-weight: bold;
      font-size: 13px;
    }

    .brand h2 {
      font-size: 17px;
    }

    .brand p {
      font-size: 11px;
      color: #777;
      margin-top: 3px;
    }

    .cart-button {
      background: #16833b;
      color: white;
      border: none;
      border-radius: 10px;
      padding: 10px 14px;
      font-weight: bold;
      cursor: pointer;
    }

    /* HERO */
    .hero {
      background: linear-gradient(135deg,#151515,#3c3c3c);
      color: white;
      padding: 30px 20px;
    }

    .hero h1 {
      font-size: 30px;
      margin: 10px 0;
    }

    .hero p {
      color: #ddd;
      font-size: 14px;
    }

    .table-badge {
      display: inline-block;
      background: #d4af37;
      color: #111;
      padding: 8px 13px;
      border-radius: 8px;
      font-weight: bold;
      margin-top: 15px;
      font-size: 13px;
    }

    /* CATEGORY BAR */
    .categories {
      position: sticky;
      top: 74px;
      z-index: 900;
      background: white;
      display: flex;
      gap: 8px;
      overflow-x: auto;
      padding: 12px;
      border-bottom: 1px solid #eee;
    }

    .categories button {
      white-space: nowrap;
      padding: 9px 15px;
      border: 1px solid #ddd;
      background: white;
      border-radius: 20px;
      cursor: pointer;
    }

    .categories button.active {
      background: #111;
      color: white;
    }

    /* MENU */
    main {
      max-width: 1000px;
      margin: auto;
      padding: 10px 15px;
    }

    .category {
      margin-bottom: 28px;
    }

    .category h2 {
      font-size: 21px;
      margin: 15px 0;
    }

    .menu-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit,minmax(220px,1fr));
      gap: 12px;
    }

    .food-card {
      background: white;
      border-radius: 15px;
      padding: 15px;
      border: 1px solid #eee;
      box-shadow: 0 2px 8px rgba(0,0,0,.04);
    }

    .food-card h3 {
      font-size: 16px;
      margin-bottom: 8px;
    }

    .food-card p {
      color: #777;
      font-size: 12px;
    }

    .food-bottom {
      margin-top: 15px;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    .price {
      font-weight: bold;
      font-size: 16px;
    }

    .add-btn {
      border: 1px solid #16833b;
      color: #16833b;
      background: white;
      border-radius: 8px;
      padding: 7px 16px;
      font-weight: bold;
      cursor: pointer;
    }

    .quantity {
      display: flex;
      align-items: center;
      gap: 10px;
      border: 1px solid #ddd;
      padding: 4px;
      border-radius: 8px;
    }

    .quantity button {
      width: 27px;
      height: 27px;
      border: none;
      background: white;
      font-size: 18px;
      cursor: pointer;
    }

    /* CART BAR */
    .cart-bar {
      position: fixed;
      bottom: 15px;
      left: 50%;
      transform: translateX(-50%);
      width: min(650px,calc(100% - 24px));
      background: #16833b;
      color: white;
      border-radius: 14px;
      padding: 13px 17px;
      display: none;
      justify-content: space-between;
      align-items: center;
      z-index: 2000;
      box-shadow: 0 7px 30px rgba(0,0,0,.3);
      cursor: pointer;
    }

    .cart-bar small {
      display: block;
      color: #d8f5df;
      margin-top: 3px;
    }

    /* OVERLAY */
    .overlay {
      position: fixed;
      inset: 0;
      background: rgba(0,0,0,.65);
      display: none;
      z-index: 3000;
    }

    .overlay.show {
      display: block;
    }

    /* CART DRAWER */
    .cart-drawer {
      position: fixed;
      right: -500px;
      top: 0;
      height: 100%;
      width: min(470px,100%);
      background: white;
      z-index: 4000;
      transition: .3s;
      padding: 20px;
      display: flex;
      flex-direction: column;
    }

    .cart-drawer.open {
      right: 0;
    }

    .cart-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 15px;
    }

    .close-btn {
      border: none;
      background: #eee;
      border-radius: 50%;
      width: 35px;
      height: 35px;
      cursor: pointer;
    }

    #cartItems {
      overflow-y: auto;
    }

    .cart-item {
      display: flex;
      justify-content: space-between;
      padding: 14px 0;
      border-bottom: 1px solid #eee;
    }

    .cart-item small {
      display: block;
      color: #777;
      margin-top: 5px;
    }

    .cart-controls {
      display: flex;
      align-items: center;
      gap: 7px;
    }

    .cart-controls button {
      border: 1px solid #ddd;
      background: white;
      width: 28px;
      height: 28px;
      border-radius: 6px;
      cursor: pointer;
    }

    .bill {
      margin-top: auto;
      border-top: 1px solid #ddd;
      padding-top: 15px;
    }

    .bill-row {
      display: flex;
      justify-content: space-between;
      margin: 8px 0;
    }

    .bill-total {
      font-size: 19px;
      font-weight: bold;
    }

    .primary-btn {
      width: 100%;
      background: #16833b;
      color: white;
      border: none;
      padding: 14px;
      border-radius: 10px;
      font-size: 15px;
      font-weight: bold;
      margin-top: 12px;
      cursor: pointer;
    }

    /* MODAL */
    .modal {
      position: fixed;
      inset: 0;
      background: rgba(0,0,0,.7);
      display: none;
      align-items: center;
      justify-content: center;
      padding: 15px;
      z-index: 5000;
    }

    .modal.show {
      display: flex;
    }

    .modal-box {
      width: min(500px,100%);
      max-height: 92vh;
      overflow-y: auto;
      background: white;
      border-radius: 18px;
      padding: 22px;
      position: relative;
    }

    .modal-box h2 {
      margin-bottom: 15px;
    }

    .modal-close {
      position: absolute;
      right: 15px;
      top: 15px;
      border: none;
      background: #eee;
      border-radius: 50%;
      width: 35px;
      height: 35px;
      cursor: pointer;
    }

    label {
      display: block;
      margin-top: 13px;
      font-size: 13px;
      font-weight: bold;
    }

    input,
    select,
    textarea {
      width: 100%;
      margin-top: 6px;
      padding: 12px;
      border: 1px solid #ddd;
      border-radius: 9px;
      font-size: 14px;
    }

    textarea {
      min-height: 75px;
      resize: vertical;
    }

    .checkout-summary {
      background: #f7f7f7;
      padding: 12px;
      border-radius: 10px;
      margin-bottom: 10px;
    }

    .summary-row {
      display: flex;
      justify-content: space-between;
      margin: 6px 0;
      font-size: 13px;
    }

    /* SUCCESS */
    .success {
      text-align: center;
    }

    .success-icon {
      width: 70px;
      height: 70px;
      background: #e5f7ea;
      color: #16833b;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 40px;
      margin: auto;
    }

    .order-number {
      font-size: 30px;
      font-weight: bold;
      margin: 12px;
      letter-spacing: 2px;
    }

    .empty {
      text-align: center;
      color: #777;
      padding: 35px 10px;
    }

    @media(max-width:600px) {
      .hero h1 {
        font-size: 26px;
      }

      .menu-grid {
        grid-template-columns: 1fr;
      }
    }
  </style>
</head>

<body>

<!-- HEADER -->
<header>
  <div class="brand">
    <div class="logo">SRB</div>
    <div>
      <h2>Sri Raghavendra Bhavana</h2>
      <p>Fresh • Tasty • Fast</p>
    </div>
  </div>

  <button class="cart-button" onclick="openCart()">
    🛒 <span id="headerCount">0</span>
  </button>
</header>

<!-- HERO -->
<section class="hero">
  <h1>Order your favourites 🍽️</h1>
  <p>Choose your food and place your order directly from your table.</p>

  <div class="table-badge" id="tableBadge">
    Select your table
  </div>
</section>

<!-- CATEGORIES -->
<nav class="categories" id="categories"></nav>

<!-- MENU -->
<main id="menu"></main>

<!-- BOTTOM CART -->
<div class="cart-bar" id="cartBar" onclick="openCart()">
  <div>
    <b><span id="cartCount">0</span> items</b>
    <small>View your cart</small>
  </div>

  <strong>
    ₹<span id="cartTotal">0</span> →
  </strong>
</div>

<!-- OVERLAY -->
<div class="overlay" id="overlay" onclick="closeCart()"></div>

<!-- CART DRAWER -->
<aside class="cart-drawer" id="cartDrawer">

  <div class="cart-header">
    <h2>Your Cart</h2>
    <button class="close-btn" onclick="closeCart()">✕</button>
  </div>

  <div id="cartItems"></div>

  <div class="bill" id="bill"></div>

  <button
    class="primary-btn"
    id="checkoutButton"
    onclick="openCheckout()">
    Proceed to Checkout
  </button>

</aside>

<!-- CHECKOUT MODAL -->
<div class="modal" id="checkoutModal">

  <div class="modal-box">

    <button class="modal-close" onclick="closeCheckout()">✕</button>

    <h2>Checkout</h2>

    <div class="checkout-summary" id="checkoutSummary"></div>

    <label>
      Customer Name
      <input
        type="text"
        id="customerName"
        placeholder="Enter your name">
    </label>

    <label>
      Mobile Number
      <input
        type="tel"
        id="customerPhone"
        maxlength="10"
        placeholder="10-digit mobile number">
    </label>

    <label>
      Table Number
      <select id="tableSelect"></select>
    </label>

    <label>
      Payment Method
      <select id="paymentMethod">
        <option>Pay at Hotel (Cash)</option>
      </select>
    </label>

    <label>
      Special Instructions
      <textarea
        id="notes"
        placeholder="Example: Less spicy, extra chutney..."></textarea>
    </label>

    <button class="primary-btn" onclick="placeOrder()">
      🛍️ Place Order
    </button>

    <p style="text-align:center;color:#777;font-size:12px;margin-top:10px">
      No online payment required.
    </p>

  </div>

</div>

<!-- SUCCESS MODAL -->
<div class="modal" id="successModal">

  <div class="modal-box success">

    <div class="success-icon">✓</div>

    <h2 style="margin-top:15px">
      Order Placed!
    </h2>

    <p>Your order number is</p>

    <div class="order-number" id="orderNumber"></div>

    <p id="successMessage"></p>

    <button class="primary-btn" onclick="closeSuccess()">
      Done
    </button>

  </div>

</div>

<script>

  /* =========================
     MENU
  ========================= */

  const MENU = [

    ["Breakfast","Masala Dosa",50],
    ["Breakfast","Open Dosa",60],
    ["Breakfast","Khali Dosa",45],
    ["Breakfast","Onion Dosa",70],
    ["Breakfast","Set Dosa",50],
    ["Breakfast","Poori",40],
    ["Breakfast","Idli",25],
    ["Breakfast","Upma",25],
    ["Breakfast","Kesari Bath",25],
    ["Breakfast","Upma Kesari Bath",40],
    ["Breakfast","Idli Vada",40],
    ["Breakfast","Chapati",50],
    ["Breakfast","Single Chapati",25],
    ["Breakfast","Single Khali Dosa",25],
    ["Breakfast","Single Poori",20],
    ["Breakfast","Single Idli",15],
    ["Breakfast","Single Idli Vada",30],

    ["Rice & Meals","Chitranna",40],
    ["Rice & Meals","Curd Rice",40],
    ["Rice & Meals","Puliyogare",40],
    ["Rice & Meals","Palav",40],
    ["Rice & Meals","Meals",80],
    ["Rice & Meals","Rice",50],
    ["Rice & Meals","Half Curd Rice",25],
    ["Rice & Meals","Half Chitranna",25],
    ["Rice & Meals","Half Palav",25],
    ["Rice & Meals","Half Puliyogare",25],

    ["Snacks","Mixture",40],
    ["Snacks","Pakoda",40],
    ["Snacks","Plate Jilebi",20],
    ["Snacks","Jilebi",10],
    ["Snacks","Gulab Jamun",15],
    ["Snacks","Avalakki Sev",40],
    ["Snacks","Mirchi",5],
    ["Snacks","Vada",15],
    ["Snacks","Half Pakoda",20],

    ["Curd","Curd Vada",35],

    ["Beverages","Coffee",5],
    ["Beverages","Tea",5],
    ["Beverages","Maaza Glass",15],
    ["Beverages","Fanta Glass",15],
    ["Beverages","Fanta",20],
    ["Beverages","Mazaa",20],
    ["Beverages","Sprite",20],
    ["Beverages","Sprite Glass",15],
    ["Beverages","Limca Glass",15],
    ["Beverages","Bindu Jeera",15],
    ["Beverages","Mirinda",20],
    ["Beverages","Nandini Badam Milk",25],
    ["Beverages","Pineapple Juice",15],
    ["Beverages","Sipon Orange",15],
    ["Beverages","Chill Mill",10],
    ["Beverages","Butter Milk",15],
    ["Beverages","Water 500ml",10],
    ["Beverages","Water 1L",20],
    ["Beverages","Water 2L",30],
    ["Beverages","Sting",20],
    ["Beverages","Thums Up Glass",15],
    ["Beverages","Sipon Tender Water",20],
    ["Beverages","Sprite 400ml",40],

    ["Ice Creams","10 Rs Ice Cream",10],
    ["Ice Creams","20 Rs Ice Cream",20],
    ["Ice Creams","25 Rs Ice Cream",25],
    ["Ice Creams","30 Rs Ice Cream",30],
    ["Ice Creams","40 Rs Ice Cream",40],

    ["Packed Items","Jilebi 250g",70],
    ["Packed Items","Mixture 250g",70]

  ];


  /* =========================
     CART
  ========================= */

  let cart =
    JSON.parse(localStorage.getItem("srb_cart") || "{}");


  /* =========================
     TABLE FROM QR
  ========================= */

  const params =
    new URLSearchParams(window.location.search);

  let tableNumber = params.get("table") || "";


  /* =========================
     INITIALIZE
  ========================= */

  function initialize() {

    createCategories();

    createTableOptions();

    updateTableDisplay();

    renderMenu();

    renderCart();

  }


  /* =========================
     CATEGORIES
  ========================= */

  const categories =
    [...new Set(MENU.map(item => item[0]))];


  function createCategories() {

    let html =
      `<button class="active"
      onclick="showAll(this)">All</button>`;

    categories.forEach(category => {

      html += `
        <button onclick="showCategory('${escapeText(category)}',this)">
          ${category}
        </button>
      `;

    });

    document.getElementById("categories").innerHTML = html;

  }


  /* =========================
     MENU
  ========================= */

  function renderMenu(filter = null) {

    const groups =
      filter ? [filter] : categories;

    let html = "";

    groups.forEach(category => {

      const items =
        MENU.filter(item => item[0] === category);

      html += `
        <section class="category">

          <h2>${category}</h2>

          <div class="menu-grid">

            ${items.map(createFoodCard).join("")}

          </div>

        </section>
      `;

    });

    document.getElementById("menu").innerHTML = html;

  }


  function createFoodCard(item) {

    const name = item[1];
    const price = item[2];

    const quantity =
      cart[name] ? cart[name].qty : 0;

    let action;

    if (quantity > 0) {

      action = `
        <div class="quantity">

          <button onclick="changeQuantity('${escapeText(name)}',-1)">
            −
          </button>

          <b>${quantity}</b>

          <button onclick="changeQuantity('${escapeText(name)}',1)">
            +
          </button>

        </div>
      `;

    } else {

      action = `
        <button
          class="add-btn"
          onclick="addToCart('${escapeText(name)}',${price})">
          ADD
        </button>
      `;

    }

    return `
      <div class="food-card">

        <h3>${name}</h3>

        <p>Freshly prepared • Dine-in</p>

        <div class="food-bottom">

          <span class="price">
            ₹${price}
          </span>

          ${action}

        </div>

      </div>
    `;

  }


  /* =========================
     CART FUNCTIONS
  ========================= */

  function addToCart(name,price) {

    if (!cart[name]) {

      cart[name] = {
        price: price,
        qty: 0
      };

    }

    cart[name].qty++;

    saveCart();

    renderMenu();

    renderCart();

  }


  function changeQuantity(name,amount) {

    if (!cart[name]) return;

    cart[name].qty += amount;

    if (cart[name].qty <= 0) {

      delete cart[name];

    }

    saveCart();

    renderMenu();

    renderCart();

  }


  function saveCart() {

    localStorage.setItem(
      "srb_cart",
      JSON.stringify(cart)
    );

  }


  function calculateTotal() {

    let total = 0;

    Object.values(cart).forEach(item => {

      total += item.price * item.qty;

    });

    return total;

  }


  function calculateCount() {

    let count = 0;

    Object.values(cart).forEach(item => {

      count += item.qty;

    });

    return count;

  }


  function renderCart() {

    const count =
      calculateCount();

    const total =
      calculateTotal();

    document.getElementById("headerCount")
      .textContent = count;

    document.getElementById("cartCount")
      .textContent = count;

    document.getElementById("cartTotal")
      .textContent = total;


    const bar =
      document.getElementById("cartBar");

    bar.style.display =
      count > 0 ? "flex" : "none";


    const container =
      document.getElementById("cartItems");


    if (count === 0) {

      container.innerHTML = `
        <div class="empty">
          Your cart is empty 🍽️
          <br><br>
          Add something delicious!
        </div>
      `;

      document.getElementById("bill").innerHTML = "";

      return;

    }


    let html = "";

    Object.entries(cart).forEach(([name,item]) => {

      html += `
        <div class="cart-item">

          <div>

            <b>${name}</b>

            <small>
              ₹${item.price} × ${item.qty}
              = ₹${item.price * item.qty}
            </small>

          </div>

          <div class="cart-controls">

            <button
              onclick="changeQuantity('${escapeText(name)}',-1)">
              −
            </button>

            <b>${item.qty}</b>

            <button
              onclick="changeQuantity('${escapeText(name)}',1)">
              +
            </button>

          </div>

        </div>
      `;

    });

    container.innerHTML = html;


    document.getElementById("bill").innerHTML = `

      <div class="bill-row">
        <span>Item Total</span>
        <b>₹${total}</b>
      </div>

      <div class="bill-row bill-total">
        <span>To Pay</span>
        <b>₹${total}</b>
      </div>

    `;

  }


  /* =========================
     CART DRAWER
  ========================= */

  function openCart() {

    document
      .getElementById("overlay")
      .classList.add("show");

    document
      .getElementById("cartDrawer")
      .classList.add("open");

  }


  function closeCart() {

    document
      .getElementById("overlay")
      .classList.remove("show");

    document
      .getElementById("cartDrawer")
      .classList.remove("open");

  }


  /* =========================
     CHECKOUT
  ========================= */

  function openCheckout() {

    if (calculateCount() === 0) {

      alert("Your cart is empty.");

      return;

    }

    closeCart();

    let html = "";

    Object.entries(cart).forEach(([name,item]) => {

      html += `
        <div class="summary-row"
