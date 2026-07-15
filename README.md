# Sri-Raghavendra-bhavana- /  [ index.html        ]
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sri Raghavendra Bhavan - Digital Menu</title>
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
            padding: 20px 15px 80px 15px;
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
            display: flex;
            align-items: center;
            justify-content: space-between;
        }

        /* Menu Item Styles */
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
        }

        .item-price {
            font-weight: 700;
            font-size: 1.1rem;
            color: var(--secondary-color);
            white-space: nowrap;
        }

        /* Footer */
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

    <!-- 1. Breakfast & Main Dishes -->
    <div class="category-section">
        <h2>Breakfast & Main Dishes</h2>
        
        <div class="menu-item">
            <div class="item-details"><span class="item-name">Masala Dosa</span></div>
            <span class="item-price">₹50</span>
        </div>
        
        <div class="menu-item">
            <div class="item-details"><span class="item-name">Open Dosa (Butter Masala)</span></div>
            <span class="item-price">₹60</span>
        </div>
        
        <div class="menu-item">
            <div class="item-details"><span class="item-name">Khali Dosa</span></div>
            <span class="item-price">₹45</span>
        </div>
        
        <div class="menu-item">
            <div class="item-details"><span class="item-name">Onion Dosa</span></div>
            <span class="item-price">₹70</span>
        </div>
        
        <div class="menu-item">
            <div class="item-details"><span class="item-name">Set Dosa</span></div>
            <span class="item-price">₹50</span>
        </div>
        
        <div class="menu-item">
            <div class="item-details"><span class="item-name">Poori</span></div>
            <span class="item-price">₹40</span>
        </div>
        
        <div class="menu-item">
            <div class="item-details"><span class="item-name">Idli</span></div>
            <span class="item-price">₹25</span>
        </div>
        
        <div class="menu-item">
            <div class="item-details"><span class="item-name">Idli Vada</span></div>
            <span class="item-price">₹40</span>
        </div>
        
        <div class="menu-item">
            <div class="item-details"><span class="item-name">Vada</span></div>
            <span class="item-price">₹15</span>
        </div>
        
        <div class="menu-item">
            <div class="item-details"><span class="item-name">Curd Vada</span></div>
            <span class="item-price">₹35</span>
        </div>
        
        <div class="menu-item">
            <div class="item-details"><span class="item-name">Chapati</span></div>
            <span class="item-price">₹50</span>
        </div>
        
        <div class="menu-item">
            <div class="item-details"><span class="item-name">Meals</span></div>
            <span class="item-price">₹80</span>
        </div>
        
        <div class="menu-item">
            <div class="item-details"><span class="item-name">Rice</span></div>
            <span class="item-price">₹50</span>
        </div>
    </div>

    <!-- 2. Bath & Rice Varieties -->
    <div class="category-section">
        <h2>Bath & Rice Varieties</h2>
        
        <div class="menu-item">
            <div class="item-details"><span class="item-name">Upma</span></div>
            <span class="item-price">₹25</span>
        </div>
        
        <div class="menu-item">
            <div class="item-details"><span class="item-name">Kesari Bath</span></div>
            <span class="item-price">₹25</span>
        </div>
        
        <div class="menu-item">
            <div class="item-details"><span class="item-name">Upma Kesari Bath</span></div>
            <span class="item-price">₹40</span>
        </div>
        
        <div class="menu-item">
            <div class="item-details"><span class="item-name">Chitranna</span></div>
            <span class="item-price">₹40</span>
        </div>
        
        <div class="menu-item">
            <div class="item-details"><span class="item-name">Curd Rice</span></div>
            <span class="item-price">₹40</span>
        </div>
        
        <div class="menu-item">
            <div class="item-details"><span class="item-name">Puliyogare</span></div>
            <span class="item-price">₹40</span>
        </div>
        
        <div class="menu-item">
            <div class="item-details"><span class="item-name">Palav</span></div>
            <span class="item-price">₹40</span>
        </div>
    </div>

    <!-- 3. Snacks & Sweets -->
    <div class="category-section">
        <h2>Snacks & Sweets</h2>
        
        <div class="menu-item">
            <div class="item-details"><span class="item-name">Pakoda</span></div>
            <span class="item-price">₹40</span>
        </div>
        
        <div class="menu-item">
            <div class="item-details"><span class="item-name">Mixture</span></div>
            <span class="item-price">₹40</span>
        </div>
        
        <div class="menu-item">
            <div class="item-details"><span class="item-name">Plate Jilebi</span></div>
            <span class="item-price">₹20</span>
        </div>
        
        <div class="menu-item">
            <div class="item-details"><span class="item-name">Jilebi (Single)</span></div>
            <span class="item-price">₹10</span>
        </div>
        
        <div class="menu-item">
            <div class="item-details"><span class="item-name">Gulab Jamun</span></div>
            <span class="item-price">₹15</span>
        </div>
        
        <div class="menu-item">
            <div class="item-details"><span class="item-name">Avalakki Sev</span></div>
            <span class="item-price">₹40</span>
        </div>
        
        <div class="menu-item">
            <div class="item-details"><span class="item-name">Mirchi</span></div>
            <span class="item-price">₹5</span>
        </div>
    </div>

    <!-- 4. Single & Half Portions -->
    <div class="category-section">
        <h2>Single & Half Portions</h2>
        
        <div class="menu-item">
            <div class="item-details"><span class="item-name">Single Chapati</span></div>
            <span class="item-price">₹25</span>
        </div>
        
        <div class="menu-item">
            <div class="item-details"><span class="item-name">Single Khali Dosa</span></div>
            <span class="item-price">₹25</span>
        </div>
        
        <div class="menu-item">
            <div class="item-details"><span class="item-name">Single Poori</span></div>
            <span class="item-price">₹20</span>
        </div>
        
        <div class="menu-item">
            <div class="item-details"><span class="item-name">Single Idli</span></div>
            <span class="item-price">₹15</span>
        </div>
        
        <div class="menu-item">
            <div class="item-details"><span class="item-name">Single Idli Vada</span></div>
            <span class="item-price">₹30</span>
        </div>
        
        <div class="menu-item">
            <div class="item-details"><span class="item-name">Half Pakoda</span></div>
            <span class="item-price">₹20</span>
        </div>
        
        <div class="menu-item">
            <div class="item-details"><span class="item-name">Half Curd Rice</span></div>
            <span class="item-price">₹25</span>
        </div>
        
        <div class="menu-item">
            <div class="item-details"><span class="item-name">Half Chitranna</span></div>
            <span class="item-price">₹25</span>
        </div>
        
        <div class="menu-item">
            <div class="item-details"><span class="item-name">Half Palav</span></div>
            <span class="item-price">₹25</span>
        </div>
        
        <div class="menu-item">
            <div class="item-details"><span class="item-name">Half Puliyogare</span></div>
            <span class="item-price">₹25</span>
        </div>
    </div>

    <!-- 5. Beverages & Cold Drinks -->
    <div class="category-section">
        <h2>Beverages & Cold Drinks</h2>
        
        <div class="menu-item">
            <div class="item-details"><span class="item-name">Tea / Coffee</span></div>
            <span class="item-price">₹5</span>
        </div>
        
        <div class="menu-item">
            <div class="item-details"><span class="item-name">Buttermilk</span></div>
            <span class="item-price">₹15</span>
        </div>
        
        <div class="menu-item">
            <div class="item-details"><span class="item-name">Nandini Badam Milk</span></div>
            <span class="item-price">₹25</span>
        </div>
        
        <div class="menu-item">
            <div class="item-details"><span class="item-name">Soft Drink Bottles (Sting / Mazaa / Sprite / Fanta / Mirinda)</span></div>
            <span class="item-price">₹20</span>
        </div>
        
        <div class="menu-item">
            <div class="item-details"><span class="item-name">Soft Drink Glasses (Sprite / Fanta / Limca / Thums Up)</span></div>
            <span class="item-price">₹15</span>
        </div>
        
        <div class="menu-item">
            <div class="item-details"><span class="item-name">Bindu Jeera</span></div>
            <span class="item-price">₹15</span>
        </div>
        
        <div class="menu-item">
            <div class="item-details"><span class="item-name">Water Bottle (500ml)</span></div>
            <span class="item-price">₹10</span>
        </div>
        
        <div class="menu-item">
            <div class="item-details"><span class="item-name">Water Bottle (1L)</span></div>
            <span class="item-price">₹20</span>
        </div>
        
        <div class="menu-item">
            <div class="item-details"><span class="item-name">Water Bottle (2L)</span></div>
            <span class="item-price">₹30</span>
        </div>
        
        <div class="menu-item">
            <div class="item-details"><span class="item-name">Sprite (400ml)</span></div>
            <span class="item-price">₹40</span>
        </div>
    </div>

    <!-- 6. Sweets by Weight & Ice Cream -->
    <div class="category-section">
        <h2>Sweets by Weight & Ice Cream</h2>
        
        <div class="menu-item">
            <div class="item-details"><span class="item-name">Jilebi (250g)</span></div>
            <span class="item-price">₹70</span>
        </div>
        
        <div class="menu-item">
            <div class="item-details"><span class="item-name">Mixture (250g)</span></div>
            <span class="item-price">₹70</span>
        </div>
        
        <div class="menu-item">
            <div class="item-details"><span class="item-name">Ice Creams</span></div>
            <span class="item-price">₹10 - ₹40</span>
        </div>
    </div>

    <footer>
        <p>© 2026 Sri Raghavendra Bhavan. All Rights Reserved.</p>
    </footer>
</div>

</body>
</html>
