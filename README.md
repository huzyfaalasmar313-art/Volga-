<!DOCTYPE html>
<html lang="sv">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Teabombs Premium - Lyxiga Tebomber</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary-gold: #D4AF37;
            --secondary-gold: #B8860B;
            --dark-green: #0A5C36;
            --medium-green: #1E7B4C;
            --light-green: #2E8B57;
            --cream: #FFF8E7;
            --dark-red: #8B0000;
            --text-dark: #2C2C2C;
            --text-light: #5A5A5A;
            --border-radius: 12px;
            --shadow: 0 8px 30px rgba(0,0,0,0.12);
            --transition: all 0.3s ease;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #f9f9f9 0%, #e6f2e6 100%);
            color: var(--text-dark);
            line-height: 1.6;
            min-height: 100vh;
        }
        
        .hidden {
            display: none;
        }

        /* Portal Styles */
        .portal-container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 2rem;
            text-align: center;
        }
        
        .portal-header {
            background: linear-gradient(135deg, var(--dark-green) 0%, var(--medium-green) 100%);
            color: white;
            padding: 3rem 2rem;
            border-radius: var(--border-radius);
            margin-bottom: 3rem;
            box-shadow: var(--shadow);
            position: relative;
            overflow: hidden;
        }
        
        .portal-header::before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100" width="100" height="100" opacity="0.1"><path fill="%23D4AF37" d="M50,5 L60,40 L95,40 L65,60 L75,95 L50,75 L25,95 L35,60 L5,40 L40,40 Z"/></svg>');
            background-size: 80px;
        }
        
        .portal-header h1 {
            font-size: 3rem;
            margin-bottom: 1rem;
            color: var(--primary-gold);
            position: relative;
        }
        
        .portal-cards {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 2rem;
            margin-bottom: 3rem;
        }
        
        .portal-card {
            background: white;
            border-radius: var(--border-radius);
            padding: 2.5rem;
            box-shadow: var(--shadow);
            transition: var(--transition);
            position: relative;
            overflow: hidden;
        }
        
        .portal-card::before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 5px;
            background: linear-gradient(90deg, var(--primary-gold) 0%, var(--dark-red) 100%);
        }
        
        .portal-card:hover {
            transform: translateY(-10px);
        }
        
        .portal-card h2 {
            color: var(--dark-green);
            margin-bottom: 1rem;
            font-size: 1.8rem;
        }
        
        .portal-card h2 i {
            margin-right: 0.75rem;
            color: var(--primary-gold);
        }
        
        .portal-btn {
            display: inline-block;
            background: linear-gradient(135deg, var(--primary-gold) 0%, var(--secondary-gold) 100%);
            color: var(--dark-green);
            text-decoration: none;
            padding: 1rem 2rem;
            border-radius: 50px;
            font-weight: 700;
            font-size: 1.1rem;
            transition: var(--transition);
            border: none;
            cursor: pointer;
            width: 100%;
            margin-top: 1rem;
        }
        
        .portal-btn i {
            margin-right: 0.75rem;
        }
        
        .portal-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 20px rgba(212, 175, 55, 0.4);
        }
        
        .portal-btn.secondary {
            background: linear-gradient(135deg, var(--dark-green) 0%, var(--medium-green) 100%);
            color: white;
        }
        
        .portal-btn.secondary:hover {
            box-shadow: 0 8px 20px rgba(30, 123, 76, 0.4);
        }

        /* Password Modal */
        .password-modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0,0,0,0.7);
            justify-content: center;
            align-items: center;
            z-index: 1000;
        }
        
        .password-content {
            background: white;
            padding: 2.5rem;
            border-radius: var(--border-radius);
            width: 90%;
            max-width: 400px;
            text-align: center;
            box-shadow: var(--shadow);
        }
        
        .password-content h3 {
            color: var(--dark-green);
            margin-bottom: 1.5rem;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        
        .password-content h3 i {
            margin-right: 0.75rem;
            color: var(--primary-gold);
        }
        
        .password-input {
            width: 100%;
            padding: 1rem;
            border: 2px solid var(--cream);
            border-radius: 8px;
            font-size: 1rem;
            margin-bottom: 1.5rem;
        }
        
        .password-input:focus {
            border-color: var(--primary-gold);
            outline: none;
            box-shadow: 0 0 0 3px rgba(212, 175, 55, 0.3);
        }
        
        .password-error {
            color: var(--dark-red);
            margin-bottom: 1rem;
            display: none;
        }

        /* Admin Styles */
        .admin-container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 2rem;
        }
        
        .admin-header {
            background: linear-gradient(135deg, var(--dark-green) 0%, var(--medium-green) 100%);
            color: white;
            padding: 2rem;
            border-radius: var(--border-radius);
            margin-bottom: 2rem;
            text-align: center;
            box-shadow: var(--shadow);
            position: relative;
            overflow: hidden;
        }
        
        .admin-header::before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100" width="100" height="100" opacity="0.1"><path fill="%23D4AF37" d="M50,5 L60,40 L95,40 L65,60 L75,95 L50,75 L25,95 L35,60 L5,40 L40,40 Z"/></svg>');
            background-size: 80px;
        }
        
        .admin-header h1 {
            font-size: 2.5rem;
            margin-bottom: 0.5rem;
            color: var(--primary-gold);
            position: relative;
        }
        
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 1.5rem;
            margin-bottom: 2rem;
        }
        
        .stat-card {
            background: white;
            border-radius: var(--border-radius);
            padding: 1.5rem;
            box-shadow: var(--shadow);
            text-align: center;
            position: relative;
            overflow: hidden;
        }
        
        .stat-card::before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 4px;
            background: linear-gradient(90deg, var(--primary-gold) 0%, var(--dark-green) 100%);
        }
        
        .stat-value {
            font-size: 2.5rem;
            font-weight: bold;
            color: var(--dark-green);
            margin: 0.5rem 0;
        }
        
        .stat-label {
            color: var(--text-light);
            font-size: 0.9rem;
        }
        
        .admin-panels {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 2rem;
        }
        
        .admin-panel {
            background: white;
            border-radius: var(--border-radius);
            padding: 2rem;
            box-shadow: var(--shadow);
            position: relative;
            overflow: hidden;
        }
        
        .admin-panel::before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 5px;
            background: linear-gradient(90deg, var(--primary-gold) 0%, var(--dark-red) 100%);
        }
        
        .panel-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 1.5rem;
            padding-bottom: 0.75rem;
            border-bottom: 2px solid var(--cream);
        }
        
        .panel-header h2 {
            color: var(--dark-green);
            display: flex;
            align-items: center;
        }
        
        .panel-header h2 i {
            margin-right: 0.75rem;
            color: var(--primary-gold);
        }
        
        .btn {
            padding: 0.75rem 1.5rem;
            border: none;
            border-radius: var(--border-radius);
            cursor: pointer;
            font-weight: bold;
            transition: var(--transition);
            display: flex;
            align-items: center;
        }
        
        .btn i {
            margin-right: 0.5rem;
        }
        
        .btn-primary {
            background: linear-gradient(135deg, var(--primary-gold) 0%, var(--secondary-gold) 100%);
            color: var(--dark-green);
        }
        
        .btn-danger {
            background: linear-gradient(135deg, #dc3545 0%, #c82333 100%);
            color: white;
        }
        
        .btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        }
        
        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 1rem;
            box-shadow: 0 5px 15px rgba(0,0,0,0.05);
            border-radius: var(--border-radius);
            overflow: hidden;
        }
        
        th, td {
            padding: 1rem;
            text-align: left;
            border-bottom: 1px solid var(--cream);
        }
        
        th {
            background-color: var(--dark-green);
            color: white;
            font-weight: 600;
        }
        
        tr:nth-child(even) {
            background-color: rgba(212, 175, 55, 0.05);
        }
        
        .profit-positive {
            color: var(--light-green);
            font-weight: bold;
        }
        
        .profit-negative {
            color: var(--dark-red);
            font-weight: bold;
        }
        
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0,0,0,0.7);
            justify-content: center;
            align-items: center;
            z-index: 1000;
        }
        
        .modal-content {
            background-color: white;
            padding: 2.5rem;
            border-radius: var(--border-radius);
            width: 90%;
            max-width: 600px;
            max-height: 90vh;
            overflow-y: auto;
            box-shadow: 0 20px 60px rgba(0,0,0,0.3);
            position: relative;
        }
        
        .modal-content::before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 5px;
            background: linear-gradient(90deg, var(--primary-gold) 0%, var(--dark-red) 100%);
        }
        
        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 1.5rem;
        }
        
        .close-modal {
            background: none;
            border: none;
            font-size: 1.8rem;
            cursor: pointer;
            color: var(--text-light);
            transition: var(--transition);
        }
        
        .close-modal:hover {
            color: var(--dark-red);
            transform: rotate(90deg);
        }
        
        .form-group {
            margin-bottom: 1.5rem;
        }
        
        label {
            display: block;
            margin-bottom: 0.75rem;
            font-weight: bold;
            color: var(--dark-green);
        }
        
        input, textarea, select {
            width: 100%;
            padding: 1rem;
            border: 2px solid var(--cream);
            border-radius: 8px;
            font-size: 1rem;
            transition: var(--transition);
        }
        
        input:focus, textarea:focus, select:focus {
            border-color: var(--primary-gold);
            outline: none;
            box-shadow: 0 0 0 3px rgba(212, 175, 55, 0.3);
        }
        
        .submit-btn {
            background: linear-gradient(135deg, var(--primary-gold) 0%, var(--secondary-gold) 100%);
            color: var(--dark-green);
            border: none;
            padding: 1.25rem 2.5rem;
            border-radius: 50px;
            cursor: pointer;
            font-size: 1.2rem;
            font-weight: 700;
            transition: var(--transition);
            width: 100%;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        
        .submit-btn i {
            margin-right: 0.75rem;
        }
        
        .submit-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 20px rgba(212, 175, 55, 0.4);
        }
        
        .notification {
            position: fixed;
            top: 20px;
            right: 20px;
            padding: 1.25rem 1.5rem;
            border-radius: var(--border-radius);
            color: white;
            z-index: 1001;
            display: none;
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
            font-weight: 600;
        }
        
        .notification.success {
            background: linear-gradient(135deg, var(--light-green) 0%, var(--medium-green) 100%);
        }
        
        .notification.error {
            background: linear-gradient(135deg, #dc3545 0%, #c82333 100%);
        }

        /* Customer Styles */
        .customer-header {
            background: linear-gradient(135deg, var(--dark-green) 0%, var(--medium-green) 100%);
            color: white;
            padding: 2rem 1rem;
            text-align: center;
            position: relative;
            overflow: hidden;
        }
        
        .customer-header::before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100" width="100" height="100" opacity="0.1"><path fill="%23D4AF37" d="M50,5 L60,40 L95,40 L65,60 L75,95 L50,75 L25,95 L35,60 L5,40 L40,40 Z"/></svg>');
            background-size: 80px;
        }
        
        .customer-container {
            max-width: 1200px;
            margin: 2rem auto;
            padding: 0 1rem;
        }
        
        .customer-nav {
            background-color: rgba(10, 92, 54, 0.95);
            padding: 1rem;
            position: sticky;
            top: 0;
            z-index: 100;
            box-shadow: 0 4px 12px rgba(0,0,0,0.1);
        }
        
        .customer-nav ul {
            display: flex;
            justify-content: center;
            list-style: none;
            max-width: 1200px;
            margin: 0 auto;
        }
        
        .customer-nav li {
            margin: 0 1.5rem;
        }
        
        .customer-nav a {
            color: white;
            text-decoration: none;
            padding: 0.75rem 1.5rem;
            border-radius: 50px;
            transition: var(--transition);
            display: flex;
            align-items: center;
            font-weight: 600;
        }
        
        .customer-nav a i {
            margin-right: 0.5rem;
        }
        
        .customer-nav a:hover, .customer-nav a.active {
            background-color: var(--primary-gold);
            color: var(--dark-green);
            transform: translateY(-2px);
            box-shadow: 0 4px 8px rgba(0,0,0,0.2);
        }
        
        .section {
            display: none;
            background: white;
            padding: 2.5rem;
            border-radius: var(--border-radius);
            box-shadow: var(--shadow);
            margin-bottom: 2rem;
            position: relative;
            overflow: hidden;
        }
        
        .section::before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 5px;
            background: linear-gradient(90deg, var(--primary-gold) 0%, var(--dark-red) 100%);
        }
        
        .section.active {
            display: block;
            animation: fadeIn 0.5s ease;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        h2 {
            color: var(--dark-green);
            margin-bottom: 1.5rem;
            padding-bottom: 0.75rem;
            border-bottom: 2px solid var(--cream);
            font-size: 2rem;
            display: flex;
            align-items: center;
        }
        
        h2 i {
            margin-right: 0.75rem;
            color: var(--primary-gold);
        }
        
        .products-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 2rem;
        }
        
        .product-card {
            border-radius: var(--border-radius);
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0,0,0,0.08);
            transition: var(--transition);
            background: white;
            position: relative;
        }
        
        .product-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 30px rgba(0,0,0,0.15);
        }
        
        .product-card::before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 4px;
            background: linear-gradient(90deg, var(--primary-gold) 0%, var(--dark-red) 50%, var(--dark-green) 100%);
            z-index: 2;
        }
        
        .product-image {
            width: 100%;
            height: 220px;
            object-fit: cover;
            transition: var(--transition);
        }
        
        .product-card:hover .product-image {
            transform: scale(1.05);
        }
        
        .product-content {
            padding: 1.5rem;
        }
        
        .product-title {
            font-weight: 700;
            margin-bottom: 0.5rem;
            color: var(--dark-green);
            font-size: 1.3rem;
        }
        
        .product-price {
            color: var(--dark-red);
            font-weight: bold;
            margin-bottom: 1rem;
            font-size: 1.4rem;
            display: flex;
            align-items: center;
        }
        
        .product-price i {
            margin-right: 0.5rem;
            color: var(--primary-gold);
        }
        
        .product-description {
            color: var(--text-light);
            margin-bottom: 1.5rem;
            line-height: 1.6;
        }
        
        .product-flavors {
            display: flex;
            flex-wrap: wrap;
            gap: 0.5rem;
            margin-bottom: 1.5rem;
        }
        
        .flavor-tag {
            background-color: var(--cream);
            color: var(--dark-green);
            padding: 0.3rem 0.8rem;
            border-radius: 50px;
            font-size: 0.85rem;
            font-weight: 600;
        }
        
        .flavor-selector {
            margin-bottom: 1.5rem;
        }
        
        .flavor-selector label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: bold;
            color: var(--dark-green);
        }
        
        .quantity-selector {
            display: flex;
            justify-content: center;
            align-items: center;
            margin-bottom: 1.5rem;
        }
        
        .quantity-btn {
            background-color: var(--primary-gold);
            color: var(--dark-green);
            border: none;
            width: 36px;
            height: 36px;
            border-radius: 50%;
            cursor: pointer;
            font-weight: bold;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: var(--transition);
        }
        
        .quantity-btn:hover {
            background-color: var(--secondary-gold);
            transform: scale(1.1);
        }
        
        .quantity-input {
            width: 60px;
            text-align: center;
            margin: 0 0.75rem;
            padding: 0.5rem;
            border: 2px solid var(--cream);
            border-radius: 8px;
            font-weight: bold;
            font-size: 1.1rem;
        }
        
        .add-to-cart {
            background: linear-gradient(135deg, var(--dark-green) 0%, var(--medium-green) 100%);
            color: white;
            border: none;
            padding: 1rem 1.5rem;
            border-radius: 50px;
            cursor: pointer;
            transition: var(--transition);
            width: 100%;
            font-weight: 700;
            font-size: 1.1rem;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        
        .add-to-cart i {
            margin-right: 0.75rem;
        }
        
        .add-to-cart:hover {
            background: linear-gradient(135deg, var(--medium-green) 0%, var(--light-green) 100%);
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(30, 123, 76, 0.4);
        }
        
        .cart-items {
            margin-bottom: 2rem;
        }
        
        .cart-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1.5rem;
            border-bottom: 1px solid var(--cream);
            transition: var(--transition);
        }
        
        .cart-item:hover {
            background-color: rgba(212, 175, 55, 0.05);
        }
        
        .cart-item-info {
            flex-grow: 1;
        }
        
        .cart-item-name {
            font-weight: bold;
            color: var(--dark-green);
            font-size: 1.2rem;
        }
        
        .cart-item-details {
            color: var(--text-light);
            font-size: 0.9rem;
            margin-top: 0.25rem;
        }
        
        .cart-item-price {
            color: var(--dark-red);
            font-weight: bold;
        }
        
        .cart-total {
            text-align: right;
            font-size: 1.5rem;
            font-weight: bold;
            margin-bottom: 1.5rem;
            color: var(--dark-green);
            padding: 1rem;
            background-color: var(--cream);
            border-radius: var(--border-radius);
        }
        
        .checkout-form {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 1.5rem;
        }
        
        .form-group.full-width {
            grid-column: 1 / -1;
        }
        
        footer {
            background: linear-gradient(135deg, var(--dark-green) 0%, var(--medium-green) 100%);
            color: white;
            text-align: center;
            padding: 2rem 1rem;
            margin-top: 3rem;
        }
        
        .footer-content {
            max-width: 1200px;
            margin: 0 auto;
        }
        
        .footer-logo {
            font-size: 2rem;
            font-weight: 700;
            margin-bottom: 1rem;
            color: var(--primary-gold);
        }
        
        .footer-text {
            max-width: 600px;
            margin: 0 auto;
            line-height: 1.6;
        }
        
        @media (max-width: 1024px) {
            .admin-panels {
                grid-template-columns: 1fr;
            }
            
            .stats-grid {
                grid-template-columns: repeat(2, 1fr);
            }
        }
        
        @media (max-width: 768px) {
            .portal-cards {
                grid-template-columns: 1fr;
            }
            
            .checkout-form {
                grid-template-columns: 1fr;
            }
            
            .products-grid {
                grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            }
            
            .customer-nav ul {
                flex-direction: column;
                align-items: center;
            }
            
            .customer-nav li {
                margin: 0.5rem 0;
            }
            
            .portal-header h1 {
                font-size: 2.2rem;
            }
            
            .stats-grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <!-- Portal Startsida -->
    <div id="portal-page">
        <div class="portal-container">
            <div class="portal-header">
                <h1><i class="fas fa-crown"></i> Teabombs Premium</h1>
                <p>Din lyxiga tebombs butik - Admin & Kundportal</p>
            </div>
            
            <div class="portal-cards">
                <div class="portal-card">
                    <h2><i class="fas fa-user-shield"></i> Admin Area</h2>
                    <p>Hantera produkter, beställningar och statistik</p>
                    <button class="portal-btn" onclick="showPasswordModal()">
                        <i class="fas fa-sign-in-alt"></i> Öppna Admin
                    </button>
                </div>
                
                <div class="portal-card">
                    <h2><i class="fas fa-shopping-bag"></i> Butik</h2>
                    <p>Kundens butik - här kan alla handla dina tebomber</p>
                    <button class="portal-btn secondary" onclick="showCustomer()">
                        <i class="fas fa-store"></i> Öppna Butik
                    </button>
                </div>
            </div>
        </div>
    </div>

    <!-- Lösenords Modal -->
    <div class="password-modal" id="password-modal">
        <div class="password-content">
            <h3><i class="fas fa-lock"></i> Admin Åtkomst</h3>
            <p>Ange lösenord för att komma åt admin-området</p>
            <input type="password" class="password-input" id="admin-password" placeholder="Ange lösenord...">
            <div class="password-error" id="password-error">
                <i class="fas fa-exclamation-triangle"></i> Fel lösenord!
            </div>
            <button class="portal-btn" onclick="checkPassword()">
                <i class="fas fa-unlock"></i> Lås upp Admin
            </button>
            <button class="portal-btn secondary" onclick="hidePasswordModal()" style="margin-top: 1rem;">
                <i class="fas fa-times"></i> Avbryt
            </button>
        </div>
    </div>

    <!-- Admin Sida -->
    <div id="admin-page" class="hidden">
        <div class="admin-container">
            <div class="admin-header">
                <h1><i class="fas fa-user-shield"></i> Teabombs Admin</h1>
                <p>Hantera dina produkter, beställningar och se din försäljningsstatistik</p>
                <button class="portal-btn" onclick="showPortal()" style="width: auto; margin-top: 1rem;">
                    <i class="fas fa-arrow-left"></i> Tillbaka till portal
                </button>
            </div>
            
            <div class="stats-grid">
                <div class="stat-card">
                    <div class="stat-label">Totalt Antal Beställningar</div>
                    <div class="stat-value" id="total-orders">0</div>
                    <div class="stat-label">Alla beställningar</div>
                </div>
                <div class="stat-card">
                    <div class="stat-label">Total Försäljning</div>
                    <div class="stat-value" id="total-sales">0 kr</div>
                    <div class="stat-label">Alla beställningar</div>
                </div>
                <div class="stat-card">
                    <div class="stat-label">Total Vinst</div>
                    <div class="stat-value" id="total-profit">0 kr</div>
                    <div class="stat-label">Alla beställningar</div>
                </div>
            </div>
            
            <div class="admin-panels">
                <div class="admin-panel">
                    <div class="panel-header">
                        <h2><i class="fas fa-box-open"></i> Produkter</h2>
                        <button class="btn btn-primary" id="add-product-btn">
                            <i class="fas fa-plus-circle"></i> Lägg till produkt
                        </button>
                    </div>
                    <table id="admin-products-table">
                        <thead>
                            <tr>
                                <th>Namn</th>
                                <th>Försäljningspris</th>
                                <th>Kostnad</th>
                                <th>Vinst</th>
                                <th>Åtgärder</th>
                            </tr>
                        </thead>
                        <tbody id="admin-products-body">
                            <!-- Produkter läggs till här -->
                        </tbody>
                    </table>
                </div>
                
                <div class="admin-panel">
                    <div class="panel-header">
                        <h2><i class="fas fa-clipboard-list"></i> Beställningar</h2>
                        <button class="btn btn-danger" id="clear-orders-btn">
                            <i class="fas fa-trash-alt"></i> Rensa alla
                        </button>
                    </div>
                    <table id="admin-orders-table">
                        <thead>
                            <tr>
                                <th>Kund</th>
                                <th>Produkter</th>
                                <th>Totalt</th>
                                <th>Vinst</th>
                                <th>Datum</th>
                            </tr>
                        </thead>
                        <tbody id="admin-orders-body">
                            <!-- Beställningar läggs till här -->
                        </tbody>
                    </table>
                </div>
            </div>
        </div>
        
        <!-- Modal för att lägga till/redigera produkter -->
        <div class="modal" id="product-modal">
            <div class="modal-content">
                <div class="modal-header">
                    <h3 id="modal-title"><i class="fas fa-cube"></i> Lägg till produkt</h3>
                    <button class="close-modal">&times;</button>
                </div>
                <form id="product-form">
                    <input type="hidden" id="product-id">
                    <div class="form-group">
                        <label for="product-name">Produktnamn</label>
                        <input type="text" id="product-name" required>
                    </div>
                    <div class="form-group">
                        <label for="product-price">Försäljningspris (kr)</label>
                        <input type="number" id="product-price" min="0" step="0.01" required>
                    </div>
                    <div class="form-group">
                        <label for="product-cost">Tillverkningskostnad (kr)</label>
                        <input type="number" id="product-cost" min="0" step="0.01" required>
                    </div>
                    <div class="form-group">
                        <label for="product-description">Beskrivning</label>
                        <textarea id="product-description" rows="3" required></textarea>
                    </div>
                    <div class="form-group">
                        <label for="product-flavors">Smaker (separera med kommatecken)</label>
                        <input type="text" id="product-flavors" placeholder="Choklad, vanilj, kanel...">
                    </div>
                    <div class="form-group">
                        <label for="product-image">Bild-URL</label>
                        <input type="text" id="product-image">
                    </div>
                    <button type="submit" class="submit-btn"><i class="fas fa-save"></i> Spara produkt</button>
                </form>
            </div>
        </div>
    </div>

    <!-- Kund Sida -->
    <div id="customer-page" class="hidden">
        <div class="customer-header">
            <div class="header-content">
                <h1><i class="fas fa-crown"></i> Teabombs Premium</h1>
                <p class="tagline">Lyxiga julpresenter för att värma hjärtan</p>
                <div class="intro-text">
                    <p>Upptäck vårt exklusiva utbud av tebomber - perfekta julpresenter till din partner, familj och vänner. Varje tebomb är noggrant handgjord med premiumingredienser för en oförglömlig smakupplevelse som sprider julstämning.</p>
                </div>
                <button class="portal-btn" onclick="showPortal()" style="width: auto; margin-top: 1rem;">
                    <i class="fas fa-arrow-left"></i> Tillbaka till portal
                </button>
            </div>
        </div>
        
        <nav class="customer-nav">
            <ul>
                <li><a href="#" class="nav-link active" data-section="products"><i class="fas fa-gift"></i> Våra Teabombs</a></li>
                <li><a href="#" class="nav-link" data-section="cart"><i class="fas fa-shopping-cart"></i> Varukorg <span id="cart-count">(0)</span></a></li>
            </ul>
        </nav>
        
        <div class="customer-container">
            <!-- Produktsektion -->
            <section id="products" class="section active">
                <h2><i class="fas fa-star"></i> Våra Premium Teabombs</h2>
                <div class="products-grid" id="products-container">
                    <!-- Produkter läggs till dynamiskt här -->
                </div>
            </section>
            
            <!-- Varukorgsektion -->
            <section id="cart" class="section">
                <h2><i class="fas fa-shopping-cart"></i> Din Varukorg</h2>
                <div class="cart-items" id="cart-items">
                    <!-- Varukorgsartiklar läggs till dynamiskt här -->
                </div>
                <div class="cart-total" id="cart-total">
                    Totalt: 0 kr
                </div>
                <button class="portal-btn secondary" id="checkout-btn"><i class="fas fa-credit-card"></i> Gå till kassan</button>
            </section>
            
            <!-- Kassasektion -->
            <section id="checkout" class="section">
                <h2><i class="fas fa-truck"></i> Leveransinformation</h2>
                <form id="checkout-form" class="checkout-form">
                    <div class="form-group">
                        <label for="first-name">Förnamn</label>
                        <input type="text" id="first-name" required>
                    </div>
                    <div class="form-group">
                        <label for="last-name">Efternamn</label>
                        <input type="text" id="last-name" required>
                    </div>
                    <div class="form-group full-width">
                        <label for="email">E-postadress</label>
                        <input type="email" id="email" required>
                    </div>
                    <div class="form-group">
                        <label for="phone">Telefonnummer</label>
                        <input type="tel" id="phone" required>
                    </div>
                    <div class="form-group full-width">
                        <label for="address">Adress</label>
                        <textarea id="address" rows="3" required></textarea>
                    </div>
                    <div class="form-group full-width">
                        <label for="message">Meddelande (frivilligt)</label>
                        <textarea id="message" rows="3" placeholder="Önskemål om personlig hälsning eller annat..."></textarea>
                    </div>
                    <button type="submit" class="portal-btn"><i class="fas fa-paper-plane"></i> Skicka beställning</button>
                </form>
            </section>
            
            <!-- Orderbekräftelse -->
            <section id="confirmation" class="section">
                <h2><i class="fas fa-check-circle"></i> Tack för din beställning!</h2>
                <div id="order-summary">
                    <!-- Orderdetaljer läggs till här -->
                </div>
                <button class="portal-btn secondary" onclick="continueShopping()">
                    <i class="fas fa-shopping-bag"></i> Fortsätt handla
                </button>
            </section>
        </div>
        
        <footer>
            <div class="footer-content">
                <div class="footer-logo">Teabombs Premium</div>
                <p class="footer-text">Skapa oförglömliga stunder med våra exklusiva tebomber. Perfekt som julpresenter, gåvor till nära och kära eller bara för att unna dig själv en lyxig paus.</p>
                <p>© 2023 Teabombs Premium. Alla rättigheter förbehållna.</p>
            </div>
        </footer>
    </div>

    <!-- Notifikationer -->
    <div class="notification" id="notification"></div>

    <script>
        // ===== KONFIGURATION =====
        const ADMIN_PASSWORD = "Amhhai=201iahhma6";

        // ===== PORTAL NAVIGATION =====
        function showPortal() {
            document.getElementById('portal-page').classList.remove('hidden');
            document.getElementById('admin-page').classList.add('hidden');
            document.getElementById('customer-page').classList.add('hidden');
            hidePasswordModal();
        }
        
        function showAdmin() {
            document.getElementById('portal-page').classList.add('hidden');
            document.getElementById('admin-page').classList.remove('hidden');
            document.getElementById('customer-page').classList.add('hidden');
            hidePasswordModal();
            loadAdmin();
        }
        
        function showCustomer() {
            document.getElementById('portal-page').classList.add('hidden');
            document.getElementById('admin-page').classList.add('hidden');
            document.getElementById('customer-page').classList.remove('hidden');
            loadCustomer();
        }

        // ===== LÖSENORD FUNKTIONER =====
        function showPasswordModal() {
            document.getElementById('password-modal').style.display = 'flex';
            document.getElementById('admin-password').value = '';
            document.getElementById('password-error').style.display = 'none';
            document.getElementById('admin-password').focus();
        }

        function hidePasswordModal() {
            document.getElementById('password-modal').style.display = 'none';
        }

        function checkPassword() {
            const enteredPassword = document.getElementById('admin-password').value;
            const errorElement = document.getElementById('password-error');
            
            if (enteredPassword === ADMIN_PASSWORD) {
                showAdmin();
            } else {
                errorElement.style.display = 'block';
                document.getElementById('admin-password').value = '';
                document.getElementById('admin-password').focus();
                
                // Lägg till lite skakning för effekt
                const input = document.getElementById('admin-password');
                input.style.transform = 'translateX(-10px)';
                setTimeout(() => input.style.transform = 'translateX(10px)', 100);
                setTimeout(() => input.style.transform = 'translateX(-10px)', 200);
                setTimeout(() => input.style.transform = 'translateX(0)', 300);
            }
        }

        // Lägg till enter-tangent support för lösenord
        document.getElementById('admin-password').addEventListener('keypress', function(e) {
            if (e.key === 'Enter') {
                checkPassword();
            }
        });

        // ===== DATA =====
        let products = JSON.parse(localStorage.getItem('teabombs_products')) || [
            {
                id: 1,
                name: "Julglöd Te Bomb",
                price: 89,
                cost: 45,
                description: "En festlig tebomb med smaker av kanel, apelsin och nejlikor som sprider äkta julstämning. Perfekt att njuta av framför en brasa.",
                flavors: ["Kanel", "Apelsin", "Nejlikor", "Vanilj"],
                image: "https://images.unsplash.com/photo-1571934811356-5cc061b6821f?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=800&q=80"
            },
            {
                id: 2,
                name: "Choklad Mint Explosion",
                price: 95,
                cost: 50,
                description: "En lyxig kombination av premium choklad och färsk pepparmint. Denna tebomb är som en eftermiddag på en exklusiv spaanläggning.",
                flavors: ["Mörk choklad", "Pepparmint", "Kakao"],
                image: "https://images.unsplash.com/photo-1597481499750-3e11b45fa683?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=800&q=80"
            },
            {
                id: 3,
                name: "Himlakram Te Bomb",
                price: 79,
                cost: 40,
                description: "En ljuvlig blandning av lavendel, honung och vanilj som lugnar sinnet och ger en känsla av ren lyx. Perfekt avslappning.",
                flavors: ["Lavendel", "Honung", "Vanilj", "Kardemumma"],
                image: "https://images.unsplash.com/photo-1621382829715-3c56d8162b66?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=800&q=80"
            }
        ];
        
        // Varukorg
        let cart = JSON.parse(localStorage.getItem('teabombs_cart')) || [];
        
        // Beställningar
        let orders = JSON.parse(localStorage.getItem('teabombs_orders')) || [];

        // ===== ADMIN FUNKTIONER =====
        function loadAdmin() {
            updateStats();
            loadProductsTable();
            loadOrdersTable();
            
            document.getElementById('add-product-btn').onclick = () => {
                document.getElementById('modal-title').innerHTML = '<i class="fas fa-cube"></i> Lägg till produkt';
                document.getElementById('product-form').reset();
                document.getElementById('product-id').value = '';
                document.getElementById('product-modal').style.display = 'flex';
            };
            
            document.getElementById('product-form').onsubmit = function(e) {
                e.preventDefault();
                saveProduct();
            };
            
            document.getElementById('clear-orders-btn').onclick = function() {
                if (confirm('Är du säker på att du vill radera alla beställningar? Detta kan inte ångras.')) {
                    orders = [];
                    localStorage.setItem('teabombs_orders', JSON.stringify(orders));
                    loadOrdersTable();
                    updateStats();
                    showNotification('Alla beställningar har raderats!', 'success');
                }
            };
            
            // Stäng modal
            document.querySelector('.close-modal').addEventListener('click', () => {
                document.getElementById('product-modal').style.display = 'none';
            });
        }

        function updateStats() {
            // Räkna totala beställningar
            document.getElementById('total-orders').textContent = orders.length;
            
            // Räkna total försäljning
            const totalSales = orders.reduce((total, order) => total + order.total, 0);
            document.getElementById('total-sales').textContent = `${totalSales} kr`;
            
            // Räkna total vinst
            const totalProfit = orders.reduce((total, order) => total + order.profit, 0);
            document.getElementById('total-profit').textContent = `${totalProfit} kr`;
        }

        function loadProductsTable() {
            const tbody = document.getElementById('admin-products-body');
            tbody.innerHTML = '';
            
            products.forEach(product => {
                const profit = product.price - product.cost;
                const profitClass = profit >= 0 ? 'profit-positive' : 'profit-negative';
                
                const row = document.createElement('tr');
                
                row.innerHTML = `
                    <td>${product.name}</td>
                    <td>${product.price} kr</td>
                    <td>${product.cost} kr</td>
                    <td class="${profitClass}">${profit} kr</td>
                    <td>
                        <button class="btn btn-primary edit-product" data-id="${product.id}"><i class="fas fa-edit"></i> Redigera</button>
                        <button class="btn btn-danger delete-product" data-id="${product.id}"><i class="fas fa-trash-alt"></i> Ta bort</button>
                    </td>
                `;
                
                tbody.appendChild(row);
            });
            
            // Lägg till event listeners för produktredigering och borttagning
            document.querySelectorAll('.edit-product').forEach(btn => {
                btn.addEventListener('click', (e) => {
                    const productId = parseInt(e.target.getAttribute('data-id'));
                    editProduct(productId);
                });
            });
            
            document.querySelectorAll('.delete-product').forEach(btn => {
                btn.addEventListener('click', (e) => {
                    const productId = parseInt(e.target.getAttribute('data-id'));
                    deleteProduct(productId);
                });
            });
        }

        function loadOrdersTable() {
            const tbody = document.getElementById('admin-orders-body');
            tbody.innerHTML = '';
            
            if (orders.length === 0) {
                tbody.innerHTML = '<tr><td colspan="5" style="text-align: center;">Inga beställningar än</td></tr>';
            } else {
                orders.forEach(order => {
                    const profitClass = order.profit >= 0 ? 'profit-positive' : 'profit-negative';
                    
                    const itemsText = order.items.map(item => 
                        `${item.name} (${item.quantity} st)${item.selectedFlavor ? ` - ${item.selectedFlavor}` : ''}`
                    ).join(', ');
                    
                    const row = document.createElement('tr');
                    
                    row.innerHTML = `
                        <td>${order.customer.firstName} ${order.customer.lastName}</td>
                        <td>${itemsText}</td>
                        <td>${order.total} kr</td>
                        <td class="${profitClass}">${order.profit} kr</td>
                        <td>${order.date}</td>
                    `;
                    
                    tbody.appendChild(row);
                });
            }
        }

        function saveProduct() {
            const productId = document.getElementById('product-id').value;
            const name = document.getElementById('product-name').value;
            const price = parseFloat(document.getElementById('product-price').value);
            const cost = parseFloat(document.getElementById('product-cost').value);
            const description = document.getElementById('product-description').value;
            const flavors = document.getElementById('product-flavors').value.split(',').map(f => f.trim()).filter(f => f);
            const image = document.getElementById('product-image').value || 'https://images.unsplash.com/photo-1571934811356-5cc061b6821f?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=800&q=80';
            
            if (productId) {
                // Redigera befintlig produkt
                const index = products.findIndex(p => p.id === parseInt(productId));
                if (index !== -1) {
                    products[index] = {
                        ...products[index],
                        name,
                        price,
                        cost,
                        description,
                        flavors,
                        image
                    };
                }
            } else {
                // Lägg till ny produkt
                const newId = products.length > 0 ? Math.max(...products.map(p => p.id)) + 1 : 1;
                products.push({
                    id: newId,
                    name,
                    price,
                    cost,
                    description,
                    flavors,
                    image
                });
            }
            
            localStorage.setItem('teabombs_products', JSON.stringify(products));
            loadProductsTable();
            document.getElementById('product-modal').style.display = 'none';
            showNotification('Produkten har sparats!', 'success');
        }

        function editProduct(productId) {
            const product = products.find(p => p.id === productId);
            
            if (!product) return;
            
            document.getElementById('modal-title').innerHTML = '<i class="fas fa-edit"></i> Redigera produkt';
            document.getElementById('product-id').value = product.id;
            document.getElementById('product-name').value = product.name;
            document.getElementById('product-price').value = product.price;
            document.getElementById('product-cost').value = product.cost;
            document.getElementById('product-description').value = product.description;
            document.getElementById('product-flavors').value = product.flavors ? product.flavors.join(', ') : '';
            document.getElementById('product-image').value = product.image;
            
            document.getElementById('product-modal').style.display = 'flex';
        }

        function deleteProduct(productId) {
            if (confirm('Är du säker på att du vill ta bort denna produkt?')) {
                products = products.filter(p => p.id !== productId);
                localStorage.setItem('teabombs_products', JSON.stringify(products));
                loadProductsTable();
                showNotification('Produkten har tagits bort!', 'success');
            }
        }

        // ===== KUND FUNKTIONER =====
        function loadCustomer() {
            // DOM-element för kund
            const productsContainer = document.getElementById('products-container');
            const cartItemsContainer = document.getElementById('cart-items');
            const cartTotalElement = document.getElementById('cart-total');
            const cartCountElement = document.getElementById('cart-count');
            const checkoutBtn = document.getElementById('checkout-btn');
            const checkoutForm = document.getElementById('checkout-form');
            
            // Navigering
            document.querySelectorAll('.nav-link').forEach(link => {
                link.addEventListener('click', (e) => {
                    e.preventDefault();
                    const targetSection = e.target.getAttribute('data-section');
                    
                    // Uppdatera aktiv navigeringslänk
                    document.querySelectorAll('.nav-link').forEach(l => l.classList.remove('active'));
                    e.target.classList.add('active');
                    
                    // Visa rätt sektion
                    document.querySelectorAll('.section').forEach(section => {
                        section.classList.remove('active');
                    });
                    
                    if (targetSection === 'cart') {
                        document.getElementById('cart').classList.add('active');
                        updateCartDisplay();
                    } else {
                        document.getElementById('products').classList.add('active');
                    }
                });
            });
            
            // Visa produkter
            function displayProducts() {
                productsContainer.innerHTML = '';
                
                products.forEach(product => {
                    const productCard = document.createElement('div');
                    productCard.className = 'product-card';
                    
                    const flavorsHTML = product.flavors ? 
                        `<div class="product-flavors">${product.flavors.map(flavor => `<span class="flavor-tag">${flavor}</span>`).join('')}</div>` : '';
                    
                    const flavorSelectorHTML = product.flavors && product.flavors.length > 0 ? 
                        `<div class="flavor-selector">
                            <label for="flavor-${product.id}">Välj smak:</label>
                            <select id="flavor-${product.id}">
                                <option value="">Välj en smak</option>
                                ${product.flavors.map(flavor => `<option value="${flavor}">${flavor}</option>`).join('')}
                            </select>
                        </div>` : '';
                    
                    productCard.innerHTML = `
                        <img src="${product.image}" alt="${product.name}" class="product-image">
                        <div class="product-content">
                            <div class="product-title">${product.name}</div>
                            <div class="product-price"><i class="fas fa-tag"></i> ${product.price} kr</div>
                            <div class="product-description">${product.description}</div>
                            ${flavorsHTML}
                            ${flavorSelectorHTML}
                            <div class="quantity-selector">
                                <button class="quantity-btn minus" data-id="${product.id}">-</button>
                                <input type="number" class="quantity-input" data-id="${product.id}" value="1" min="1">
                                <button class="quantity-btn plus" data-id="${product.id}">+</button>
                            </div>
                            <button class="add-to-cart" data-id="${product.id}"><i class="fas fa-cart-plus"></i> Lägg i varukorg</button>
                        </div>
                    `;
                    
                    productsContainer.appendChild(productCard);
                });
                
                // Lägg till event listeners för kvantitetsknappar
                document.querySelectorAll('.quantity-btn.plus').forEach(btn => {
                    btn.addEventListener('click', (e) => {
                        const productId = parseInt(e.target.getAttribute('data-id'));
                        const input = document.querySelector(`.quantity-input[data-id="${productId}"]`);
                        input.value = parseInt(input.value) + 1;
                    });
                });
                
                document.querySelectorAll('.quantity-btn.minus').forEach(btn => {
                    btn.addEventListener('click', (e) => {
                        const productId = parseInt(e.target.getAttribute('data-id'));
                        const input = document.querySelector(`.quantity-input[data-id="${productId}"]`);
                        if (parseInt(input.value) > 1) {
                            input.value = parseInt(input.value) - 1;
                        }
                    });
                });
                
                // Lägg till event listeners för "Lägg i varukorg"-knappar
                document.querySelectorAll('.add-to-cart').forEach(btn => {
                    btn.addEventListener('click', (e) => {
                        const productId = parseInt(e.target.getAttribute('data-id'));
                        const quantityInput = document.querySelector(`.quantity-input[data-id="${productId}"]`);
                        const quantity = parseInt(quantityInput.value);
                        const flavorSelect = document.getElementById(`flavor-${productId}`);
                        const selectedFlavor = flavorSelect ? flavorSelect.value : '';
                        
                        addToCart(productId, quantity, selectedFlavor);
                        showNotification('Produkten har lagts till i varukorgen!', 'success');
                    });
                });
            }
            
            // Lägg till produkt i varukorg
            function addToCart(productId, quantity, selectedFlavor) {
                const product = products.find(p => p.id === productId);
                
                if (!product) return;
                
                // Kolla om vald smak är obligatorisk
                if (product.flavors && product.flavors.length > 0 && !selectedFlavor) {
                    showNotification('Vänligen välj en smak först!', 'error');
                    return;
                }
                
                const existingItemIndex = cart.findIndex(item => 
                    item.id === productId && item.selectedFlavor === selectedFlavor
                );
                
                if (existingItemIndex !== -1) {
                    cart[existingItemIndex].quantity += quantity;
                } else {
                    cart.push({
                        id: product.id,
                        name: product.name,
                        price: product.price,
                        cost: product.cost,
                        quantity: quantity,
                        selectedFlavor: selectedFlavor
                    });
                }
                
                localStorage.setItem('teabombs_cart', JSON.stringify(cart));
                updateCartCount();
            }
            
            // Uppdatera varukorgsräknare
            function updateCartCount() {
                const cartCount = cart.reduce((total, item) => total + item.quantity, 0);
                cartCountElement.textContent = `(${cartCount})`;
            }
            
            // Uppdatera varukorgsvisningen
            function updateCartDisplay() {
                cartItemsContainer.innerHTML = '';
                
                if (cart.length === 0) {
                    cartItemsContainer.innerHTML = '<p style="text-align: center; padding: 2rem;">Din varukorg är tom</p>';
                    cartTotalElement.textContent = 'Totalt: 0 kr';
                    checkoutBtn.style.display = 'none';
                    return;
                }
                
                checkoutBtn.style.display = 'block';
                let total = 0;
                
                cart.forEach((item, index) => {
                    const itemTotal = item.price * item.quantity;
                    total += itemTotal;
                    
                    const cartItem = document.createElement('div');
                    cartItem.className = 'cart-item';
                    
                    cartItem.innerHTML = `
                        <div class="cart-item-info">
                            <div class="cart-item-name">${item.name}</div>
                            <div class="cart-item-details">
                                ${item.selectedFlavor ? `Smak: ${item.selectedFlavor} • ` : ''}
                                ${item.price} kr x ${item.quantity}
                            </div>
                        </div>
                        <div class="cart-item-total">${itemTotal} kr</div>
                    `;
                    
                    cartItemsContainer.appendChild(cartItem);
                });
                
                cartTotalElement.textContent = `Totalt: ${total} kr`;
            }
            
            // Gå till kassan
            checkoutBtn.addEventListener('click', () => {
                document.querySelectorAll('.section').forEach(section => {
                    section.classList.remove('active');
                });
                document.getElementById('checkout').classList.add('active');
            });
            
            // Hantera beställning
            checkoutForm.addEventListener('submit', (e) => {
                e.preventDefault();
                
                if (cart.length === 0) {
                    showNotification('Varukorgen är tom!', 'error');
                    return;
                }
                
                const order = {
                    id: Date.now(),
                    customer: {
                        firstName: document.getElementById('first-name').value,
                        lastName: document.getElementById('last-name').value,
                        email: document.getElementById('email').value,
                        phone: document.getElementById('phone').value,
                        address: document.getElementById('address').value,
                        message: document.getElementById('message').value
                    },
                    items: [...cart],
                    total: cart.reduce((total, item) => total + (item.price * item.quantity), 0),
                    totalCost: cart.reduce((total, item) => total + (item.cost * item.quantity), 0),
                    profit: cart.reduce((total, item) => total + ((item.price - item.cost) * item.quantity), 0),
                    date: new Date().toLocaleString('sv-SE')
                };
                
                orders.push(order);
                localStorage.setItem('teabombs_orders', JSON.stringify(orders));
                
                // Visa orderbekräftelse
                showOrderConfirmation(order);
                
                // Rensa varukorgen
                cart = [];
                localStorage.setItem('teabombs_cart', JSON.stringify(cart));
                updateCartCount();
            });
            
            // Visa orderbekräftelse
            function showOrderConfirmation(order) {
                const orderSummary = document.getElementById('order-summary');
                let summaryHTML = `
                    <div style="background: var(--cream); padding: 1.5rem; border-radius: var(--border-radius); margin-bottom: 2rem;">
                        <h3 style="color: var(--dark-green); margin-bottom: 1rem;">Order #${order.id}</h3>
                        <p><strong>Beställd av:</strong> ${order.customer.firstName} ${order.customer.lastName}</p>
                        <p><strong>E-post:</strong> ${order.customer.email}</p>
                        <p><strong>Telefon:</strong> ${order.customer.phone}</p>
                        <p><strong>Leveransadress:</strong> ${order.customer.address}</p>
                        ${order.customer.message ? `<p><strong>Meddelande:</strong> ${order.customer.message}</p>` : ''}
                    </div>
                    <div style="margin-bottom: 2rem;">
                        <h4 style="color: var(--dark-green); margin-bottom: 1rem;">Beställda produkter:</h4>
                        <ul style="list-style: none; padding: 0;">
                `;
                
                order.items.forEach(item => {
                    summaryHTML += `
                        <li style="padding: 0.5rem 0; border-bottom: 1px solid var(--cream);">
                            ${item.name}${item.selectedFlavor ? ` (${item.selectedFlavor})` : ''} - 
                            ${item.quantity} st x ${item.price} kr = ${item.quantity * item.price} kr
                        </li>
                    `;
                });
                
                summaryHTML += `
                        </ul>
                        <div style="text-align: right; margin-top: 1rem; font-size: 1.2rem; font-weight: bold;">
                            Totalt: ${order.total} kr
                        </div>
                    </div>
                    <div style="background: var(--light-green); color: white; padding: 1rem; border-radius: var(--border-radius); text-align: center;">
                        <i class="fas fa-check-circle" style="font-size: 2rem; margin-bottom: 0.5rem;"></i>
                        <p>Tack för din beställning! Du kommer att få ett bekräftelsemail inom kort.</p>
                    </div>
                `;
                
                orderSummary.innerHTML = summaryHTML;
                
                document.querySelectorAll('.section').forEach(section => {
                    section.classList.remove('active');
                });
                document.getElementById('confirmation').classList.add('active');
            }
            
            // Fortsätt handla
            window.continueShopping = function() {
                document.querySelectorAll('.section').forEach(section => {
                    section.classList.remove('active');
                });
                document.getElementById('products').classList.add('active');
                document.querySelectorAll('.nav-link').forEach(l => l.classList.remove('active'));
                document.querySelector('.nav-link[data-section="products"]').classList.add('active');
                
                // Återställ formuläret
                checkoutForm.reset();
            };
            
            // Initiera kundsida
            displayProducts();
            updateCartCount();
            updateCartDisplay();
        }

        // ===== HJÄLP FUNKTIONER =====
        function showNotification(message, type) {
            const notification = document.getElementById('notification');
            notification.textContent = message;
            notification.className = `notification ${type}`;
            notification.style.display = 'block';
            
            setTimeout(() => {
                notification.style.display = 'none';
            }, 5000);
        }

        // Starta portalen
        showPortal();
    </script>
</body>
</html>
