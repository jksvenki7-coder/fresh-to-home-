# fresh-to-home-<!DOCTYPE html>
<html>
<head>
    <title>App Delivery Service</title>
    <style>
        body { font-family: Arial, sans-serif; background: #f7f7f7; margin: 0; padding: 0; }
        .navbar { background: #2296f3; padding: 10px; display: flex; justify-content: space-around; }
        .navbar a { color: #fff; text-decoration: none; padding: 8px 16px; border-radius: 4px; transition: background 0.3s; }
        .navbar a:hover { background: #1565c0; }
        .container { max-width: 800px; margin: 30px auto; background: #fff; padding: 20px; border-radius: 8px; box-shadow: 0 2px 8px #ddd; }
        h2 { color: #2296f3; }
        .categories, .subcategories { display: flex; gap: 15px; margin-bottom: 20px; }
        .category-btn, .subcategory-btn { padding: 10px 20px; background: #2296f3; color: #fff; border: none; border-radius: 4px; cursor: pointer; }
        .category-btn:hover, .subcategory-btn:hover { background: #1565c0; }
        .hidden { display: none; }
        form input, form textarea { width: 100%; padding: 8px; margin: 10px 0; border-radius: 4px; border: 1px solid #ccc; }
        form button { background: #2296f3; color: #fff; border: none; padding: 10px 20px; border-radius: 4px; cursor: pointer; }
        form button:hover { background: #1565c0; }
    </style>
</head>
<body>
    <div class="navbar">
        <a href="#" onclick="showSection('home')">Home</a>
        <a href="#" onclick="showSection('contact')">Contact</a>
        <a href="#" onclick="showSection('camera')">Camera</a>
        <a href="#" onclick="showSection('maps')">Maps</a>
        <a href="#" onclick="showSection('profile')">Profile</a>
    </div>
    <div class="container">
        <!-- Home Section -->
        <div id="home">
            <h2>Select Category</h2>
            <div class="categories">
                <button class="category-btn" onclick="showCategories('groceries')">Groceries</button>
                <button class="category-btn" onclick="showCategories('food')">Food</button>
                <button class="category-btn" onclick="showCategories('pharmacy')">Pharmacy</button>
            </div>
            <div id="groceries" class="subcategories hidden">
                <h3>Groceries Subcategories</h3>
                <button class="subcategory-btn" onclick="showOrderForm('Groceries')">Groceries</button>
                <button class="subcategory-btn" onclick="showOrderForm('Meat')">Meat</button>
                <button class="subcategory-btn" onclick="showOrderForm('Milk')">Milk</button>
                <button class="subcategory-btn" onclick="showOrderForm('Fruits')">Fruits</button>
                <button class="subcategory-btn" onclick="showOrderForm('Vegetables')">Vegetables</button>
                <button class="subcategory-btn" onclick="showOrderForm('Flowers')">Flowers</button>
                <button class="subcategory-btn" onclick="showOrderForm('Others')">Others</button>
            </div>
            <div id="food" class="subcategories hidden">
                <h3>Food Category</h3>
                <p>Image Display (Add your images here)</p>
            </div>
            <div id="pharmacy" class="subcategories hidden">
                <h3>Pharmacy Category</h3>
                <p>Image Display (Add your images here)</p>
            </div>
        </div>
        <!-- Order Form Section -->
        <div id="order-form" class="hidden">
            <h2>Place Your Order</h2>
            <form id="deliveryForm">
                <label>Category:</label><input type="text" id="order-category" readonly>
                <label>Name:</label><input type="text" id="name" required>
                <label>Mobile:</label><input type="text" id="mobile" required>
                <label>Order:</label><textarea id="order-details" required></textarea>
                <label>Delivery Address:</label><textarea id="delivery-address" required></textarea>
                <button type="submit">Order via WhatsApp</button>
            </form>
        </div>
        <!-- Contact Section -->
        <div id="contact" class="hidden">
            <h2>Contact Us</h2>
            <p>WhatsApp: <a href="https://wa.me/8977143043" target="_blank">8977143043</a></p>
        </div>
        <!-- Camera Section -->
        <div id="camera" class="hidden">
            <h2>Camera</h2>
            <button onclick="activateCamera()">Open Camera</button>
            <div id="camera-output"></div>
        </div>
        <!-- Maps Section -->
        <div id="maps" class="hidden">
            <h2>Google Maps</h2>
            <a href="https://maps.google.com" target="_blank">Open Google Maps</a>
        </div>
        <!-- Profile Section -->
        <div id="profile" class="hidden">
            <h2>Customer Profile</h2>
            <p>Display customer profile info here.</p>
        </div>
    </div>
    <script>
        // Navigation show/hide
        function showSection(section) {
            ['home', 'contact', 'camera', 'maps', 'profile', 'order-form'].forEach(id => {
                document.getElementById(id).classList.add('hidden');
            });
            document.getElementById(section).classList.remove('hidden');
        }
        // Show subcategories for categories
        function showCategories(cat) {
            ['groceries', 'food', 'pharmacy'].forEach(id => {
                document.getElementById(id).classList.add('hidden');
            });
            document.getElementById(cat).classList.remove('hidden');
        }
        // Show order form
        function showOrderForm(subcat) {
            showSection('order-form');
            document.getElementById('order-category').value = subcat;
        }
        // Handle WhatsApp order
        document.getElementById('deliveryForm').onsubmit = function(e) {
            e.preventDefault();
            var category = document.getElementById('order-category').value;
            var name = document.getElementById('name').value;
            var mobile = document.getElementById('mobile').value;
            var orderDetails = document.getElementById('order-details').value;
            var address = document.getElementById('delivery-address').value;
            var whatsappMsg = `Category: ${category}%0aName: ${name}%0aMobile: ${mobile}%0aOrder: ${orderDetails}%0aAddress: ${address}`;
            window.open(`https://wa.me/8977143043?text=${whatsappMsg}`, "_blank");
        };
        // Camera functionality
        function activateCamera() {
            let camSection = document.getElementById('camera-output');
            camSection.innerHTML = '<p>Camera activated (demo only, browser permissions required).</p>';
        }
        // Default to Home
        showSection('home');
    </script>
</body>
</html>
