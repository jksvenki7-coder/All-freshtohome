groceries and foo<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Order Food & Groceries via WhatsApp</title>
    <meta name="viewport" content="width=device-width,initial-scale=1.0">
    <style>
        body { font-family: Arial, sans-serif; background: #f9fafb; margin: 0; }
        header { background: #2383c5; color: #fff; padding: 28px 10px; text-align: center; }
        h1 { margin: 0; font-size: 2em; }
        .section-title { font-size: 1.3em; color: #125784; margin-top: 32px; margin-bottom:14px; }
        .container { max-width: 1000px; margin:20px auto; padding: 0 12px; }
        .shop-list, .hotel-list, .product-list { display: flex; flex-wrap: wrap; gap: 26px; }
        .shop, .hotel, .product { background: #fff; border-radius: 8px; box-shadow: 0 2px 12px #e4eaf3; width: 240px; padding: 18px; text-align: center; }
        .shop img, .hotel img, .product img { width: 100px; height: 75px; object-fit: cover; border-radius:6px; margin-bottom:8px; }
        .item-title { font-weight:bold; margin:5px 0 9px 0; font-size:1em;}
        .item-price { color: #168850; margin-bottom:10px;}
        .order-btn { background: #25d366; color: #fff; border: none; border-radius: 5px; padding: 10px 18px; font-size: 1em; cursor: pointer; }
        .order-btn:hover { background: #128c7e; }
        footer { background: #2383c5; color: #fff; text-align: center; padding: 14px; margin-top: 35px; }
    </style>
    <script>
        function orderOnWhatsApp(item, vendorType, vendorName, price) {
            const phone = "919999999999"; // Replace with actual WhatsApp contact number (country code)
            let message = "";
            if (vendorType === "hotel") {
                message = encodeURIComponent(`Order request from website:\nFood Item: ${item}\nHotel: ${vendorName}\nPrice: ${price}\nPlease share delivery details.`);
            } else if (vendorType === "shop") {
                message = encodeURIComponent(`Order request from website:\nGrocery: ${item}\nShop: ${vendorName}\nPrice: ${price}\nPlease share delivery details.`);
            }
            window.open(`https://wa.me/${phone}?text=${message}`, '_blank');
        }
    </script>
</head>
<body>
    <header>
        <h1>Order Food & Groceries Online</h1>
        <p>Quick orders from top hotels and shops. Delivered fast. Order now via WhatsApp!</p>
    </header>
    <div class="container">

        <div class="section-title">Hotels - Popular Food Items</div>
        <div class="hotel-list">
            <div class="hotel">
                <img src="https://images.unsplash.com/photo-1504674900247-0877df9cc836" alt="Hotel A">
                <div class="item-title">Hotel GreenPark</div>
                <div class="item-title">Chicken Biryani</div>
                <div class="item-price">₹199</div>
                <button class="order-btn" onclick="orderOnWhatsApp('Chicken Biryani','hotel','Hotel GreenPark','₹199')">Order via WhatsApp</button>
            </div>
            <div class="hotel">
                <img src="https://images.unsplash.com/photo-1519864600265-abb23847ef2c" alt="Hotel B">
                <div class="item-title">Hotel Sai Foods</div>
                <div class="item-title">Paneer Butter Masala</div>
                <div class="item-price">₹179</div>
                <button class="order-btn" onclick="orderOnWhatsApp('Paneer Butter Masala','hotel','Hotel Sai Foods','₹179')">Order via WhatsApp</button>
            </div>
            <div class="hotel">
                <img src="https://images.unsplash.com/photo-1470337458703-46ad1756a187" alt="Hotel C">
                <div class="item-title">Hotel Classic</div>
                <div class="item-title">Veg Fried Rice</div>
                <div class="item-price">₹129</div>
                <button class="order-btn" onclick="orderOnWhatsApp('Veg Fried Rice','hotel','Hotel Classic','₹129')">Order via WhatsApp</button>
            </div>
        </div>

        <div class="section-title">Shops - Groceries & Essentials</div>
        <div class="shop-list">
            <div class="shop">
                <img src="https://images.unsplash.com/photo-1464306076886-debca5e8a6b0" alt="Shop A">
                <div class="item-title">FreshMart</div>
                <div class="item-title">Tomato (1kg)</div>
                <div class="item-price">₹32</div>
                <button class="order-btn" onclick="orderOnWhatsApp('Tomato 1kg','shop','FreshMart','₹32')">Order via WhatsApp</button>
            </div>
            <div class="shop">
                <img src="https://images.unsplash.com/photo-1502741338009-cac2772e18bc" alt="Shop B">
                <div class="item-title">GreenLeaf</div>
                <div class="item-title">Sona Masoori Rice (5kg)</div>
                <div class="item-price">₹315</div>
                <button class="order-btn" onclick="orderOnWhatsApp('Sona Masoori Rice 5kg','shop','GreenLeaf','₹315')">Order via WhatsApp</button>
            </div>
            <div class="shop">
                <img src="https://images.unsplash.com/photo-1519864600265-abb23847ef2c" alt="Shop C">
                <div class="item-title">Daily Dairy</div>
                <div class="item-title">Milk (1ltr)</div>
                <div class="item-price">₹55</div>
                <button class="order-btn" onclick="orderOnWhatsApp('Milk 1ltr','shop','Daily Dairy','₹55')">Order via WhatsApp</button>
            </div>
        </div>
    </div>
    <footer>
        &copy; 2025 OrderFoodGroceries.com | All rights reserved.
    </footer>
</body>
</html>d delivery through whatsapp
