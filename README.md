# Sri-Raghavendra-bhavana- /  [ index.html        ]<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sri Raghavendra Bhavan - Order Online</title>
    <style>
        :root {
            --primary-color: #e65100;
            --secondary-color: #2e7d32;
            --background-color: #fdfbf7;
            --card-color: #ffffff;
            --text-color: #333333;
            --muted-text: #666666;
            --border-color: #f0eae1;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
            background-color: var(--background-color);
            color: var(--text-color);
            margin: 0;
            padding: 0;
            line-height: 1.6;
        }

        .container {
            max-width: 600px;
            margin: 0 auto;
            padding: 20px 15px 120px 15px;
        }

        /* Header Styles */
        header {
            text-align: center;
            padding: 30px 20px;
            background: var(--card-color);
            border-radius: 16px;
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.04);
            margin-bottom: 25px;
            border: 1px solid var(--border-color);
        }

        h1 {
            margin: 0 0 8px 0;
            color: var(--primary-color);
            font-size: 1.8rem;
            font-weight: 800;
            letter-spacing: -0.5px;
        }

        .tagline {
            font-size: 0.95rem;
            color: var(--muted-text);
            margin-bottom: 15px;
            font-weight: 500;
        }

        .contact-info {
            display: flex;
            justify-content: center;
            gap: 15px;
            flex-wrap: wrap;
            font-size: 0.85rem;
            font-weight: 600;
        }

        .info-tag {
            background: #fff3e0;
            color: #b26a00;
            padding: 6px 12px;
            border-radius: 20px;
            text-decoration: none;
            display: inline-flex;
            align-items: center;
            gap: 5px;
        }

        .info-tag.phone {
            background: #e8f5e9;
            color: var(--secondary-color);
        }

        /* QR Code Container Style */
        .qr-section {
            text-align: center;
            background: #fff8e1;
            border: 2px dashed #ffe082;
            border-radius: 16px;
            padding: 20px;
            margin-bottom: 25px;
        }

        .qr-section p {
            margin: 0 0 12px 0;
            font-weight: bold;
            color: #b26a00;
        }

        .qr-image {
            background: white;
            padding: 8px;
            border-radius: 8px;
            box-shadow: 0 4px 10px rgba(0,0,0,0.05);
        }

        /* Category Section */
        .category-section {
            background: var(--card-color);
            border-radius: 16px;
            padding: 20px;
            margin-bottom: 25px;
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.04);
            border: 1px solid var(--border-color);
        }

        h2 {
            color: var(--primary-color);
            font-size: 1.3rem;
            margin-top: 0;
            margin-bottom: 15px;
            padding-bottom: 8px;
            border-bottom: 2px solid #ffe0b2;
        }

        /* Menu Item Styles with Controls */
        .menu-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 12px 0;
            border-bottom: 1px dashed var(--border-color);
        }

        .menu-item:last-child {
            border-bottom: none;
        }

        .item-details {
            flex-grow: 1;
            padding-right: 15px;
        }

        .item-name {
            font-weight: 600;
            font-size: 1.05rem;
            color: var(--text-color);
            display: block;
        }

        .item-price {
            font-weight: 700;
            font-size: 1rem;
            color: var(--secondary-color);
        }

        /* Quantity Selector Buttons */
        .quantity-controls {
            display: flex;
            align-items: center;
            background: #f5f5f5;
            border-radius: 30px;
            padding: 3px;
        }

        .btn-qty {
            background: white;
            border: 1px solid #ddd;
            color: var(--primary-color);
            width: 28px;
            height: 28px;
            border-radius: 50%;
            font-size: 1.1rem;
            font-weight: bold;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: all 0.2s ease;
            box-shadow: 0 2px 5px rgba(0,0,0,0.05);
        }

        .btn-qty:active {
            transform: scale(0.9);
        }

        .qty-val {
            min-width: 25px;
            text-align: center;
            font-weight: bold;
            font-size: 0.95rem;
        }

        /* Sticky Bottom Cart Bar */
        .cart-bar {
            position: fixed;
            bottom: 0;
            left: 0;
            right: 0;
            background: white;
            box-shadow: 0 -4px 20px rgba(0,0,0,0.1);
            padding: 15px 20px;
            display: none; /* Hidden by default, shows when item added */
            justify-content: space-between;
            align-items: center;
            z-index: 1000;
            border-top: 1px solid var(--border-color);
        }

        .cart-info {
            display: flex;
            flex-direction: column;
        }

        .cart-count {
            font-size: 0.85rem;
            color: var(--muted-text);
            font-weight: bold;
        }

        .cart-total {
            font-size: 1.3rem;
            font-weight: bold;
            color: var(--secondary-color);
        }

        .btn-checkout {
            background: #2e7d32;
            color: white;
            border: none;
            padding: 12px 24px;
            border-radius: 30px;
            font-weight: bold;
            font-size: 1rem;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 8px;
            box-shadow: 0 4px 10px rgba(46, 125, 50, 0.3);
        }

        .btn-checkout:hover {
            background: #276b2b;
        }

        footer {
            text-align: center;
            padding: 20px;
            font-size: 0.85rem;
            color: var(--muted-text);
        }
    </style>
