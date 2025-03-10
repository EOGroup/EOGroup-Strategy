<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>EO Group Strategy Course 2025</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background: url('https://source.unsplash.com/1600x900/?trading,ai,robot') no-repeat center center fixed;
            background-size: cover;
            color: white;
            text-align: center;
            padding: 50px;
        }
        .container {
            background: rgba(0, 0, 0, 0.8);
            padding: 20px;
            border-radius: 10px;
            width: 50%;
            margin: auto;
        }
        input, select, button {
            display: block;
            width: 80%;
            margin: 10px auto;
            padding: 10px;
            font-size: 16px;
        }
        button {
            background: green;
            color: white;
            border: none;
            cursor: pointer;
        }
        button:hover {
            background: darkgreen;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>EO Group Strategy Course 2025</h1>
        <p>Fill in the details below to complete your registration.</p>
        <form id="registrationForm" enctype="multipart/form-data">
            <input type="text" id="name" placeholder="Full Name" required>
            <input type="email" id="email" placeholder="Email" required>
            <input type="text" id="phone" placeholder="Phone Number" required>
            
            <label for="country">Select Country:</label>
            <select id="country" required>
                <option value="">Select your country</option>
                <option value="Saudi Arabia">Saudi Arabia</option>
                <option value="UAE">UAE</option>
                <option value="Qatar">Qatar</option>
                <option value="Pakistan">Pakistan</option>
                <option value="India">India</option>
                <option value="Sri Lanka">Sri Lanka</option>
                <option value="USA">USA</option>
                <option value="UK">UK</option>
            </select>

            <input type="text" id="transactionId" placeholder="Transaction ID" required>
            <input type="number" id="paidAmount" placeholder="Paid Amount (USD)" required>

            <label for="paymentProof">Upload Payment Proof (Screenshot):</label>
            <input type="file" id="paymentProof" accept="image/*" required>
            <label for="idFront">Upload Identity Document (Front Side):</label>
            <input type="file" id="idFront" accept="image/*" required>
            <label for="idBack">Upload Identity Document (Back Side):</label>
            <input type="file" id="idBack" accept="image/*" required>
            <button type="submit">Register</button>
        </form>
        <p id="confirmationMessage" style="display: none; color: yellow;">Verification takes up to 10 days. You will receive access once it is completed.</p>

        <!-- Register Button with Google Form Link -->
        <a href="https://docs.google.com/forms/d/e/1FAIpQLSeZdrqNuSeX0LlFUeZ2qRCnpMn06ONcyneyyMK1gDriT_u3iw/viewform?usp=dialog" target="_blank">
            <button style="background: blue; padding: 10px 20px; font-size: 16px;">Register Now</button>
        </a>
    </div>

    <script>
        document.getElementById("registrationForm").addEventListener("submit", function(event) {
            event.preventDefault();
            document.getElementById("confirmationMessage").style.display = "block";
        });
    </script>
</body>
</html>
