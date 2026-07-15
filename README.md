# Sri-Raghavendra-bhavana- /  [ index.html        ]
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sri Raghavendra Bhavan</title>
    <style>
        :root {
            --primary: #e65100;
            --secondary: #2e7d32;
            --background: #f7f9fc;
            --surface: #ffffff;
            --text: #333333;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: var(--background);
            color: var(--text);
            margin: 0;
            padding: 0;
            padding-bottom: 100px; /* Space for sticky cart */
        }

        header {
            background: var(--surface);
            text-align: center;
            padding: 20px 10px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.05);
            border-bottom: 3px solid var(--primary);
        }

        header h1 {
            color: var(--primary);
            margin: 0 0 5px 0;
            font-size: 24px;
        }

        header p {
            margin: 5px 0;
            color: #666;
            font-size: 14px;
        }

        /* 🎯 Table Selection Styling */
        .table-selector-box {
            background: #fffde7;
            border: 2px dashed #ffe082;
            border-radius: 12px;
            margin: 15px;
            padding: 15px;
            text-align: center;
        }

        .table-selector-box h3 {
            margin: 0 0 10px 0;
            color: #b26a00;
            font-size: 16px;
        }

        .table-buttons {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 8px;
            max-width: 320px;
            margin: 0 auto;
        }

        .table-btn {
            background: white;
            border: 1.5px solid #ffe082;
            padding: 10px;
            font-size: 14px;
            font-weight: bold;
            border-radius: 8px;
            cursor: pointer;
            transition: 0.2s ease;
        }

        .table-btn.selected {
            background: var(--secondary);
            color: white;
            border-color: var(--secondary);
            box-shadow: 0 3px 8px rgba(46, 125, 50, 0.3);
        }

        /* 📋 Menu Grid styling */
        .category-title {
            color: var(--primary);
            margin: 20px 15px 10px 15px;
            font-size: 18px;
            border-left: 4px solid var(--primary);
            padding-left: 8px;
        }

        .menu-grid {
            display: grid;
            grid-template-columns: 1fr;
            gap: 12px;
            padding: 0 15px;
        }

        @media (min-width: 600px) {
            .menu-grid {
                grid-template-columns: 1fr 1fr;
            }
        }

        .menu-card {
            background: var(--surface);
            border-radius: 12px;
            padding: 12px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            box-shadow: 0 2px 8px rgba(0,0,0,0.04);
        }

        .item-info h4 {
            margin: 0 0 4px 0;
            font-size: 16px;
        }

        .item-price {
            color: var(--secondary);
            font-weight: bold;
            font-size: 15px;
        }

        /* ➕ Add / Quantity Buttons */
        .qty-controls {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .add-btn {
            background: var(--primary);
            color: white;
            border: none;
            padding: 8px 16px;
            border-radius: 20px;
            font-weight: bold;
            cursor: pointer;
        }

        .adjust-btn {
            background: #f0f0f0;
            border: none;
            width: 28px;
            height: 28px;
            border-radius: 50%;
            font-weight: bold;
            cursor: pointer;
        }

        /* 🛒 Sticky Footer Cart styling */
        .cart-bar {
            position: fixed;
            bottom: 0;
            left: 0;
            right: 0;
            background: var(--surface);
            box-shadow: 0 -4px 15px rgba(0,0,0,0.1);
            padding: 15px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-top: 1px solid #eee;
            z-index: 1000;
        }

        .order-btn {
            background: var(--secondary);
            color: white;
            border: none;
            padding: 12px 24px;
            font-size: 16px;
            font-weight: bold;
            border-radius: 30px;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 8px;
        }
    </style>
</head>
<body>

    <header>
        <h1>Sri Raghavendra Bhavan</h1>
        <p>📍 Sh Road, Malebennur | 📞 8095004556</p>
    </header>

    <!-- 🎯 Table Selection Box (All 8 Tables) -->
    <div class="table-selector-box">
        <h3 id="tableStatus">👉 Please Select Your Table Number:</h3>
        <div class="table-buttons">
            <button class="table-btn" onclick="selectTable(1)">Tab 1</button>
            <button class="table-btn" onclick="selectTable(2)">Tab 2</button>
            <button class="table-btn" onclick="selectTable(3)">Tab 3</button>
            <button class="table-btn" onclick="selectTable(4)">Tab 4</button>
            <button class="table-btn" onclick="selectTable(5)">Tab 5</button>
            <button class="table-btn" onclick="selectTable(6)">Tab 6</button>
            <button class="table-btn" onclick="selectTable(7)">Tab 7</button>
            <button class="table-btn" onclick="selectTable(8)">Tab 8</button>
        </div>
    </div>

    <!-- 📋 Menu Sections -->
    <div id="menu-container"></div>

    <!-- 🛒 Sticky Cart Bar -->
    <div class="cart-bar">
        <div>
            <div style="font-size: 12px; color: #666;">Total Items</div>
            <div id="cartTotal" style="font-size: 18px; font-weight: bold; color: var(--primary);">₹0</div>
        </div>
        <button class="order-btn" onclick="sendWhatsAppOrder()">
            💬 Send Order on WhatsApp
        </button>
    </div>

<script>
    // 🍔 Complete menu database formatted directly from your images
    const menuData = {
        "Main Dishes": [
            { id: "masala_dosa", name: "Masala Dosa", price: 50 },
            { id: "open_dosa", name: "Open Dosa", price: 60 },
            { id: "khali_dosa", name: "Khali Dosa", price: 45 },
            { id: "onion_dosa", name: "Onion Dosa", price: 70 },
            { id: "set_dosa", name: "Set Dosa", price: 50 },
            { id: "poori", name: "Poori", price: 40 },
            { id: "idli", name: "Idli", price: 25 },
            { id: "idli_vada", name: "Idli Vada", price: 40 },
            { id: "chapati", name: "Chapati", price: 50 },
            { id: "meals", name: "Meals", price: 80 },
            { id: "rice", name: "Rice", price: 50 },
            { id: "upma", name: "Upma", price: 25 },
            { id: "kesari_bath", name: "Kesari Bath", price: 25 },
            { id: "upma_kesari_bath", name: "Upma Kesari Bath", price: 40 },
            { id: "chitranna", name: "Chitranna", price: 40 },
            { id: "curd_rice", name: "Curd Rice", price: 40 },
            { id: "puliyogare", name: "Puliyogare", price: 40 },
            { id: "palav", name: "Palav", price: 40 }
        ],
        "Single / Half Portions": [
            { id: "single_idli", name: "Single Idli", price: 15 },
            { id: "single_idli_vada", name: "Single Idli Vada", price: 30 },
            { id: "single_khali_dosa", name: "Single Khali Dosa", price: 25 },
            { id: "single_poori", name: "Single Poori", price: 20 },
            { id: "single_chapati", name: "Single Chapati", price: 25 },
            { id: "half_pakoda", name: "Half Pakoda", price: 20 },
            { id: "half_curd_rice", name: "Half Curd Rice", price: 25 },
            { id: "half_chitranna", name: "Half Chitranna", price: 25 },
            { id: "half_palav", name: "Half Palav", price: 25 },
            { id: "half_puliyogare", name: "Half Puliyogare", price: 25 }
        ],
        "Snacks & Sweets": [
            { id: "pakoda", name: "Pakoda", price: 40 },
            { id: "mixture", name: "Mixture", price: 40 },
            { id: "plate_jilebi", name: "Plate Jilebi", price: 20 },
            { id: "jilebi", name: "Jilebi", price: 10 },
            { id: "gulab_jamun", name: "Gulab Jamun", price: 15 },
            { id: "curd_vada", name: "Curd Vada", price: 35 },
            { id: "vada", name: "Vada", price: 15 },
            { id: "mirchi", name: "Mirchi", price: 5 },
            { id: "avalakki_sev", name: "Avalakki Sev", price: 40 },
            { id: "jilebi_250g", name: "Jilebi (250g)", price: 70 },
            { id: "mixture_250g", name: "Mixture (250g)", price: 70 }
        ],
        "Juices & Soft Drinks": [
            { id: "tea", name: "Tea", price: 5 },
            { id: "coffee", name: "Coffee", price: 5 },
            { id: "nandini_badam_milk", name: "Nandini Badam Milk", price: 25 },
            { id: "butter_milk", name: "Butter Milk", price: 15 },
            { id: "water_500ml", name: "Water (500ml)", price: 10 },
            { id: "water_1l", name: "Water (1L)", price: 20 },
            { id: "water_2l", name: "Water (2L)", price: 30 },
            { id: "maaza_glass", name: "Maaza Glass", price: 15 },
            { id: "maaza_bottle", name: "Mazaa Bottle", price: 20 },
            { id: "fanta_glass", name: "Fanta Glass", price: 15 },
            { id: "fanta_bottle", name: "Fanta Bottle", price: 20 },
            { id: "sprite_glass", name: "Sprite Glass", price: 15 },
            { id: "sprite_400ml", name: "Sprite (400ml)", price: 40 },
            { id: "sprite_bottle", name: "Sprite Bottle", price: 20 },
            { id: "limca_glass", name: "Limca Glass", price: 15 },
            { id: "mirinda", name: "Mirinda", price: 20 },
            { id: "bindu_jeera", name: "Bindu Jeera", price: 15 },
            { id: "pineapple", name: "Pineapple Juice", price: 15 },
            { id: "sipon_orange", name: "Sipon Orange", price: 15 },
            { id: "sipon_tender_water", name: "Sipon Tender Water", price: 20 },
            { id: "chill_mill", name: "Chill Mill", price: 10 },
            { id: "sting", name: "Sting", price: 20 },
            { id: "thumps_up_glass", name: "Thums Up Glass", price: 15 }
        ],
        "Ice Creams": [
            { id: "ice_10", name: "Ice Cream (₹10)", price: 10 },
            { id: "ice_20", name: "Ice Cream (₹20)", price: 20 },
            { id: "ice_25", name: "Ice Cream (₹25)", price: 25 },
            { id: "ice_30", name: "Ice Cream (₹30)", price: 30 },
            { id: "ice_40", name: "Ice Cream (₹40)", price: 40 }
        ]
    };

    let selectedTableNum = null;
    let cart = {};

    // 🚀 Select table handler
    function selectTable(num) {
        selectedTableNum = num;
        
        // Highlight active button
        document.querySelectorAll('.table-btn').forEach((btn, index) => {
            if (index + 1 === num) {
                btn.classList.add('selected');
            } else {
                btn.classList.remove('selected');
            }
        });

        document.getElementById('tableStatus').innerText = `✅ Table Selected: Table ${num}`;
        document.getElementById('tableStatus').style.color = "var(--secondary)";
    }

    // 🎨 Render Menu on page
    function renderMenu() {
        const container = document.getElementById('menu-container');
        container.innerHTML = '';

        for (const [category, items] of Object.entries(menuData)) {
            const catTitle = document.createElement('h3');
            catTitle.className = 'category-title';
            catTitle.innerText = category;
            container.appendChild(catTitle);

            const grid = document.createElement('div');
            grid.className = 'menu-grid';

            items.forEach(item => {
                const card = document.createElement('div');
                card.className = 'menu-card';
                card.innerHTML = `
                    <div class="item-info">
                        <h4>${item.name}</h4>
                        <div class="item-price">₹${item.price}</div>
                    </div>
                    <div class="qty-controls" id="controls-${item.id}">
                        <button class="add-btn" onclick="addToCart('${item.id}', '${item.name}', ${item.price})">ADD</button>
                    </div>
                `;
                grid.appendChild(card);
            });
            container.appendChild(grid);
        }
    }

    function addToCart(id, name, price) {
        cart[id] = { name, price, qty: 1 };
        updateQtyUI(id);
        calculateTotal();
    }

    // Adjust quantity
    function updateQty(id, change) {
        if (!cart[id]) return;
        cart[id].qty += change;
        if (cart[id].qty <= 0) {
            delete cart[id];
            resetAddBtn(id);
        } else {
            updateQtyUI(id);
        }
        calculateTotal();
    }

    function updateQtyUI(id) {
        const container = document.getElementById(`controls-${id}`);
        if (!container) return;
        container.innerHTML = `
            <button class="adjust-btn" onclick="updateQty('${id}', -1)">-</button>
            <span style="font-weight: bold; min-width: 15px; text-align: center;">${cart[id].qty}</span>
            <button class="adjust-btn" onclick="updateQty('${id}', 1)">+</button>
        `;
    }

    function resetAddBtn(id) {
        const container = document.getElementById(`controls-${id}`);
        if (!container) return;
        // Find item to restore standard ADD button setup
        let foundItem = null;
        for (const items of Object.values(menuData)) {
            foundItem = items.find(item => item.id === id);
            if (foundItem) break;
        }
        if (foundItem) {
            container.innerHTML = `<button class="add-btn" onclick="addToCart('${foundItem.id}', '${foundItem.name}', ${foundItem.price})">ADD</button>`;
        }
    }

    function calculateTotal() {
        let total = 0;
        for (const item of Object.values(cart)) {
            total += item.price * item.qty;
        }
        document.getElementById('cartTotal').innerText = `₹${total}`;
    }

    // 📤 Send structured order to WhatsApp
    function sendWhatsAppOrder() {
        if (!selectedTableNum) {
            alert("❌ Please select your Table Number at the top of the menu before sending your order!");
            document.querySelector('.table-selector-box').scrollIntoView({ behavior: 'smooth' });
            return;
        }

        const cartItems = Object.values(cart);
        if (cartItems.length === 0) {
            alert("❌ Your cart is empty. Please add items to order.");
            return;
        }

        let totalBill = 0;
        let message = `🍽️ *SRI RAGHAVENDRA BHAVAN*\n`;
        message += `📍 *Table Number:* Table ${selectedTableNum}\n`;
        message += `-----------------------------\n`;

        cartItems.forEach(item => {
            const cost = item.price * item.qty;
            totalBill += cost;
            message += `▪️ ${item.name} x ${item.qty} = *₹${cost}*\n`;
        });

        message += `-----------------------------\n`;
        message += `💰 *Grand Total:* *₹${totalBill}*\n\n`;
        message += `Please prepare our order! Thank you.`;

        // Restaurant Phone Number setup
        const phoneNumber = "918095004556"; 
        const whatsappUrl = `https://api.whatsapp.com/send?phone=${phoneNumber}&text=${encodeURIComponent(message)}`;
        
        window.open(whatsappUrl, '_blank');
    }

    // Run setup on page load
    window.onload = function() {
        renderMenu();
    }
</script>

</body>
</html>
