# formjavascript

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Feedback Form</title>
  <style>
    body {
      background: linear-gradient(135deg, #667eea, #764ba2);
      height: 100vh;
      margin: 0;
      display: flex;
      justify-content: center;
      align-items: center;
      font-family: sans-serif;
    }
    .form-container {
      background: #fff;
      padding: 30px;
      border-radius: 10px;
      width: 400px;
      box-shadow: 0 0 10px rgba(0,0,0,0.3);
    }
    .form-container h2 {
      text-align: center;
      margin-bottom: 20px;
    }
    .form-group {
      margin-bottom: 15px;
    }
    .form-group label {
      display: block;
      margin-bottom: 5px;
      font-weight: bold;
    }
    .form-group input,
    .form-group select,
    .form-group textarea {
      width: 100%;
      padding: 10px;
      border: 1px solid #ccc;
      border-radius: 5px;
      font-size: 14px;
    }
    .form-group button {
      width: 100%;
      background: #667eea;
      color: #fff;
      padding: 10px;
      border: none;
      border-radius: 5px;
      font-weight: bold;
      font-size: 16px;
      cursor: pointer;
    }
    .error {
      color: red;
      font-size: 13px;
      margin-top: 5px;
      display: none;
    }
    .success-message {
      color: green;
      text-align: center;
      margin-top: 15px;
      font-weight: bold;
    }
  </style>
</head>
<body>
  <div class="form-container">
    <h2>Feedback Form</h2>
    <form id="feedbackForm">
      <div class="form-group">
        <label for="name">Name *</label>
        <input type="text" id="name" name="name">
        <div class="error" id="nameError">This field is required.</div>
      </div>

      <div class="form-group">
        <label for="gender">Gender *</label>
        <select id="gender" name="gender">
          <option value="">Select Gender</option>
          <option value="Male">Male</option>
          <option value="Female">Female</option>
          <option value="Other">Other</option>
        </select>
        <div class="error" id="genderError">This field is required.</div>
      </div>

      <div class="form-group">
        <label for="age">Age *</label>
        <input type="number" id="age" name="age">
        <div class="error" id="ageError">This field is required.</div>
      </div>

      <div class="form-group">
        <label for="number">Phone Number *</label>
        <input type="text" id="number" name="number">
        <div class="error" id="numberError">This field is required.</div>
      </div>

      <div class="form-group">
        <label for="email">Email *</label>
        <input type="email" id="email" name="email">
        <div class="error" id="emailError">This field is required.</div>
      </div>

      <div class="form-group">
        <label for="city">City *</label>
        <select id="city" name="city">
          <option value="">Select City</option>
          <option value="Karachi, Pakistan">Karachi</option>
          <option value="Lahore, Pakistan">Lahore</option>
          <option value="New York, USA">New York</option>
          <option value="London, UK">London</option>
          <option value="Tokyo, Japan">Tokyo</option>
        </select>
        <div class="error" id="cityError">This field is required.</div>
      </div>

      <div class="form-group">
        <label for="feedback">Feedback *</label>
        <textarea id="feedback" name="feedback"></textarea>
        <div class="error" id="feedbackError">This field is required.</div>
      </div>

      <div class="form-group">
        <button type="submit">Submit</button>
      </div>

      <div class="success-message" id="successMessage"></div>
    </form>
  </div>

  <script>
    document.getElementById("feedbackForm").addEventListener("submit", function(e) {
      e.preventDefault();

      let hasError = false;

      const fields = [
        "name",
        "gender",
        "age",
        "number",
        "email",
        "city",
        "feedback"
      ];

      // Hide all errors first
      fields.forEach(field => {
        document.getElementById(field + "Error").style.display = "none";
      });

      fields.forEach(field => {
        const value = document.getElementById(field).value.trim();
        if (value === "") {
          document.getElementById(field + "Error").style.display = "block";
          hasError = true;
        }
      });

      if (!hasError) {
        document.getElementById("successMessage").textContent = "✅ Thank you! Your feedback has been submitted.";
        this.reset();
      } else {
        document.getElementById("successMessage").textContent = "";
      }
    });
  </script>
</body>
</html>
