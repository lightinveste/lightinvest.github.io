<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>INVEST WITH LIGHT - Smart Investment Platform</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #1a1a2e 0%, #16213e 50%, #0f3460 100%);
            min-height: 100vh;
            color: white;
            position: relative;
            overflow-x: hidden;
        }

        body::before {
            content: '';
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: radial-gradient(circle at 20% 50%, rgba(255, 215, 0, 0.1) 0%, transparent 50%),
                        radial-gradient(circle at 80% 20%, rgba(255, 165, 0, 0.1) 0%, transparent 50%),
                        radial-gradient(circle at 40% 80%, rgba(255, 107, 107, 0.1) 0%, transparent 50%);
            pointer-events: none;
            z-index: -1;
        }

        .app-container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }

        .login-container {
            max-width: 400px;
            margin: 0 auto;
            padding: 20px;
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .login-card {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(20px);
            border-radius: 20px;
            padding: 40px;
            border: 1px solid rgba(255, 255, 255, 0.2);
            text-align: center;
            animation: slideIn 0.6s ease-out;
            width: 100%;
        }

        .login-header {
            margin-bottom: 30px;
        }

        .login-header h1 {
            font-size: 2.2em;
            margin-bottom: 10px;
            background: linear-gradient(45deg, #FFD700, #FFA500, #FF6B6B);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            text-shadow: 0 0 20px rgba(255, 215, 0, 0.3);
        }

        .login-form {
            display: flex;
            flex-direction: column;
            gap: 20px;
        }

        .login-form input {
            padding: 15px 20px;
            border: 1px solid rgba(255, 255, 255, 0.3);
            border-radius: 12px;
            background: rgba(255, 255, 255, 0.1);
            color: white;
            font-size: 1em;
            transition: all 0.3s ease;
        }

        .login-form input:focus {
            outline: none;
            border-color: #FFD700;
            box-shadow: 0 0 0 3px rgba(255, 215, 0, 0.2);
        }

        .login-form input::placeholder {
            color: rgba(255, 255, 255, 0.6);
        }

        .login-btn {
            background: linear-gradient(45deg, #FFD700, #FFA500);
            color: white;
            border: none;
            padding: 15px 30px;
            border-radius: 12px;
            font-size: 1.1em;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(255, 215, 0, 0.3);
        }

        .login-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(255, 215, 0, 0.4);
        }

        .login-toggle {
            margin-top: 20px;
            color: rgba(255, 255, 255, 0.7);
        }

        .login-toggle a {
            color: #FFD700;
            text-decoration: none;
            font-weight: 600;
        }

        .login-toggle a:hover {
            text-decoration: underline;
        }

        .header {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(20px);
            border-radius: 20px;
            padding: 30px;
            margin-bottom: 30px;
            text-align: center;
            border: 1px solid rgba(255, 255, 255, 0.2);
            animation: fadeIn 0.6s ease-out;
            position: relative;
        }

        .auth-controls {
            position: absolute;
            top: 20px;
            right: 20px;
            display: flex;
            gap: 15px;
            align-items: center;
        }

        .user-info {
            display: flex;
            align-items: center;
            gap: 10px;
            background: rgba(255, 255, 255, 0.1);
            padding: 8px 16px;
            border-radius: 50px;
            border: 1px solid rgba(255, 255, 255, 0.2);
        }

        .user-avatar {
            width: 32px;
            height: 32px;
            border-radius: 50%;
            background: linear-gradient(45deg, #FFD700, #FFA500);
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            color: white;
            font-size: 14px;
        }

        .logout-btn {
            background: rgba(255, 255, 255, 0.1);
            color: white;
            border: 1px solid rgba(255, 255, 255, 0.3);
            padding: 8px 16px;
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.3s ease;
            font-size: 0.9em;
        }

        .logout-btn:hover {
            background: rgba(255, 255, 255, 0.2);
            transform: translateY(-2px);
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .header h1 {
            font-size: 2.5em;
            margin-bottom: 10px;
            background: linear-gradient(45deg, #FFD700, #FFA500, #FF6B6B);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            text-shadow: 0 0 20px rgba(255, 215, 0, 0.3);
        }

        .dashboard {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 30px;
            margin-bottom: 30px;
        }

        .balance-card {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(20px);
            border-radius: 20px;
            padding: 30px;
            border: 1px solid rgba(255, 255, 255, 0.2);
            animation: slideInLeft 0.6s ease-out;
        }

        .earnings-card {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(20px);
            border-radius: 20px;
            padding: 30px;
            border: 1px solid rgba(255, 255, 255, 0.2);
            animation: slideInRight 0.6s ease-out;
        }

        @keyframes slideInLeft {
            from { opacity: 0; transform: translateX(-30px); }
            to { opacity: 1; transform: translateX(0); }
        }

        @keyframes slideInRight {
            from { opacity: 0; transform: translateX(30px); }
            to { opacity: 1; transform: translateX(0); }
        }

        .card-title {
            font-size: 1.2em;
            margin-bottom: 15px;
            color: rgba(255, 255, 255, 0.8);
        }

        .balance-amount {
            font-size: 2.5em;
            font-weight: bold;
            color: #4CAF50;
            margin-bottom: 10px;
        }

        .earnings-amount {
            font-size: 1.8em;
            font-weight: bold;
            color: #FFC107;
            margin-bottom: 10px;
        }

        .investment-plans {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }

        .plan-card {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(20px);
            border-radius: 20px;
            padding: 25px;
            border: 1px solid rgba(255, 255, 255, 0.2);
            transition: all 0.3s ease;
            cursor: pointer;
            animation: fadeInUp 0.6s ease-out;
        }

        .plan-card:hover {
            transform: translateY(-5px);
            background: rgba(255, 255, 255, 0.15);
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
        }

        @keyframes fadeInUp {
            from { opacity: 0; transform: translateY(30px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .plan-name {
            font-size: 1.4em;
            font-weight: bold;
            margin-bottom: 10px;
            color: #4CAF50;
        }

        .plan-rate {
            font-size: 2em;
            font-weight: bold;
            color: #FFC107;
            margin-bottom: 10px;
        }

        .plan-details {
            color: rgba(255, 255, 255, 0.8);
            line-height: 1.6;
            margin-bottom: 20px;
        }

        .invest-btn {
            background: linear-gradient(45deg, #4CAF50, #45a049);
            color: white;
            border: none;
            padding: 12px 30px;
            border-radius: 50px;
            font-size: 1em;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            width: 100%;
            box-shadow: 0 4px 15px rgba(76, 175, 80, 0.3);
        }

        .invest-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(76, 175, 80, 0.4);
        }

        .investment-form {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(20px);
            border-radius: 20px;
            padding: 30px;
            border: 1px solid rgba(255, 255, 255, 0.2);
            margin-bottom: 30px;
            display: none;
            animation: slideIn 0.5s ease-out;
        }

        @keyframes slideIn {
            from { opacity: 0; transform: scale(0.9); }
            to { opacity: 1; transform: scale(1); }
        }

        .form-group {
            margin-bottom: 20px;
        }

        .form-group label {
            display: block;
            margin-bottom: 8px;
            color: rgba(255, 255, 255, 0.8);
            font-weight: 500;
        }

        .form-group input, .form-group select {
            width: 100%;
            padding: 12px 16px;
            border: 1px solid rgba(255, 255, 255, 0.3);
            border-radius: 10px;
            background: rgba(255, 255, 255, 0.1);
            color: white;
            font-size: 1em;
            transition: all 0.3s ease;
        }

        .form-group input:focus, .form-group select:focus {
            outline: none;
            border-color: #4CAF50;
            box-shadow: 0 0 0 3px rgba(76, 175, 80, 0.2);
        }

        .form-group input::placeholder {
            color: rgba(255, 255, 255, 0.5);
        }

        .form-actions {
            display: flex;
            gap: 15px;
        }

        .btn-primary {
            background: linear-gradient(45deg, #4CAF50, #45a049);
            color: white;
            border: none;
            padding: 12px 30px;
            border-radius: 50px;
            font-size: 1em;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            flex: 1;
        }

        .btn-secondary {
            background: rgba(255, 255, 255, 0.1);
            color: white;
            border: 1px solid rgba(255, 255, 255, 0.3);
            padding: 12px 30px;
            border-radius: 50px;
            font-size: 1em;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            flex: 1;
        }

        .btn-primary:hover, .btn-secondary:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(0, 0, 0, 0.2);
        }

        .active-investments {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(20px);
            border-radius: 20px;
            padding: 30px;
            border: 1px solid rgba(255, 255, 255, 0.2);
            margin-bottom: 30px;
        }

        .investment-item {
            background: rgba(255, 255, 255, 0.05);
            border-radius: 10px;
            padding: 20px;
            margin-bottom: 15px;
            border: 1px solid rgba(255, 255, 255, 0.1);
            transition: all 0.3s ease;
        }

        .investment-item:hover {
            background: rgba(255, 255, 255, 0.1);
        }

        .investment-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 10px;
        }

        .investment-plan {
            font-weight: bold;
            color: #4CAF50;
        }

        .investment-status {
            background: #4CAF50;
            color: white;
            padding: 4px 12px;
            border-radius: 20px;
            font-size: 0.9em;
        }

        .investment-details {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
            gap: 15px;
            color: rgba(255, 255, 255, 0.8);
        }

        .detail-item {
            text-align: center;
        }

        .detail-label {
            font-size: 0.9em;
            margin-bottom: 5px;
        }

        .detail-value {
            font-size: 1.2em;
            font-weight: bold;
            color: white;
        }

        .earnings-tracker {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(20px);
            border-radius: 20px;
            padding: 30px;
            border: 1px solid rgba(255, 255, 255, 0.2);
        }

        .tracker-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
        }

        .tracker-toggle {
            display: flex;
            gap: 10px;
        }

        .toggle-btn {
            background: rgba(255, 255, 255, 0.1);
            color: white;
            border: 1px solid rgba(255, 255, 255, 0.3);
            padding: 8px 16px;
            border-radius: 20px;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .toggle-btn.active {
            background: #4CAF50;
            border-color: #4CAF50;
        }

        .earnings-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
        }

        .earnings-stat {
            background: rgba(255, 255, 255, 0.05);
            border-radius: 10px;
            padding: 20px;
            text-align: center;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }

        .stat-value {
            font-size: 1.8em;
            font-weight: bold;
            color: #FFC107;
            margin-bottom: 5px;
        }

        .stat-label {
            color: rgba(255, 255, 255, 0.7);
        }

        @media (max-width: 768px) {
            .dashboard {
                grid-template-columns: 1fr;
            }
            
            .app-container {
                padding: 15px;
            }
            
            .header h1 {
                font-size: 2em;
            }
            
            .balance-amount {
                font-size: 2em;
            }
        }
    </style>
</head>
<body>
    <div id="loginScreen" class="login-container">
        <div class="login-card">
            <div class="login-header">
                <h1>✨ INVEST WITH LIGHT</h1>
                <p>Illuminating Your Financial Future</p>
            </div>
            
            <form class="login-form" id="loginForm">
                <input type="email" id="email" placeholder="📧 Email Address" required>
                <input type="password" id="password" placeholder="🔒 Password" required>
                <button type="submit" class="login-btn">🚀 Login</button>
            </form>
            
            <div class="login-toggle">
                <p>Don't have an account? <a href="#" onclick="toggleAuthMode()">Sign up here</a></p>
            </div>
        </div>
    </div>

    <div id="signupScreen" class="login-container" style="display: none;">
        <div class="login-card">
            <div class="login-header">
                <h1>✨ INVEST WITH LIGHT</h1>
                <p>Join the Light - Start Your Journey</p>
            </div>
            
            <form class="login-form" id="signupForm">
                <input type="text" id="fullName" placeholder="👤 Full Name" required>
                <input type="email" id="signupEmail" placeholder="📧 Email Address" required>
                <input type="password" id="signupPassword" placeholder="🔒 Password" required>
                <input type="password" id="confirmPassword" placeholder="🔒 Confirm Password" required>
                <button type="submit" class="login-btn">✨ Create Account</button>
            </form>
            
            <div class="login-toggle">
                <p>Already have an account? <a href="#" onclick="toggleAuthMode()">Login here</a></p>
            </div>
        </div>
    </div>

    <div id="mainApp" class="app-container" style="display: none;">
        <div class="header">
            <div class="auth-controls">
                <div class="user-info">
                    <div class="user-avatar">JD</div>
                    <span>John Doe</span>
                </div>
                <button class="logout-btn" onclick="logout()">🚪 Logout</button>
            </div>
            <h1>✨ INVEST WITH LIGHT</h1>
            <p>Illuminating Your Financial Future - Earn Daily & Monthly Returns</p>
        </div>

        <div class="dashboard">
            <div class="balance-card">
                <div class="card-title">💳 Account Balance</div>
                <div class="balance-amount" id="accountBalance">$5,000.00</div>
                <div style="color: rgba(255, 255, 255, 0.7);">Available for Investment</div>
            </div>
            
            <div class="earnings-card">
                <div class="card-title">📈 Total Earnings</div>
                <div class="earnings-amount" id="totalEarnings">$247.50</div>
                <div style="color: rgba(255, 255, 255, 0.7);">Today: +$12.30 | This Month: +$247.50</div>
            </div>
        </div>

        <div class="investment-plans">
            <div class="plan-card" onclick="showInvestmentForm('daily')">
                <div class="plan-name">🌅 Daily Earner</div>
                <div class="plan-rate">2.5%</div>
                <div class="plan-details">
                    • Daily interest payment<br>
                    • Minimum: $100<br>
                    • Maximum: $10,000<br>
                    • Flexible withdrawal
                </div>
                <button class="invest-btn">Invest Now</button>
            </div>
            
            <div class="plan-card" onclick="showInvestmentForm('weekly')">
                <div class="plan-name">📅 Weekly Pro</div>
                <div class="plan-rate">4.2%</div>
                <div class="plan-details">
                
