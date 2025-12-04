<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>mayoristas-pe.com</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        :root {
            --primary: #e74c3c;
            --secondary: #3498db;
            --dark: #2c3e50;
            --light: #ecf0f1;
            --success: #27ae60;
            --warning: #f39c12;
            --whatsapp: #25D366;
        }

        body {
            background-color: #f5f7fa;
            color: var(--dark);
            display: flex;
            min-height: 100vh;
        }

        /* Sidebar Cart */
        .cart-sidebar {
            width: 320px;
            background: white;
            border-left: 1px solid #ddd;
            padding: 20px;
            box-shadow: -2px 0 10px rgba(0,0,0,0.1);
            display: flex;
            flex-direction: column;
            z-index: 100;
        }

        .cart-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
            padding-bottom: 10px;
            border-bottom: 2px solid var(--primary);
        }

        .cart-header h2 {
            font-size: 1.4rem;
            color: var(--primary);
        }

        .cart-items {
            flex: 1;
            overflow-y: auto;
            max-height: 50vh;
            margin-bottom: 20px;
        }

        .cart-item {
            display: flex;
            justify-content: space-between;
            padding: 12px 0;
            border-bottom: 1px solid #eee;
            align-items: center;
        }

        .cart-item-info {
            flex: 1;
        }

        .cart-item-name {
            font-weight: 600;
            margin-bottom: 4px;
        }

        .cart-item-price {
            font-size: 0.9rem;
            color: #666;
        }

        .cart-item-quantity {
            display: flex;
            align-items: center;
            gap: 8px;
            margin-top: 4px;
        }

        .quantity-btn {
            width: 24px;
            height: 24px;
            background: var(--secondary);
            color: white;
            border: none;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            font-size: 0.8rem;
        }

        .cart-item-total {
            font-weight: bold;
            color: var(--primary);
            min-width: 60px;
            text-align: right;
        }

        .cart-actions {
            display: flex;
            gap: 10px;
            margin-top: 10px;
        }

        .cart-total {
            font-size: 1.4rem;
            font-weight: bold;
            margin: 15px 0;
            padding-top: 15px;
            border-top: 2px solid #ddd;
            color: var(--primary);
            text-align: center;
        }

        .empty-cart {
            text-align: center;
            color: #777;
            padding: 20px 0;
            font-style: italic;
        }

        .cart-buttons {
            display: flex;
            flex-direction: column;
            gap: 12px;
        }

        .btn {
            padding: 12px;
            border: none;
            border-radius: 6px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            text-align: center;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
        }

        .btn-clear {
            background: var(--warning);
            color: white;
        }

        .btn-clear:hover {
            background: #d35400;
        }

        .btn-whatsapp {
            background: var(--whatsapp);
            color: white;
            font-size: 1.1rem;
        }

        .btn-whatsapp:hover {
            background: #128C7E;
            transform: translateY(-2px);
        }

        /* Main Content */
        .main-content {
            flex: 1;
            display: flex;
            flex-direction: column;
        }

        /* Header */
        header {
            background: linear-gradient(135deg, var(--primary), #c0392b);
            color: white;
            padding: 1rem 2rem;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
        }

        .header-container {
            display: flex;
            justify-content: space-between;
            align-items: center;
            max-width: 1200px;
            margin: 0 auto;
        }

        .logo {
            font-size: 1.8rem;
            font-weight: 800;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .logo i {
            font-size: 2rem;
        }

        /* Categories Bar */
        .categories-bar {
            background: white;
            padding: 15px 20px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
            overflow-x: auto;
            white-space: nowrap;
        }

        .categories-container {
            display: inline-flex;
            gap: 15px;
            padding: 5px 0;
        }

        .category-btn {
            background: var(--light);
            border: 2px solid #ddd;
            padding: 8px 20px;
            border-radius: 25px;
            cursor: pointer;
            transition: all 0.3s ease;
            white-space: nowrap;
            font-weight: 600;
        }

        .category-btn:hover, .category-btn.active {
            background: var(--primary);
            color: white;
            border-color: var(--primary);
        }

        /* Hero */
        .hero {
            background: linear-gradient(rgba(0,0,0,0.5), rgba(0,0,0,0.5)), 
                        url('https://images.unsplash.com/photo-1507238691740-187a5b1d37b8?ixlib=rb-4.0.3&auto=format&fit=crop&w=1200&q=80');
            background-size: cover;
            background-position: center;
            height: 250px;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            color: white;
            margin: 20px;
            border-radius: 10px;
        }

        .hero-content h1 {
            font-size: 2.2rem;
            margin-bottom: 15px;
            text-shadow: 0 2px 4px rgba(0,0,0,0.5);
        }

        .hero-content p {
            font-size: 1.1rem;
            max-width: 600px;
            text-shadow: 0 1px 2px rgba(0,0,0,0.5);
        }

        /* Products */
        .products-section {
            padding: 20px;
            flex: 1;
        }

        .section-title {
            text-align: center;
            font-size: 1.8rem;
            margin: 25px 0 15px;
            color: var(--dark);
            position: relative;
        }

        .section-title::after {
            content: '';
            display: block;
            width: 50px;
            height: 3px;
            background: var(--primary);
            margin: 8px auto;
            border-radius: 2px;
        }

        .products-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(240px, 1fr));
            gap: 20px;
            max-width: 1200px;
            margin: 0 auto;
        }

        .product-card {
            background: white;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 3px 8px rgba(0,0,0,0.1);
            transition: transform 0.3s ease;
            display: flex;
            flex-direction: column;
            height: 100%;
        }

        .product-card:hover {
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(0,0,0,0.15);
        }

        .product-img {
            height: 160px;
            background-size: contain;
            background-position: center;
            background-repeat: no-repeat;
            background-color: #f9f9f9;
        }

        .product-info {
            padding: 15px;
            flex: 1;
            display: flex;
            flex-direction: column;
        }

        .product-title {
            font-size: 1.1rem;
            margin-bottom: 8px;
            font-weight: 600;
            flex: 1;
        }

        .product-price {
            font-size: 1.25rem;
            font-weight: bold;
            color: var(--primary);
            margin: 8px 0;
        }

        .add-to-cart {
            width: 100%;
            padding: 8px;
            background: var(--secondary);
            color: white;
            border: none;
            border-radius: 5px;
            font-weight: 600;
            cursor: pointer;
            transition: background 0.3s;
            margin-top: auto;
        }

        .add-to-cart:hover {
            background: #2980b9;
        }

        /* Footer */
        footer {
            background: var(--dark);
            color: white;
            text-align: center;
            padding: 15px;
            margin-top: auto;
        }

        /* Responsive */
        @media (max-width: 768px) {
            body {
                flex-direction: column;
            }
            
            .cart-sidebar {
                width: 100%;
                border-left: none;
                border-top: 1px solid #ddd;
                max-height: 400px;
            }
            
            .categories-bar {
                padding: 10px 15px;
            }
            
            .category-btn {
                padding: 6px 15px;
                font-size: 0.9rem;
            }
        }
    </style>
