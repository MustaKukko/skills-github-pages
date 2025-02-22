<html>
<head>
  <title>Get Discount Code</title>
</head>
<body>
  <h2>Request Your Discount Code</h2>
  <form id="discountForm">
    <label>Email:</label><br />
    <input type="email" id="email" required /><br />
    <label>Membership Number:</label><br />
    <input type="text" id="membershipNumber" required /><br /><br />
    <button type="submit">Get Code</button>
  </form>
  <p id="result"></p>

  <script>
    document.getElementById("discountForm").addEventListener("submit", async function(e) {
      e.preventDefault();
      const email = document.getElementById("email").value;
      const membershipNumber = document.getElementById("membershipNumber").value;
      const response = await fetch("https://script.google.com/macros/s/AKfycbx0aVjFpstK12xbEko3Lf_8LIhJnBlS5hwryRibpzBr38RApb7g6hlhtv3AlaAZUeg8xQ/exec", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({ email, membershipNumber })
      });
      const result = await response.json();
      document.getElementById("result").innerText = result.discount_code
        ? `Your discount code: ${result.discount_code}`
        : `Error: ${result.error}`;
    });
  </script>
</body>
</html>
