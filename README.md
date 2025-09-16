<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Order Menu - Sai Restaurant</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 0;
      background-color: #fffaf0;
    }

    header {
      background-color: #c0392b;
      color: white;
      padding: 30px;
      text-align: center;
    }

    h1 {
      margin: 0;
    }

    form {
      max-width: 800px;
      margin: 40px auto;
      background-color: white;
      padding: 30px;
      border-radius: 10px;
      box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
    }

    .menu-item {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 15px 0;
      border-bottom: 1px solid #eee;
    }

    .menu-item:last-child {
      border-bottom: none;
    }

    label {
      font-weight: bold;
    }

    input[type="number"] {
      width: 60px;
      padding: 5px;
      font-size: 16px;
    }

    button {
      margin-top: 30px;
      padding: 12px 20px;
      background-color: #c0392b;
      color: white;
      border: none;
      border-radius: 5px;
      font-size: 16px;
      cursor: pointer;
    }

    button:hover {
      background-color: #a83224;
    }
  </style>
</head>
<body>

  <header>
    <h1>Order Your Favorite Food</h1>
    <p>Select quantity and place your order</p>
  </header>

  <form id="orderForm" onsubmit="sendToWhatsApp(event)">
    <!-- Starters -->
    <h2>Starters</h2>
    <div class="menu-item">
      <label for="spring-rolls">Veg Spring Rolls (₹120)</label>
      <input type="number" id="spring-rolls" name="Veg Spring Rolls" min="0" value="0">
    </div>
    <div class="menu-item">
      <label for="chicken-65">Chicken 65 (₹180)</label>
      <input type="number" id="chicken-65" name="Chicken 65" min="0" value="0">
    </div>

    <!-- Main Course -->
    <h2>Main Course</h2>
    <div class="menu-item">
      <label for="paneer">Paneer Butter Masala (₹200)</label>
      <input type="number" id="paneer" name="Paneer Butter Masala" min="0" value="0">
    </div>
    <div class="menu-item">
      <label for="biryani">Chicken Biryani (₹250)</label>
      <input type="number" id="biryani" name="Chicken Biryani" min="0" value="0">
    </div>

    <!-- Desserts -->
    <h2>Desserts</h2>
    <div class="menu-item">
      <label for="jamun">Gulab Jamun (₹80)</label>
      <input type="number" id="jamun" name="Gulab Jamun" min="0" value="0">
    </div>
    <div class="menu-item">
      <label for="ice-cream">Ice Cream (₹90)</label>
      <input type="number" id="ice-cream" name="Ice Cream" min="0" value="0">
    </div>

    <!-- Drinks -->
    <h2>Drinks</h2>
    <div class="menu-item">
      <label for="lassi">Lassi (₹60)</label>
      <input type="number" id="lassi" name="Lassi" min="0" value="0">
    </div>
    <div class="menu-item">
      <label for="coffee">Cold Coffee (₹100)</label>
      <input type="number" id="coffee" name="Cold Coffee" min="0" value="0">
    </div>

    <button type="submit">Place Order via WhatsApp</button>
  </form>

  <script>
    function sendToWhatsApp(event) {
      event.preventDefault(); // Prevent form from submitting

      const phoneNumber = "917845068370"; // WhatsApp number (without +)
      const form = document.getElementById("orderForm");
      const inputs = form.querySelectorAll("input[type='number']");

      let message = "🛒 *New Order from Sai Restaurant*\n\n";

      inputs.forEach(input => {
        const item = input.name;
        const quantity = input.value;
        if (quantity > 0) {
          message += `🍽️ ${item}: ${quantity}\n`;
        }
      });

      if (message === "🛒 *New Order from Sai Restaurant*\n\n") {
        alert("Please select at least one item.");
        return;
      }

      const encodedMessage = encodeURIComponent(message);
      const whatsappURL = `https://wa.me/${phoneNumber}?text=${encodedMessage}`;

      window.open(whatsappURL, "_blank");
    }
  </script>

</body>
</html>
