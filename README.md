<!DOCTYPE html>
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
        .shop-list, .hotel-list { display: flex; flex-wrap: wrap; gap: 26px; }
        .shop, .hotel { background: #fff; border-radius: 8px; box-shadow: 0 2px 12px #e4eaf3; width: 240px; padding: 18px; text-align: center; }
        .shop img, .hotel img { width: 100px; height: 75px; object-fit: cover; border-radius:6px; margin-bottom:8px; }
        .item-title { font-weight:bold; margin:5px 0 9px 0; font-size:1em;}
        .item-price { color: #168850; margin-bottom:10px;}
        .order-btn { background: #25d366; color: #fff; border: none; border-radius: 5px; padding: 10px 18px; font-size: 1em; cursor: pointer; }
        .order-btn:hover { background: #128c7e; }
        .image-upload-section { background: #fff; border-radius: 9px; box-shadow: 0 2px 12px #c7eaf4; padding:18px; margin: 25px 0 30px 0; text-align: center;}
        .upload-preview { margin:12px 0; }
        .upload-preview img{ max-width:180px; border:2px solid #89d6d3; border-radius:8px; }
        footer { background: #2383c5; color: #fff; text-align: center; padding: 14px; margin-top: 35px; }
        label { font-size:1.04em }
    </style>
    <script>
        // WhatsApp order with item details
        function orderOnWhatsApp(item, vendorType, vendorName, price) {
            const phone = "918977143043";
            let message = "";
            if (vendorType === "hotel") {
                message = encodeURIComponent(`Order request from website:\nFood Item: ${item}\nHotel: ${vendorName}\nPrice: ${price}\nImage (if attached): See below.\nPlease share delivery details.`);
            } else if (vendorType === "shop") {
                message = encodeURIComponent(`Order request from website:\nGrocery: ${item}\nShop: ${vendorName}\nPrice: ${price}\nImage (if attached): See below.\nPlease share delivery details.`);
            }
            alert('If you have uploaded an image, please manually attach the downloaded image in your WhatsApp chat after clicking OK.');
            window.open(`https://wa.me/${phone}?text=${message}`, '_blank');
        }

        // Image upload and download preview
        function handleImageUpload(input) {
            const preview = document.getElementById('imagePreview');
            const downloadBtn = document.getElementById('downloadImage');
            if (input.files && input.files[0]) {
                const reader = new FileReader();
                reader.onload = function(e) {
                    preview.innerHTML = `<img src="${e.target.result}" id="uploadedImg"><br><button id="downloadImage" class="order-btn" onclick="downloadImage()">Download Image for WhatsApp</button>`;
                }
                reader.readAsDataURL(input.files[0]);
            } else {
                preview.innerHTML = '';
            }
        }
        function downloadImage() {
            const img = document.getElementById('uploadedImg');
            if(img){
                const link = document.createElement('a');
                link.href = img.src;
                link.download = 'order-image.jpg';
                link.click();
            }
        }
    </script>
</head>
<body>
    <header>
        <h1>Order Food & Groceries Online</h1>
        <p>Order from hotels and shops. Upload an image (e.g. prescription) if needed, then order via WhatsApp!</p>
    </header>
    <div class="container">

        <div class="image-upload-section">
            <label for="imageInput">Upload Image (to send with WhatsApp order):</label><br>
            <input type="file" id="imageInput" accept="image/*" onchange="handleImageUpload(this)">
            <div id="imagePreview" class="upload-preview"></div>
            <small>After uploading, click 'Download Image for WhatsApp', then attach it manually in your WhatsApp chat.</small>
        </div>

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
                <div class="item-price">₹315</div><!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>FreshEats - Online Order</title>
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        body { font-family: Arial, sans-serif; margin: 0; background: #fff7e6; color: #222; }
        header { background: linear-gradient(90deg, #fd8904 0%, #fd574a 100%); color: #fff; padding: 30px 18px; text-align: center; }
        h1 { margin: 0; font-size: 2.3em; }
        nav { margin-top: 20px; }
        nav a { color: #fff; text-decoration: none; font-size: 1.1em; margin: 0 15px; }
        .container { max-width: 450px; margin: 30px auto; background: #fff; border-radius: 17px; box-shadow: 0 2px 12px #fcdda6; padding: 32px 18px; }
        .form-group { margin-bottom: 20px; }
        input, select { width: 100%; padding: 12px; font-size: 1.05em; margin-top: 5px; box-sizing: border-box; border-radius: 7px; border: 1.2px solid #fdc680; }
        label { font-weight: bold; margin-bottom: 8px; display: block; }
        table { width: 100%; margin: 25px 0; border-collapse: collapse; }
        th, td { padding: 12px 8px; text-align: left; border-bottom: 1px solid #fae3c7; }
        th { background-color: #fde1b4; font-size: 1.1em; }
        .order-btn { background: linear-gradient(90deg, #fd8904 0%, #fd574a 100%); color: #fff; border: none; border-radius: 7px; font-size: 1.1em; padding: 13px 0; width: 100%; cursor: pointer; margin-top: 26px;}
        .order-btn:hover { opacity: 0.9;}
        footer { background: #fd8904; color: #fff; text-align: center; padding: 15px; margin-top: 30px; border-radius:0 0 12px 12px;}
    </style>
    <script>
        function sendOrder(event) {
            event.preventDefault();
            const name = document.getElementById('name').value;
            const phone = document.getElementById('phone').value;
            const cheeseBurger = document.getElementById('cheeseBurger').value;
            const vegPizza = document.getElementById('vegPizza').value;
            const biryani = document.getElementById('biryani').value;
            const otherItems = document.getElementById('otherItems').value;
            const address = document.getElementById('address').value;

            let orderSummary = `Order Details:\n`;
            orderSummary += `Name: ${name}\nPhone: ${phone}\n`;
            orderSummary += `Cheese Burger: ${cheeseBurger}\n`;
            orderSummary += `Veg Pizza: ${vegPizza}\n`;
            orderSummary += `Hyderabadi Biryani: ${biryani}\n`;
            orderSummary += `Other Items: ${otherItems}\n`;
            orderSummary += `Delivery Address: ${address}`;

            // WhatsApp number (with country code)
            const phoneNumber = "918977143043";
            window.open(`https://wa.me/${phoneNumber}?text=${encodeURIComponent(orderSummary)}`, "_blank");
        }
    </script>
</head>
<body>
    <header>
        <h1>FreshEats</h1>
        <nav>
            <a href="#">Home</a>
            <a href="#">Menu</a>
            <a href="#">Order</a>
            <a href="#">Contact</a>
        </nav>
    </header>
    <div class="container">
        <form onsubmit="sendOrder(event)">
            <div class="form-group">
                <label for="name">Your Name</label>
                <input type="text" id="name" required>
            </div>
            <div class="form-group">
                <label for="phone">Phone Number</label>
                <input type="tel" id="phone" required>
            </div>
            <h2 style="text-align:center;">Select Items</h2>
            <table>
                <tr>
                    <th>Food Item</th>
                    <th>Quantity</th>
                </tr>
                <tr>
                    <td>Cheese Burger</td>
                    <td><input type="number" id="cheeseBurger" min="0" value="0"></td>
                </tr>
                <tr>
                    <td>Veg Pizza</td>
                    <td><input type="number" id="vegPizza" min="0" value="0"></td>
                </tr>
                <tr>
                    <td>Hyderabadi Biryani</td>
                    <td><input type="number" id="biryani" min="0" value="0"></td>
                </tr>
            </table>
            <div class="form-group">
                <label for="otherItems">Other Items (Coke, Fries, etc.)</label>
                <input type="text" id="otherItems">
            </div>
            <div class="form-group">
                <label for="address">Delivery Address</label>
                <input type="text" id="address" required>
            </div>
            <button class="order-btn" type="submit">Order Now via WhatsApp</button>
        </form>
    </div>
    <footer>
        &copy; 2025 FreshEats. All rights reserved.
    </footer>
</body>
</html>
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
</html>