</head>
<body>

<div class="container">
    <header>
        <h1>Sri Raghavendra Bhavan</h1>
        <div class="tagline">Delicious & Fresh Vegetarian Food</div>
        <div class="contact-info">
            <span class="info-tag">📍 Malebennur</span>
            <a href="tel:8095004556" class="info-tag phone">📞 Call: 8095004556</a>
        </div>
    </header>

    <!-- QR Code Section -->
    <div class="qr-section">
        <p>📲 Scan or Share Our Menu!</p>
        <img class="qr-image" src="https://api.qrserver.com/v1/create-qr-code/?size=150x150&data=https://skandahollavr-dev.github.io/Sri-Raghavendra-bhavana-/" alt="QR Code" width="150" height="150">
    </div>

    <!-- Breakfast & Main Dishes -->
    <div class="category-section">
        <h2>Breakfast & Main Dishes</h2>
        
        <div class="menu-item" data-id="masala-dosa" data-name="Masala Dosa" data-price="50">
            <div class="item-details">
                <span class="item-name">Masala Dosa</span>
                <span class="item-price">₹50</span>
            </div>
            <div class="quantity-controls">
                <button class="btn-qty minus">-</button>
                <span class="qty-val">0</span>
                <button class="btn-qty plus">+</button>
            </div>
        </div>

        <div class="menu-item" data-id="open-dosa" data-name="Open Dosa (Butter Masala)" data-price="60">
            <div class="item-details">
                <span class="item-name">Open Dosa (Butter Masala)</span>
                <span class="item-price">₹60</span>
            </div>
            <div class="quantity-controls">
                <button class="btn-qty minus">-</button>
                <span class="qty-val">0</span>
                <button class="btn-qty plus">+</button>
            </div>
        </div>

        <div class="menu-item" data-id="set-dosa" data-name="Set Dosa" data-price="50">
            <div class="item-details">
                <span class="item-name">Set Dosa</span>
                <span class="item-price">₹50</span>
            </div>
            <div class="quantity-controls">
                <button class="btn-qty minus">-</button>
                <span class="qty-val">0</span>
                <button class="btn-qty plus">+</button>
            </div>
        </div>

        <div class="menu-item" data-id="poori" data-name="Poori" data-price="40">
            <div class="item-details">
                <span class="item-name">Poori</span>
                <span class="item-price">₹40</span>
            </div>
            <div class="quantity-controls">
                <button class="btn-qty minus">-</button>
                <span class="qty-val">0</span>
                <button class="btn-qty plus">+</button>
            </div>
        </div>

        <div class="menu-item" data-id="idli-vada" data-name="Idli Vada" data-price="40">
            <div class="item-details">
                <span class="item-name">Idli Vada</span>
                <span class="item-price">₹40</span>
            </div>
            <div class="quantity-controls">
                <button class="btn-qty minus">-</button>
                <span class="qty-val">0</span>
                <button class="btn-qty plus">+</button>
            </div>
        </div>

        <div class="menu-item" data-id="meals" data-name="Meals" data-price="80">
            <div class="item-details">
                <span class="item-name">Meals</span>
                <span class="item-price">₹80</span>
            </div>
            <div class="quantity-controls">
                <button class="btn-qty minus">-</button>
                <span class="qty-val">0</span>
                <button class="btn-qty plus">+</button>
            </div>
        </div>
    </div>

    <!-- Bath & Rice Varieties -->
    <div class="category-section">
        <h2>Bath & Rice Varieties</h2>
        
        <div class="menu-item" data-id="upma-kesari" data-name="Upma Kesari Bath" data-price="40">
            <div class="item-details">
                <span class="item-name">Upma Kesari Bath</span>
                <span class="item-price">₹40</span>
            </div>
            <div class="quantity-controls">
                <button class="btn-qty minus">-</button>
                <span class="qty-val">0</span>
                <button class="btn-qty plus">+</button>
            </div>
        </div>

        <div class="menu-item" data-id="chitranna" data-name="Chitranna" data-price="40">
            <div class="item-details">
                <span class="item-name">Chitranna</span>
                <span class="item-price">₹40</span>
            </div>
            <div class="quantity-controls">
                <button class="btn-qty minus">-</button>
                <span class="qty-val">0</span>
                <button class="btn-qty plus">+</button>
            </div>
        </div>

        <div class="menu-item" data-id="palav" data-name="Palav" data-price="40">
            <div class="item-details">
                <span class="item-name">Palav</span>
                <span class="item-price">₹40</span>
            </div>
            <div class="quantity-controls">
                <button class="btn-qty minus">-</button>
                <span class="qty-val">0</span>
                <button class="btn-qty plus">+</button>
            </div>
        </div>
    </div>

    <!-- Beverages -->
    <div class="category-section">
        <h2>Beverages</h2>
        
        <div class="menu-item" data-id="tea-coffee" data-name="Tea / Coffee" data-price="5">
            <div class="item-details">
                <span class="item-name">Tea / Coffee</span>
                <span class="item-price">₹5</span>
            </div>
            <div class="quantity-controls">
                <button class="btn-qty minus">-</button>
                <span class="qty-val">0</span>
                <button class="btn-qty plus">+</button>
            </div>
        </div>

        <div class="menu-item" data-id="badam-milk" data-name="Nandini Badam Milk" data-price="25">
            <div class="item-details">
                <span class="item-name">Nandini Badam Milk</span>
                <span class="item-price">₹25</span>
            </div>
            <div class="quantity-controls">
                <button class="btn-qty minus">-</button>
                <span class="qty-val">0</span>
                <button class="btn-qty plus">+</button>
            </div>
        </div>
    </div>

    <footer>
        <p>© 2026 Sri Raghavendra Bhavan. All Rights Reserved.</p>
    </footer>
