<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Blood Donor Registration</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Arial', sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            padding: 20px;
        }

        .donor-form-container {
            max-width: 800px;
            margin: 40px auto;
            padding: 30px;
            background: #ffffff;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
        }

        h2 {
            text-align: center;
            color: #e74c3c;
            margin-bottom: 30px;
            font-size: 2em;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.1);
        }

        .form-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 20px;
            margin-bottom: 20px;
        }

        .form-group {
            margin-bottom: 15px;
        }

        label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            color: #333;
        }

        input, select {
            width: 100%;
            padding: 12px;
            border: 2px solid #ddd;
            border-radius: 8px;
            font-size: 1em;
            transition: border-color 0.3s ease;
        }

        input:focus, select:focus {
            outline: none;
            border-color: #e74c3c;
            box-shadow: 0 0 0 3px rgba(231, 76, 60, 0.1);
        }

        .cta-button {
            background: linear-gradient(135deg, #e74c3c 0%, #c0392b 100%);
            color: white;
            padding: 15px 30px;
            border: none;
            border-radius: 8px;
            font-size: 1.1em;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(231, 76, 60, 0.3);
        }

        .cta-button:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(231, 76, 60, 0.4);
        }

        .checkbox-group {
            display: flex;
            align-items: center;
            margin-bottom: 25px;
        }

        .checkbox-group input[type="checkbox"] {
            width: auto;
            margin-right: 10px;
        }

        .success-message {
            background: #d4edda;
            color: #155724;
            padding: 15px;
            border-radius: 8px;
            margin-bottom: 20px;
            border: 1px solid #c3e6cb;
            display: none;
        }

        .error-message {
            background: #f8d7da;
            color: #721c24;
            padding: 15px;
            border-radius: 8px;
            margin-bottom: 20px;
            border: 1px solid #f5c6cb;
            display: none;
        }

        .loading {
            display: none;
            text-align: center;
            color: #666;
        }

        @media (max-width: 768px) {
            .form-grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <div class="donor-form-container">
        <h2><i class="fas fa-heart"></i> Become a Blood Donor</h2>
        
        <div class="success-message" id="successMessage">
            <i class="fas fa-check-circle"></i> Registration successful! Thank you for becoming a blood donor.
        </div>
        
        <div class="error-message" id="errorMessage">
            <i class="fas fa-exclamation-triangle"></i> There was an error submitting your registration. Please try again.
        </div>
        
        <div class="loading" id="loadingMessage">
            <i class="fas fa-spinner fa-spin"></i> Submitting your registration...
        </div>
        
        <form id="donorRegistrationForm">
            <div class="form-grid">
                <div class="form-group">
                    <label for="fullName">Full Name*</label>
                    <input type="text" id="fullName" name="fullName" required>
                </div>
                
                <div class="form-group">
                    <label for="age">Age*</label>
                    <input type="number" id="age" name="age" min="18" max="65" required>
                </div>
            </div>
            
            <div class="form-grid">
                <div class="form-group">
                    <label for="bloodGroup">Blood Group*</label>
                    <select id="bloodGroup" name="bloodGroup" required>
                        <option value="">Select Blood Group</option>
                        <option value="A+">A+</option>
                        <option value="A-">A-</option>
                        <option value="B+">B+</option>
                        <option value="B-">B-</option>
                        <option value="AB+">AB+</option>
                        <option value="AB-">AB-</option>
                        <option value="O+">O+</option>
                        <option value="O-">O-</option>
                    </select>
                </div>
                
                <div class="form-group">
                    <label for="dob">Date of Birth*</label>
                    <input type="date" id="dob" name="dob" required>
                </div>
            </div>
            
            <div class="form-grid">
                <div class="form-group">
                    <label for="city">City*</label>
                    <input type="text" id="city" name="city" required>
                </div>
                
                <div class="form-group">
                    <label for="state">State*</label>
                    <select id="state" name="state" required>
                        <option value="">Select State</option>
                        <option value="Tamil Nadu">Tamil Nadu</option>
                        <option value="Kerala">Kerala</option>
                        <option value="Karnataka">Karnataka</option>
                        <option value="Andhra Pradesh">Andhra Pradesh</option>
                        <option value="Telangana">Telangana</option>
                        <option value="Maharashtra">Maharashtra</option>
                        <option value="Gujarat">Gujarat</option>
                        <option value="Rajasthan">Rajasthan</option>
                        <option value="Uttar Pradesh">Uttar Pradesh</option>
                        <option value="Madhya Pradesh">Madhya Pradesh</option>
                        <option value="Bihar">Bihar</option>
                        <option value="West Bengal">West Bengal</option>
                        <option value="Odisha">Odisha</option>
                        <option value="Assam">Assam</option>
                        <option value="Punjab">Punjab</option>
                        <option value="Haryana">Haryana</option>
                        <option value="Himachal Pradesh">Himachal Pradesh</option>
                        <option value="Uttarakhand">Uttarakhand</option>
                        <option value="Jharkhand">Jharkhand</option>
                        <option value="Chhattisgarh">Chhattisgarh</option>
                        <option value="Goa">Goa</option>
                        <option value="Delhi">Delhi</option>
                    </select>
                </div>
            </div>
            
            <div class="form-group">
                <label for="phone">Phone Number*</label>
                <input type="tel" id="phone" name="phone" required pattern="[0-9]{10}">
            </div>
            
            <div class="form-group">
                <label for="email">Email</label>
                <input type="email" id="email" name="email">
            </div>
            
            <div class="checkbox-group">
                <input type="checkbox" id="consent" name="consent" required>
                <label for="consent">I agree to be contacted when my blood type is needed*</label>
            </div>
            
            <div style="text-align: center;">
                <button type="submit" class="cta-button">
                    <i class="fas fa-tint"></i> Register as Donor
                </button>
            </div>
        </form>
    </div>

    <script>
        // Replace this URL with your Google Apps Script Web App URL
        const GOOGLE_SCRIPT_URL = 'https://script.google.com/macros/s/AKfycbzq5-jSPcfZ8HoOOOM3sEAtIogZz8iZR8-51ryuND3DGMUqSOGmdc3BOAh6chttGAVsAA/exec';
        
        document.getElementById('donorRegistrationForm').addEventListener('submit', async function(e) {
            e.preventDefault();
            
            const formData = new FormData(this);
            const data = Object.fromEntries(formData.entries());
            
            // Add timestamp
            data.timestamp = new Date().toISOString();
            
            // Show loading
            document.getElementById('loadingMessage').style.display = 'block';
            document.getElementById('successMessage').style.display = 'none';
            document.getElementById('errorMessage').style.display = 'none';
            
            try {
                console.log('Sending data:', data);
                console.log('To URL:', GOOGLE_SCRIPT_URL);
                
                const response = await fetch(GOOGLE_SCRIPT_URL, {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json',
                    },
                    body: JSON.stringify(data),
                    mode: 'no-cors' // This is important for Google Apps Script
                });
                
                // Since we're using no-cors mode, we can't check response.ok
                // We'll assume success if no error is thrown
                document.getElementById('successMessage').style.display = 'block';
                this.reset();
                
            } catch (error) {
                console.error('Error details:', error);
                document.getElementById('errorMessage').style.display = 'block';
                
                // Show more detailed error information
                const errorDiv = document.getElementById('errorMessage');
                errorDiv.innerHTML = `
                    <i class="fas fa-exclamation-triangle"></i> 
                    Error: ${error.message}<br>
                    Please check your Google Apps Script setup and try again.
                `;
            } finally {
                document.getElementById('loadingMessage').style.display = 'none';
            }
        });
        
        // Alternative method using Google Forms (simpler setup)
        function submitToGoogleForm() {
            const form = document.getElementById('donorRegistrationForm');
            const formData = new FormData(form);
            
            // Replace with your Google Form URL
            const GOOGLE_SCRIPT_URL = 'https://script.google.com/macros/s/AKfycbzq5-jSPcfZ8HoOOOM3sEAtIogZz8iZR8-51ryuND3DGMUqSOGmdc3BOAh6chttGAVsAA/exec';
            
            // Create hidden iframe for form submission
            const iframe = document.createElement('iframe');
            iframe.name = 'hidden_iframe';
            iframe.style.display = 'none';
            document.body.appendChild(iframe);
            
            form.target = 'hidden_iframe';
            form.action = googleFormUrl;
            form.method = 'POST';
            
            // Change input names to match Google Form entry IDs
            // You'll need to inspect your Google Form to get these entry IDs
            document.getElementById('fullName').name = 'entry.XXXXXXXXX';
            document.getElementById('age').name = 'entry.XXXXXXXXX';
            // ... continue for all fields
            
            form.submit();
        }
    </script>
</body>
</html>"
