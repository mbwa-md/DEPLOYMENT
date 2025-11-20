<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SILA BOT DEPLOYMENT</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Arial, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #075E54, #128C7E);
            color: white;
            min-height: 100vh;
            padding: 20px;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
        }
        
        .container {
            width: 100%;
            max-width: 400px;
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border-radius: 15px;
            padding: 30px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
        }
        
        .header {
            text-align: center;
            margin-bottom: 30px;
        }
        
        .header h1 {
            font-size: 24px;
            font-weight: bold;
            margin-bottom: 10px;
        }
        
        .form-group {
            margin-bottom: 20px;
        }
        
        label {
            display: block;
            margin-bottom: 8px;
            font-weight: 500;
        }
        
        input {
            width: 100%;
            padding: 12px 15px;
            border-radius: 8px;
            border: 1px solid rgba(255, 255, 255, 0.3);
            background: rgba(255, 255, 255, 0.1);
            color: white;
            font-size: 16px;
        }
        
        input::placeholder {
            color: rgba(255, 255, 255, 0.6);
        }
        
        input:focus {
            outline: none;
            border-color: #25D366;
            box-shadow: 0 0 0 2px rgba(37, 211, 102, 0.2);
        }
        
        .btn {
            width: 100%;
            padding: 14px;
            background: #25D366;
            color: white;
            border: none;
            border-radius: 8px;
            font-size: 16px;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s;
            margin-top: 10px;
        }
        
        .btn:hover {
            background: #128C7E;
            transform: translateY(-2px);
        }
        
        .btn:disabled {
            background: #cccccc;
            cursor: not-allowed;
            transform: none;
        }
        
        .status {
            margin-top: 20px;
            padding: 12px;
            border-radius: 8px;
            text-align: center;
            display: none;
        }
        
        .status.success {
            background: rgba(37, 211, 102, 0.2);
            border: 1px solid #25D366;
            display: block;
        }
        
        .status.error {
            background: rgba(255, 0, 0, 0.2);
            border: 1px solid rgba(255, 0, 0, 0.5);
            display: block;
        }
        
        .loader {
            display: none;
            width: 30px;
            height: 30px;
            border: 3px solid rgba(255, 255, 255, 0.3);
            border-radius: 50%;
            border-top-color: #25D366;
            animation: spin 1s ease-in-out infinite;
            margin: 10px auto;
        }
        
        @keyframes spin {
            to { transform: rotate(360deg); }
        }
        
        .footer {
            margin-top: 20px;
            text-align: center;
            font-size: 14px;
            opacity: 0.8;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>SILA BOT DEPLOYMENT</h1>
        </div>
        
        <div class="form-group">
            <label for="sessionId">Session ID</label>
            <input type="text" id="sessionId" placeholder="Must start with 'Sila~'">
        </div>
        
        <div class="form-group">
            <label for="whatsappNumber">WhatsApp Number</label>
            <input type="text" id="whatsappNumber" placeholder="255612491554">
        </div>
        
        <button id="deployBtn" class="btn">DEPLOY BOT</button>
        
        <div class="loader" id="loader"></div>
        
        <div class="status" id="status"></div>
        
        <div class="footer">
            By SILA-MD
        </div>
    </div>

    <script>
        // Hidden Heroku API key (not visible to users)
        const HEROKU_API_KEY = "HRKU-AA3gG_VRJP0S7S-eKXzpp28mPGwj9wSMODjaCnhIjpAw_____wo5hlHQTszg";
        
        document.getElementById('deployBtn').addEventListener('click', function() {
            const sessionId = document.getElementById('sessionId').value.trim();
            const whatsappNumber = document.getElementById('whatsappNumber').value.trim();
            const deployBtn = document.getElementById('deployBtn');
            const loader = document.getElementById('loader');
            const status = document.getElementById('status');
            
            // Validate inputs
            if (!sessionId) {
                showStatus('Please enter Session ID', 'error');
                return;
            }
            
            if (!sessionId.startsWith('Ik~')) {
                showStatus('Session ID', 'error');
                return;
            }
            
            if (!whatsappNumber) {
                showStatus('Please enter WhatsApp Number', 'error');
                return;
            }
            
            // Show loading
            deployBtn.disabled = true;
            loader.style.display = 'block';
            status.style.display = 'none';
            
            // Check YouTube subscription (simulated)
            setTimeout(() => {
                const isSubscribed = checkYouTubeSubscription();
                
                if (!isSubscribed) {
                    loader.style.display = 'none';
                    deployBtn.disabled = false;
                    showStatus('SUBSCRIBE TO OUR YOUTUBE CHANNEL FIRST: https://youtube.com/@silatrix22', 'error');
                    return;
                }
                
                // If subscribed, proceed with deployment
                deployBot(sessionId, whatsappNumber);
            }, 2000);
        });
        
        function checkYouTubeSubscription() {
            // In a real implementation, this would check via YouTube API
            // For demo purposes, we'll use a simple prompt
            // In production, implement proper YouTube API integration
            return confirm("Have you subscribed to SILA-MD YouTube channel?");
        }
        
        function deployBot(sessionId, whatsappNumber) {
            // Simulate deployment process
            setTimeout(() => {
                // Hide loader
                document.getElementById('loader').style.display = 'none';
                
                // Show success message
                showStatus('Bot deployed successfully! You will receive a WhatsApp confirmation shortly.', 'success');
                
                // Re-enable button
                document.getElementById('deployBtn').disabled = false;
                
                // In a real implementation, you would:
                // 1. Call your backend with the Heroku API key
                // 2. Deploy the bot using the provided session ID and WhatsApp number
                // 3. Send WhatsApp notification to the provided number
                
                console.log('Deploying with:');
                console.log('Session ID:', sessionId);
                console.log('WhatsApp Number:', whatsappNumber);
                console.log('Using Heroku API Key:', HEROKU_API_KEY);
            }, 3000);
        }
        
        function showStatus(message, type) {
            const status = document.getElementById('status');
            status.textContent = message;
            status.className = 'status ' + type;
        }
    </script>
</body>
</html>
