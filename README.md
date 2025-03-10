
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
                <option value="Afghanistan">Afghanistan</option>
                <option value="Albania">Albania</option>
                <option value="Algeria">Algeria</option>
                <option value="Andorra">Andorra</option>
                <option value="Angola">Angola</option>
                <option value="Argentina">Argentina</option>
                <option value="Armenia">Armenia</option>
                <option value="Australia">Australia</option>
                <option value="Austria">Austria</option>
                <option value="Azerbaijan">Azerbaijan</option>
                <option value="Bahrain">Bahrain</option>
                <option value="Bangladesh">Bangladesh</option>
                <option value="Belarus">Belarus</option>
                <option value="Belgium">Belgium</option>
                <option value="Brazil">Brazil</option>
                <option value="Canada">Canada</option>
                <option value="China">China</option>
                <option value="Colombia">Colombia</option>
                <option value="Egypt">Egypt</option>
                <option value="France">France</option>
                <option value="Germany">Germany</option>
                <option value="India">India</option>
                <option value="Indonesia">Indonesia</option>
                <option value="Iran">Iran</option>
                <option value="Iraq">Iraq</option>
                <option value="Italy">Italy</option>
                <option value="Japan">Japan</option>
                <option value="Jordan">Jordan</option>
                <option value="Kuwait">Kuwait</option>
                <option value="Lebanon">Lebanon</option>
                <option value="Malaysia">Malaysia</option>
                <option value="Mexico">Mexico</option>
                <option value="Netherlands">Netherlands</option>
                <option value="Nigeria">Nigeria</option>
                <option value="Oman">Oman</option>
                <option value="Pakistan">Pakistan</option>
                <option value="Philippines">Philippines</option>
                <option value="Qatar">Qatar</option>
                <option value="Russia">Russia</option>
                <option value="Saudi Arabia">Saudi Arabia</option>
                <option value="South Africa">South Africa</option>
                <option value="Spain">Spain</option>
                <option value="Sri Lanka">Sri Lanka</option>
                <option value="Sweden">Sweden</option>
                <option value="Switzerland">Switzerland</option>
                <option value="Thailand">Thailand</option>
                <option value="Turkey">Turkey</option>
                <option value="UAE">UAE</option>
                <option value="UK">UK</option>
                <option value="USA">USA</option>
                <option value="Vietnam">Vietnam</option>
                <option value="Yemen">Yemen</option>
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
    </div>

    <script>
        document.getElementById("registrationForm").addEventListener("submit", function(event) {
            event.preventDefault();
            document.getElementById("confirmationMessage").style.display = "block";
        });
    </script>
</body>
</html>

<script>
document.getElementById("registrationForm").addEventListener("submit", async function(event) {
    event.preventDefault();

    // User Input Data
    const name = document.getElementById("name").value;
    const email = document.getElementById("email").value;
    const phone = document.getElementById("phone").value;
    const transactionId = document.getElementById("transactionId").value;
    const paidAmount = document.getElementById("paidAmount").value;
    
    const paymentProof = document.getElementById("paymentProof").files[0];

    // Convert Image to Base64
    const reader = new FileReader();
    reader.readAsDataURL(paymentProof);
    reader.onload = async function () {
        const imageData = reader.result;

        // Fetch Existing JSON Data
        const response = await fetch('https://raw.githubusercontent.com/EOGGroup/EOGroup-Strategy/main/data.json');
        let existingData = await response.json();

        // Add New Data
        const newData = { name, email, phone, transactionId, paidAmount, imageData };
        existingData.push(newData);

        // Convert Data to JSON String
        const updatedJSON = JSON.stringify(existingData, null, 2);

        // GitHub API URL
        const repo = "EOGGroup/EOGroup-Strategy";
        const filePath = "data.json";

        // Get SHA (GitHub File Versioning)
        const shaResponse = await fetch(`https://api.github.com/repos/${repo}/contents/${filePath}`);
        const shaData = await shaResponse.json();
        const fileSHA = shaData.sha;

        // Push Updated JSON File to GitHub
        await fetch(`https://api.github.com/repos/${repo}/contents/${filePath}`, {
            method: "PUT",
            headers: {
                "Authorization": `token ${process.env.EO_GROUP_TOKEN}`,  // Use GitHub Secret
                "Accept": "application/vnd.github.v3+json"
            },
            body: JSON.stringify({
                message: "Updated User Data",
                content: btoa(unescape(encodeURIComponent(updatedJSON))), // Convert to Base64
                sha: fileSHA
            })
        });

        alert("✅ Registration Successful! Data Stored.");
    };
});
</script>