</div>

<!-- Sticky Bottom Cart Bar -->
<div class="cart-bar" id="cartBar">
    <div class="cart-info">
        <span class="cart-count" id="cartCount">0 Items Selected</span>
        <span class="cart-total" id="cartTotal">₹0</span>
    </div>
    <button class="btn-checkout" onclick="sendWhatsAppOrder()">
        <span>Order on WhatsApp</span> 📲
    </button>
</div>

<script>
    // Cart object to store items ordered
    const cart = {};
    const shopPhoneNumber = "918095004556"; // Your WhatsApp Number (including country code 91)

    // Select all plus and minus buttons
    document.querySelectorAll('.menu-item').forEach(item => {
        const id = item.getAttribute('data-id');
        const name = item.getAttribute('data-name');
        const price = parseInt(item.getAttribute('data-price'));
        const qtyVal = item.querySelector('.qty-val');
        
        const btnPlus = item.querySelector('.plus');
        const btnMinus = item.querySelector('.minus');

        btnPlus.addEventListener('click', () => {
            if (!cart[id]) {
                cart[id] = { name: name, price: price, qty: 0 };
            }
            cart[id].qty++;
            qtyVal.innerText = cart[id].qty;
            updateCart();
        });

        btnMinus.addEventListener('click', () => {
            if (cart[id] && cart[id].qty > 0) {
                cart[id].qty--;
                qtyVal.innerText = cart[id].qty;
                if (cart[id].qty === 0) {
                    delete cart[id];
                }
                updateCart();
            }
        });
    });

    // Update sticky cart calculations
    function updateCart() {
        let totalQty = 0;
        let totalPrice = 0;

        for (const id in cart) {
            totalQty += cart[id].qty;
            totalPrice += cart[id].price * cart[id].qty;
        }

        const cartBar = document.getElementById('cartBar');
        const cartCount = document.getElementById('cartCount');
        const cartTotal = document.getElementById('cartTotal');

        if (totalQty > 0) {
            cartBar.style.display = 'flex';
            cartCount.innerText = totalQty + " Item" + (totalQty > 1 ? "s" : "") + " Selected";
            cartTotal.innerText = "₹" + totalPrice;
        } else {
            cartBar.style.display = 'none';
        }
    }

    // Format order and open WhatsApp
    function sendWhatsAppOrder() {
        let orderText = "*🟢 NEW ORDER FROM WEBSITE*\n";
        orderText += "-------------------------------\n";
        
        let grandTotal = 0;
        for (const id in cart) {
            const item = cart[id];
            const itemTotal = item.price * item.qty;
            orderText += `• ${item.qty} x *${item.name}* (₹${itemTotal})\n`;
            grandTotal += itemTotal;
        }

        orderText += "-------------------------------\n";
        orderText += `*Total Bill: ₹${grandTotal}*\n\n`;
        orderText += "_Please prepare my order!_";

        // URL encode the text so WhatsApp can read it
        const encodedText = encodeURIComponent(orderText);
        
        // Open user's WhatsApp directly on their phone
        window.open(`https://wa.me/${shopPhoneNumber}?text=${encodedText}`, '_blank');
    }
</script>

</body>
</html>

