<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Booking Form</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f4f4f9;
      margin: 0;
      padding: 0;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
    }
    .container {
      background: #ffffff;
      padding: 20px;
      border-radius: 8px;
      box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
      max-width: 400px;
      width: 100%;
    }
    h1 {
      text-align: center;
      margin-bottom: 20px;
      color: #333;
    }
    form {
      display: flex;
      flex-direction: column;
    }
    label {
      margin-bottom: 5px;
      color: #555;
    }
    input, textarea, button {
      padding: 10px;
      margin-bottom: 15px;
      border: 1px solid #ddd;
      border-radius: 5px;
    }
    button {
      background-color: #007BFF;
      color: #fff;
      border: none;
      cursor: pointer;
    }
    button:hover {
      background-color: #0056b3;
    }
    .success-message {
      color: green;
      text-align: center;
    }
    .error-message {
      color: red;
      text-align: center;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>Booking Form</h1>
    <form id="bookingForm">
      <label for="name">Name:</label>
      <input type="text" id="name" name="name" required>
      
      <label for="email">Email:</label>
      <input type="email" id="email" name="email" required>
      
      <label for="phone">Phone Number:</label>
      <input type="tel" id="phone" name="phone" required>
      
      <label for="message">Message:</label>
      <textarea id="message" name="message" rows="4" required></textarea>
      
      <button type="submit">Submit</button>
      <p id="responseMessage" class="success-message"></p>
    </form>
  </div>

  <script>
    const form = document.getElementById('bookingForm');
    const responseMessage = document.getElementById('responseMessage');

    form.addEventListener('submit', async (event) => {
      event.preventDefault();
      responseMessage.textContent = '';

      const formData = {
        name: form.name.value,
        email: form.email.value,
        phone: form.phone.value,
        message: form.message.value,
      };

      try {
        const response = await fetch('https://script.google.com/macros/s/AKfycbxFUeX4vydcNG9ccPeWeh0zl6zvo91Sfk4a5RHAvRP_SQGzttoEkWn6jkzhJ-Pekkj9/exec', {
          method: 'POST',
          headers: {
            'Content-Type': 'application/json',
          },
          body: JSON.stringify(formData),
        });

        if (response.ok) {
          responseMessage.textContent = 'Booking submitted successfully!';
          form.reset();
        } else {
          throw new Error('Something went wrong.');
        }
      } catch (error) {
        responseMessage.textContent = 'Failed to submit booking. Please try again.';
      }
    });
  </script>
</body>
</html>