</head>
<body>
    <!-- Main Content -->
    <div class="main-content">
        <!-- Header -->
        <header>
            <div class="header-container">
                <div class="logo">
                    <i class="fas fa-store"></i>
                    <span>mayoristas-pe.com</span>
                </div>
            </div>
        </header>

        <!-- Categories Bar -->
        <div class="categories-bar">
            <div class="categories-container" id="categories-container">
                <!-- Categories will be added by JavaScript -->
            </div>
        </div>

        <!-- Hero -->
        <section class="hero">
            <div class="hero-content">
                <h1>Productos al por mayor</h1>
                <p>Los mejores precios para tu negocio. Envíos a todo el Perú.</p>
            </div>
        </section>

        <!-- Products -->
        <section class="products-section">
            <h2 class="section-title">Catálogo de Productos</h2>
            <div class="products-grid" id="products-container">
                <!-- Products will be added by JavaScript -->
            </div>
        </section>

        <!-- Footer -->
        <footer>
            <p>&copy; 2025 mayoristas-pe.com - Todos los derechos reservados</p>
        </footer>
    </div>

    <!-- Cart Sidebar -->
    <div class="cart-sidebar">
        <div class="cart-header">
            <h2>Carrito de Compras</h2>
            <i class="fas fa-shopping-cart"></i>
        </div>
        <div class="cart-items" id="cart-items">
            <div class="empty-cart">Tu carrito está vacío</div>
        </div>
        <div class="cart-total" id="cart-total">
            Total: S/ 0.00
        </div>
        <div class="cart-buttons">
            <button class="btn btn-clear" id="clear-cart">
                <i class="fas fa-trash"></i> Borrar Órdenes
            </button>
            <button class="btn btn-whatsapp" id="whatsapp-button">
                <i class="fab fa-whatsapp"></i> Enviar a WhatsApp
            </button>
        </div>
    </div>

    <script>
        // Product data with categories
        const products = [
            { id: 1, name: "Aceite Vegetal 1L", price: 8.50, category: "Alimentos", img: "https://images.unsplash.com/photo-1603532648955-a2a4c44b5af9?ixlib=rb-4.0.3&auto=format&fit=crop&w=200&q=80" },
            { id: 2, name: "Arroz Costeño 5kg", price: 18.90, category: "Alimentos", img: "https://images.unsplash.com/photo-1595837438831-5c31c45a6b63?ixlib=rb-4.0.3&auto=format&fit=crop&w=200&q=80" },
            { id: 3, name: "Azúcar Rubia 1kg", price: 3.20, category: "Alimentos", img: "https://images.unsplash.com/photo-1593069456760-0e8a6a7d7b1b?ixlib=rb-4.0.3&auto=format&fit=crop&w=200&q=80" },
            { id: 4, name: "Fideos Spaghetti", price: 2.80, category: "Alimentos", img: "https://images.unsplash.com/photo-1603532648955-a2a4c44b5af9?ixlib=rb-4.0.3&auto=format&fit=crop&w=200&q=80" },
            { id: 5, name: "Leche Evaporada", price: 3.50, category: "Lácteos", img: "https://images.unsplash.com/photo-1550583724-b2692b85b150?ixlib=rb-4.0.3&auto=format&fit=crop&w=200&q=80" },
            { id: 6, name: "Yogurt Natural", price: 4.20, category: "Lácteos", img: "https://images.unsplash.com/photo-1594032444157-391486e5ef95?ixlib=rb-4.0.3&auto=format&fit=crop&w=200&q=80" },
            { id: 7, name: "Queso Fresco", price: 12.50, category: "Lácteos", img: "https://images.unsplash.com/photo-1603532648955-a2a4c44b5af9?ixlib=rb-4.0.3&auto=format&fit=crop&w=200&q=80" },
            { id: 8, name: "Atún en Lata", price: 4.20, category: "Conservas", img: "https://images.unsplash.com/photo-1603532648955-a2a4c44b5af9?ixlib=rb-4.0.3&auto=format&fit=crop&w=200&q=80" },
            { id: 9, name: "Sardinas en Aceite", price: 3.80, category: "Conservas", img: "https://images.unsplash.com/photo-1603532648955-a2a4c44b5af9?ixlib=rb-4.0.3&auto=format&fit=crop&w=200&q=80" },
            { id: 10, name: "Galletas Soda", price: 2.90, category: "Snacks", img: "https://images.unsplash.com/photo-1603532648955-a2a4c44b5af9?ixlib=rb-4.0.3&auto=format&fit=crop&w=200&q=80" },
            { id: 11, name: "Papas Fritas", price: 3.50, category: "Snacks", img: "https://images.unsplash.com/photo-1598213755091-75390d4b3f1d?ixlib=rb-4.0.3&auto=format&fit=crop&w=200&q=80" },
            { id: 12, name: "Jabón Lavanda", price: 5.70, category: "Aseo", img: "https://images.unsplash.com/photo-1593069456760-0e8a6a7d7b1b?ixlib=rb-4.0.3&auto=format&fit=crop&w=200&q=80" },
            { id: 13, name: "Detergente en Polvo", price: 8.90, category: "Aseo", img: "https://images.unsplash.com/photo-1593069456760-0e8a6a7d7b1b?ixlib=rb-4.0.3&auto=format&fit=crop&w=200&q=80" },
            { id: 14, name: "Papel Higiénico", price: 6.50, category: "Aseo", img: "https://images.unsplash.com/photo-1593069456760-0e8a6a7d7b1b?ixlib=rb-4.0.3&auto=format&fit=crop&w=200&q=80" }
        ];

        // Get unique categories
        const categories = [...new Set(products.map(product => product.category))];

        // Cart state
        let cart = [];
        let currentCategory = 'Todos';

        // DOM elements
        const categoriesContainer = document.getElementById('categories-container');
        const productsContainer = document.getElementById('products-container');
        const cartItems = document.getElementById('cart-items');
        const cartTotal = document.getElementById('cart-total');
        const clearCartBtn = document.getElementById('clear-cart');
        const whatsappButton = document.getElementById('whatsapp-button');

        // Render categories
        function renderCategories() {
            categoriesContainer.innerHTML = '<button class="category-btn active" data-category="Todos">Todos</button>';
            categories.forEach(category => {
                const categoryBtn = document.createElement('button');
                categoryBtn.className = 'category-btn';
                categoryBtn.textContent = category;
                categoryBtn.dataset.category = category;
                categoriesContainer.appendChild(categoryBtn);
            });
        }

        // Render products based on current category
        function renderProducts() {
            productsContainer.innerHTML = '';
            const filteredProducts = currentCategory === 'Todos' 
                ? products 
                : products.filter(product => product.category === currentCategory);

            if (filteredProducts.length === 0) {
                productsContainer.innerHTML = '<p style="text-align: center; grid-column: 1/-1; padding: 40px; color: #666;">No hay productos en esta categoría</p>';
                return;
            }

            filteredProducts.forEach(product => {
                const productCard = document.createElement('div');
                productCard.className = 'product-card';
                productCard.innerHTML = `
                    <div class="product-img" style="background-image: url('${product.img}')"></div>
                    <div class="product-info">
                        <h3 class="product-title">${product.name}</h3>
                        <div class="product-price">S/ ${product.price.toFixed(2)}</div>
                        <button class="add-to-cart" data-id="${product.id}">Agregar al carrito</button>
                    </div>
                `;
                productsContainer.appendChild(productCard);
            });
        }

        // Cart functions
        function addToCart(productId) {
            const product = products.find(p => p.id == productId);
            if (!product) return;

            const existingItem = cart.find(item => item.id === productId);
            if (existingItem) {
                existingItem.quantity += 1;
            } else {
                cart.push({ ...product, quantity: 1 });
            }
            updateCart();
        }

        function removeFromCart(productId) {
            cart = cart.filter(item => item.id !== productId);
            updateCart();
        }

        function updateQuantity(productId, change) {
            const item = cart.find(item => item.id === productId);
            if (item) {
                item.quantity += change;
                if (item.quantity <= 0) {
                    removeFromCart(productId);
                } else {
                    updateCart();
                }
            }
        }

        function updateCart() {
            if (cart.length === 0) {
                cartItems.innerHTML = '<div class="empty-cart">Tu carrito está vacío</div>';
                cartTotal.textContent = 'Total: S/ 0.00';
                return;
            }

            cartItems.innerHTML = '';
            let total = 0;

            cart.forEach(item => {
                const itemTotal = item.price * item.quantity;
                total += itemTotal;

                const cartItem = document.createElement('div');
                cartItem.className = 'cart-item';
                cartItem.innerHTML = `
                    <div class="cart-item-info">
                        <div class="cart-item-name">${item.name}</div>
                        <div class="cart-item-price">S/ ${item.price.toFixed(2)}</div>
                        <div class="cart-item-quantity">
                            <button class="quantity-btn minus" data-id="${item.id}">-</button>
                            <span>${item.quantity}</span>
                            <button class="quantity-btn plus" data-id="${item.id}">+</button>
                        </div>
                    </div>
                    <div class="cart-item-total">S/ ${itemTotal.toFixed(2)}</div>
                `;
                cartItems.appendChild(cartItem);
            });

            cartTotal.textContent = `Total: S/ ${total.toFixed(2)}`;
        }

        function clearCart() {
            if (cart.length === 0) return;
            if (confirm('¿Estás seguro de que quieres borrar todas las órdenes?')) {
                cart = [];
                updateCart();
            }
        }

        function generateWhatsAppMessage() {
            if (cart.length === 0) {
                alert('Tu carrito está vacío. Agrega productos antes de enviar a WhatsApp.');
                return;
            }

            let message = '¡Hola! Quisiera hacer un pedido desde mayoristas-pe.com:\n\n';
            let total = 0;

            cart.forEach((item, index) => {
                const itemTotal = item.price * item.quantity;
                total += itemTotal;
                message += `${index + 1}. ${item.name}\n   Cantidad: ${item.quantity}\n   Precio: S/ ${item.price.toFixed(2)}\n   Subtotal: S/ ${itemTotal.toFixed(2)}\n\n`;
            });

            message += `TOTAL: S/ ${total.toFixed(2)}\n\nGracias por su atención.`;

            // Encode the message for URL
            const encodedMessage = encodeURIComponent(message);
            
            // Replace with your WhatsApp number (include country code, no spaces or dashes)
            const whatsappNumber = '51999999999'; // Example: Peru number
            
            // Open WhatsApp with the message
            window.open(`https://wa.me/${whatsappNumber}?text=${encodedMessage}`, '_blank');
        }

        // Event listeners
        document.addEventListener('click', (e) => {
            // Add to cart
            if (e.target.classList.contains('add-to-cart')) {
                const productId = e.target.getAttribute('data-id');
                addToCart(productId);
            }
            
            // Category filtering
            if (e.target.classList.contains('category-btn')) {
                document.querySelectorAll('.category-btn').forEach(btn => btn.classList.remove('active'));
                e.target.classList.add('active');
                currentCategory = e.target.dataset.category;
                renderProducts();
            }
            
            // Quantity buttons
            if (e.target.classList.contains('minus')) {
                const productId = e.target.dataset.id;
                updateQuantity(productId, -1);
            }
            
            if (e.target.classList.contains('plus')) {
                const productId = e.target.dataset.id;
                updateQuantity(productId, 1);
            }
        });

        // Clear cart button
        clearCartBtn.addEventListener('click', clearCart);

        // WhatsApp button
        whatsappButton.addEventListener('click', generateWhatsAppMessage);

        // Initialize
        renderCategories();
        renderProducts();
    </script>
</body>
</html>

