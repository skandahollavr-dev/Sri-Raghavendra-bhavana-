
<div id="food-app" style="font-family:Arial,sans-serif;max-width:1000px;margin:auto;color:#222">
  <header style="background:#fc8019;color:white;padding:22px;border-radius:14px">
    <h1 style="margin:0">🍴 Our Food Corner</h1>
    <p>Delicious food, delivered to your door!</p>
    <a href="https://menu.khide.in/590595044" target="_blank" rel="noopener"
       style="display:inline-block;background:white;color:#fc8019;padding:10px 14px;border-radius:7px;text-decoration:none;font-weight:bold">
       View Our Full Menu
    </a>
  </header>

  <input id="food-search" placeholder="🔍 Search food..."
    style="box-sizing:border-box;width:100%;padding:13px;margin:18px 0;border:1px solid #ddd;border-radius:9px">

  <div id="food-categories" style="display:flex;gap:8px;flex-wrap:wrap"></div>
  <div id="food-list" style="display:grid;grid-template-columns:repeat(auto-fit,minmax(155px,1fr));gap:12px;margin:18px 0"></div>

  <section style="background:#fff7ef;padding:16px;border-radius:12px">
    <h2>🛒 Your Cart (<span id="food-count">0</span>)</h2>
    <div id="food-cart">Your cart is empty.</div>
    <h3 id="food-total">Total: ₹0</h3>
    <button id="food-checkout" style="background:#fc8019;color:white;padding:12px 18px;border:0;border-radius:8px">
      Proceed to Checkout
    </button>
  </section>

  <section id="food-details" style="display:none;padding:16px">
    <h2>Delivery Details</h2>
    <input id="food-name" placeholder="Customer name" style="box-sizing:border-box;width:100%;padding:12px;margin:5px 0">
    <input id="food-phone" placeholder="Phone number" type="tel" style="box-sizing:border-box;width:100%;padding:12px;margin:5px 0">
    <textarea id="food-address" placeholder="Full delivery address" style="box-sizing:border-box;width:100%;padding:12px;margin:5px 0"></textarea>
    <p><b>Payment method:</b> Cash on Delivery</p>
    <button id="food-place" style="background:#16803c;color:white;padding:12px 18px;border:0;border-radius:8px">
      Place Order
    </button>
    <p id="food-result"></p>
  </section>
</div>

<script>
(function () {
  // SAMPLE MENU: replace these items and prices with your actual menu.
  const foods = [
    {id:1,name:"Masala Dosa",price:119,category:"South Indian",emoji:"🥞"},
    {id:2,name:"Idli Vada",price:80,category:"South Indian",emoji:"🍽️"},
    {id:3,name:"Veg Burger",price:149,category:"Fast Food",emoji:"🍔"},
    {id:4,name:"French Fries",price:99,category:"Fast Food",emoji:"🍟"},
    {id:5,name:"Veg Pizza",price:229,category:"Fast Food",emoji:"🍕"},
    {id:6,name:"Cold Coffee",price:89,category:"Drinks",emoji:"🥤"}
  ];

  const cart = {};
  let category = "All";
  const el = id => document.getElementById(id);
  const rupees = n => "₹" + n.toFixed(2).replace(/\.00$/,"");

  function renderCategories() {
    const categories = ["All", ...new Set(foods.map(f => f.category))];
    el("food-categories").innerHTML = categories.map(c =>
      `<button data-category="${c}" style="padding:9px 13px;border:0;border-radius:20px;background:${c===category?"#fc8019":"#eee"};color:${c===category?"white":"#222"}">${c}</button>`
    ).join("");
  }

  function renderFoods() {
    const query = el("food-search").value.toLowerCase();
    el("food-list").innerHTML = foods
      .filter(f => (category==="All" || f.category===category) &&
        f.name.toLowerCase().includes(query))
      .map(f => `<article style="border:1px solid #eee;padding:14px;border-radius:12px">
        <div style="font-size:38px">${f.emoji}</div>
        <b>${f.name}</b>
        <p>${f.category}</p>
        <strong>${rupees(f.price)}</strong><br>
        <button data-add="${f.id}" style="margin-top:10px;padding:9px 14px;border:0;border-radius:7px;background:#fc8019;color:white">+ Add</button>
      </article>`).join("") || "<p>No food found.</p>";
  }

  function renderCart() {
    const items = foods.filter(f => cart[f.id]);
    const count = items.reduce((s,f) => s + cart[f.id],0);
    const total = items.reduce((s,f) => s + f.price * cart[f.id],0);
    el("food-count").textContent = count;
    el("food-total").textContent = "Total: " + rupees(total);
    el("food-cart").innerHTML = items.length ? items.map(f =>
      `<p>${f.name} × ${cart[f.id]} — ${rupees(f.price*cart[f.id])}
      <button data-minus="${f.id}">−</button>
      <button data-plus="${f.id}">+</button></p>`
    ).join("") : "Your cart is empty.";
    return total;
  }

  el("food-app").addEventListener("click", e => {
    const b = e.target.closest("button");
    if (!b) return;

    if (b.dataset.category) {
      category = b.dataset.category;
      renderCategories(); renderFoods();
    } else if (b.dataset.add) {
      cart[b.dataset.add] = (cart[b.dataset.add] || 0) + 1;
      renderCart();
    } else if (b.dataset.plus) {
      cart[b.dataset.plus] = (cart[b.dataset.plus] || 0) + 1;
      renderCart();
    } else if (b.dataset.minus) {
      cart[b.dataset.minus]--;
      if (cart[b.dataset.minus] <= 0) delete cart[b.dataset.minus];
      renderCart();
    } else if (b.id === "food-checkout") {
      if (renderCart() === 0) {
        alert("Please add food to your cart first.");
        return;
      }
      el("food-details").style.display = "block";
      el("food-details").scrollIntoView({behavior:"smooth"});
    } else if (b.id === "food-place") {
      if (!renderCart()) {
        alert("Your cart is empty."); return;
      }
      const name = el("food-name").value.trim();
      const phone = el("food-phone").value.trim();
      const address = el("food-address").value.trim();
      if (!name || !/^[0-9+\-\s()]{8,16}$/.test(phone) || !address) {
        alert("Please enter your name, valid phone number and delivery address.");
        return;
      }
      el("food-result").textContent =
        "Demo only: no order has been sent to the restaurant. Connect an order backend to receive real orders.";
    }
  });

  el("food-search").addEventListener("input", renderFoods);
  renderCategories();
  renderFoods();
  renderCart();
})();
</script>

