# Sri-Raghavendra-bhavana- /  [ index.html        ]
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sri Raghavendra Bhavan - Order Online</title>
    <!-- QR Code Scanner Library -->
    <script src="https://unpkg.com/html5-qrcode"></script>
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

        /* Table Number Indicator */
        .table-badge {
            background: #e0f2f1;
            color: #00695c;
            font-weight: 800;
            padding: 8px 16px;
            border-radius: 20px;
            display: inline-block;
            margin-top: 15px;
            font-size: 1rem;
            border: 1px solid #b2dfdb;
            cursor: pointer;
        }

        /* QR Scanner Section styling */
        .scanner-section {
            background: #efebe9;
            border-radius: 16px;
            padding: 15px;
            margin-bottom: 25px;
            text-align: center;
            border: 1px solid #d7ccc8;
        }

        .btn-scanner {
            background: #4e342e;
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 30px;
            font-weight: bold;
            font-size: 0.95rem;
            cursor: pointer;
            display: inline-flex;
            align-items: center;
            gap: 8px;
            box-shadow: 0 4px 10px rgba(78, 52, 46, 0.2);
        }

        #reader {
            width: 100%;
            max-width: 350px;
            margin: 15px auto 0 auto;
            border-radius: 12px;
            overflow: hidden;
            display: none;
            background: white;
        }

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

        .cart-bar {
            position: fixed;
            bottom: 0;
            left: 0;
            right: 0;
            background: white;
            box-shadow: 0 -4px 20px rgba(0,0,0,0.1);
            padding: 15px 20px;
            display: none;
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
        <!-- Table Number Badge -->
        <div class="table-badge" id="tableBadge" onclick="askTableNumber()">
            🍽️ Table: <span id="tableNo">Not Set</span> (Tap to Change)
        </div>
    </header>

    <!-- QR Code Scanner Feature -->
    <div class="scanner-section">
        <button class="btn-scanner" id="scanBtn" onclick="toggleScanner()">📷 Scan Table QR</button>
        <div id="reader"></div>
    </div>

    <!-- 1. DOSA & BREAKFAST ITEMS -->
    <div class="category-section">
        <h2>Dosa & Breakfast</h2>
        
        <div class="menu-item" data-id="masala-dosa" data-name="Masala Dosa" data-price="50">
            <div class="item-details"><span class="item-name">Masala Dosa</span><span class="item-price">₹50</span></div>
            <div class="quantity-controls"><button class="btn-qty minus">-</button><span class="qty-val">0</span><button class="btn-qty plus">+</button></div>
        </div>
        
        <div class="menu-item" data-id="open-dosa" data-name="Open Dosa" data-price="60">
            <div class="item-details"><span class="item-name">Open Dosa</span><span class="item-price">₹60</span></div>
            <div class="quantity-controls"><button class="btn-qty minus">-</button><span class="qty-val">0</span><button class="btn-qty plus">+</button></div>
        </div>

        <div class="menu-item" data-id="khali-dosa" data-name="Khali Dosa" data-price="45">
            <div class="item-details"><span class="item-name">Khali Dosa</span><span class="item-price">₹45</span></div>
            <div class="quantity-controls"><button class="btn-qty minus">-</button><span class="qty-val">0</span><button class="btn-qty plus">+</button></div>
        </div>

        <div class="menu-item" data-id="onion-dosa" data-name="Onion Dosa" data-price="70">
            <div class="item-details"><span class="item-name">Onion Dosa</span><span class="item-price">₹70</span></div>
            <div class="quantity-controls"><button class="btn-qty minus">-</button><span class="qty-val">0</span><button class="btn-qty plus">+</button></div>
        </div>

        <div class="menu-item" data-id="set-dosa" data-name="Set Dosa" data-price="50">
            <div class="item-details"><span class="item-name">Set Dosa</span><span class="item-price">₹50</span></div>
            <div class="quantity-controls"><button class="btn-qty minus">-</button><span class="qty-val">0</span><button class="btn-qty plus">+</button></div>
        </div>

        <div class="menu-item" data-id="poori" data-name="Poori" data-price="40">
            <div class="item-details"><span class="item-name">Poori</span><span class="item-price">₹40</span></div>
            <div class="quantity-controls"><button class="btn-qty minus">-</button><span class="qty-val">0</span><button class="btn-qty plus">+</button></div>
        </div>

        <div class="menu-item" data-id="idli" data-name="Idli" data-price="25">
            <div class="item-details"><span class="item-name">Idli</span><span class="item-price">₹25</span></div>
            <div class="quantity-controls"><button class="btn-qty minus">-</button><span class="qty-val">0</span><button class="btn-qty plus">+</button></div>
        </div>

        <div class="menu-item" data-id="idli-vada" data-name="Idli Vada" data-price="40">
            <div class="item-details"><span class="item-name">Idli Vada</span><span class="item-price">₹40</span></div>
            <div class="quantity-controls"><button class="btn-qty minus">-</button><span class="qty-val">0</span><button class="btn-qty plus">+</button></div>
        </div>

        <div class="menu-item" data-id="vada" data-name="Vada" data-price="15">
            <div class="item-details"><span class="item-name">Vada</span><span class="item-price">₹15</span></div>
            <div class="quantity-controls"><button class="btn-qty minus">-</button><span class="qty-val">0</span><button class="btn-qty plus">+</button></div>
        </div>

        <div class="menu-item" data-id="curd-vada" data-name="Curd Vada" data-price="35">
            <div class="item-details"><span class="item-name">Curd Vada</span><span class="item-price">₹35</span></div>
            <div class="quantity-controls"><button class="btn-qty minus">-</button><span class="qty-val">0</span><button class="btn-qty plus">+</button></div>
        </div>
    </div>

    <!-- 2. MAIN MEALS & BREADS -->
    <div class="category-section">
        <h2>Meals & Breads</h2>
        
        <div class="menu-item" data-id="chapati" data-name="Chapati" data-price="50">
            <div class="item-details"><span class="item-name">Chapati</span><span class="item-price">₹50</span></div>
            <div class="quantity-controls"><button class="btn-qty minus">-</button><span class="qty-val">0</span><button class="btn-qty plus">+</button></div>
        </div>

        <div class="menu-item" data-id="meals" data-name="Meals" data-price="80">
            <div class="item-details"><span class="item-name">Meals</span><span class="item-price">₹80</span></div>
            <div class="quantity-controls"><button class="btn-qty minus">-</button><span class="qty-val">0</span><button class="btn-qty plus">+</button></div>
        </div>

        <div class="menu-item" data-id="rice" data-name="Rice" data-price="50">
            <div class="item-details"><span class="item-name">Rice</span><span class="item-price">₹50</span></div>
            <div class="quantity-controls"><button class="btn-qty minus">-</button><span class="qty-val">0</span><button class="btn-qty plus">+</button></div>
        </div>
    </div>

    <!-- 3. BATHS & RICE VARIETIES -->
    <div class="category-section">
        <h2>Rice & Bath Varieties</h2>

        <div class="menu-item" data-id="upma" data-name="Upma" data-price="25">
            <div class="item-details"><span class="item-name">Upma</span><span class="item-price">₹25</span></div>
            <div class="quantity-controls"><button class="btn-qty minus">-</button><span class="qty-val">0</span><button class="btn-qty plus">+</button></div>
        </div>

        <div class="menu-item" data-id="kesari-bath" data-name="Kesari Bath" data-price="25">
            <div class="item-details"><span class="item-name">Kesari Bath</span><span class="item-price">₹25</span></div>
            <div class="quantity-controls"><button class="btn-qty minus">-</button><span class="qty-val">0</span><button class="btn-qty plus">+</button></div>
        </div>

        <div class="menu-item" data-id="upma-kesari-bath" data-name="Upma Kesari Bath" data-price="40">
            <div class="item-details"><span class="item-name">Upma Kesari Bath</span><span class="item-price">₹40</span></div>
            <div class="quantity-controls"><button class="btn-qty minus">-</button><span class="qty-val">0</span><button class="btn-qty plus">+</button></div>
        </div>

        <div class="menu-item" data-id="chitranna" data-name="Chitranna" data-price="40">
            <div class="item-details"><span class="item-name">Chitranna</span><span class="item-price">₹40</span></div>
            <div class="quantity-controls"><button class="btn-qty minus">-</button><span class="qty-val">0</span><button class="btn-qty plus">+</button></div>
        </div>

        <div class="menu-item" data-id="curd-rice" data-name="Curd Rice" data-price="40">
            <div class="item-details"><span class="item-name">Curd Rice</span><span class="item-price">₹40</span></div>
            <div class="quantity-controls"><button class="btn-qty minus">-</button><span class="qty-val">0</span><button class="btn-qty plus">+</button></div>
        </div>

        <div class="menu-item" data-id="puliyogare" data-name="Puliyogare" data-price="40">
            <div class="item-details"><span class="item-name">Puliyogare</span><span class="item-price">₹40</span></div>
            <div class="quantity-controls"><button class="btn-qty minus">-</button><span class="qty-val">0</span><button class="btn-qty plus">+</button></div>
        </div>

        <div class="menu-item" data-id="palav" data-name="Palav" data-price="40">
            <div class="item-details"><span class="item-name">Palav</span><span class="item-price">₹40</span></div>
            <div class="quantity-controls"><button class="btn-qty minus">-</button><span class="qty-val">0</span><button class="btn-qty plus">+</button></div>
        </div>
    </div>

    <!-- 4. SNACKS & SWEETS -->
    <div class="category-section">
        <h2>Snacks & Sweets</h2>

        <div class="menu-item" data-id="mixture" data-name="Mixture" data-price="40">
            <div class="item-details"><span class="item-name">Mixture</span><span class="item-price">₹40</span></div>
            <div class="quantity-controls"><button class="btn-qty minus">-</button><span class="qty-val">0</span><button class="btn-qty plus">+</button></div>
        </div>

        <div class="menu-item" data-id="pakoda" data-name="Pakoda" data-price="40">
            <div class="item-details"><span class="item-name">Pakoda</span><span class="item-price">₹40</span></div>
            <div class="quantity-controls"><button class="btn-qty minus">-</button><span class="qty-val">0</span><button class="btn-qty plus">+</button></div>
        </div>

        <div class="menu-item" data-id="plate-jilebi" data-name="Plate Jilebi" data-price="20">
            <div class="item-details"><span class="item-name">Plate Jilebi</span><span class="item-price">₹20</span></div>
            <div class="quantity-controls"><button class="btn-qty minus">-</button><span class="qty-val">0</span><button class="btn-qty plus">+</button></div>
        </div>

        <div class="menu-item" data-id="jilebi" data-name="Jilebi" data-price="10">
            <div class="item-details"><span class="item-name">Jilebi (Single)</span><span class="item-price">₹10</span></div>
            <div class="quantity-controls"><button class="btn-qty minus">-</button><span class="qty-val">0</span><button class="btn-qty plus">+</button></div>
        </div>

        <div class="menu-item" data-id="gulab-jamun" data-name="Gulab Jamun" data-price="15">
            <div class="item-details"><span class="item-name">Gulab Jamun</span><span class="item-price">₹15</span></div>
            <div class="quantity-controls"><button class="btn-qty minus">-</button><span class="qty-val">0</span><button class="btn-qty plus">+</button></div>
        </div>

        <div class="menu-item" data-id="avalakki-sev" data-name="Avalakki Sev" data-price="40">
            <div class="item-details"><span class="item-name">Avalakki Sev</span><span class="item-price">₹40</span></div>
            <div class="quantity-controls"><button class="btn-qty minus">-</button><span class="qty-val">0</span><button class="btn-qty plus">+</button></div>
        </div>

        <div class="menu-item" data-id="mirchi" data-name="Mirchi" data-price="5">
            <div class="item-details"><span class="item-name">Mirchi</span><span class="item-price">₹5</span></div>
            <div class="quantity-controls"><button class="btn-qty minus">-</button><span class="qty-val">0</span><button class="btn-qty plus">+</button></div>
        </div>
    </div>

    <!-- 5. SINGLE & HALF PORTIONS -->
    <div class="category-section">
        <h2>Single & Half Portions</h2>

        <div class="menu-item" data-id="single-chapati" data-name="Single Chapati" data-price="25">
            <div class="item-details"><span class="item-name">Single Chapati</span><span class="item-price">₹25</span></div>
            <div class="quantity-controls"><button class="btn-qty minus">-</button><span class="qty-val">0</span><button class="btn-qty plus">+</button></div>
        </div>

        <div class="menu-item" data-id="single-khali-dosa" data-name="Single Khali Dosa" data-price="25">
            <div class="item-details"><span class="item-name">Single Khali Dosa</span><span class="item-price">₹25</span></div>
            <div class="quantity-controls"><button class="btn-qty minus">-</button><span class="qty-val">0</span><button class="btn-qty plus">+</button></div>
        </div>

        <div class="menu-item" data-id="single-poori" data-name="Single Poori" data-price="20">
            <div class="item-details"><span class="item-name">Single Poori</span><span class="item-price">₹20</span></div>
            <div class="quantity-controls"><button class="btn-qty minus">-</button><span class="qty-val">0</sp

