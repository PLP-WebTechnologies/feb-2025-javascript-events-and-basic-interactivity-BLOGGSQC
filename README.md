# feb-2025-avasjcript-events-and-basic-interactivity
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Interactive Feedback Form</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      padding: 2rem;
      background: #f5f5f5;
    }
    form {
      background: #fff;
      padding: 1.5rem;
      border-radius: 8px;
      max-width: 400px;
      margin: auto;
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
    }
    input, textarea, button {
      width: 100%;
      margin-top: 0.5rem;
      margin-bottom: 1rem;
      padding: 0.6rem;
      font-size: 1rem;
    }
    #charCount {
      font-size: 0.9rem;
      color: #555;
      text-align: right;
    }
    #helpSection {
      display: none;
      background: #e0f7fa;
      padding: 1rem;
      margin: 1rem auto;
      border-left: 4px solid #00acc1;
      max-width: 400px;
    }
    .success {
      color: green;
      font-weight: bold;
    }
  </style>
</head>
<body>

  <h2>Feedback Form</h2>

  <form id="feedbackForm">
    <label for="name">Name:</label>
    <input type="text" id="name" required>

    <label for="email">Email:</label>
    <input type="email" id="email" required>

    <label for="message">Message:</label>
    <textarea id="message" rows="5" maxlength="200" required></textarea>
    <div id="charCount">0 / 200</div>

    <button type="submit">Submit</button>
    <p id="responseMessage" class="success"></p>
  </form>

  <button id="toggleHelp">Toggle Help Section</button>
  <div id="helpSection">
    <p>Fill in your full name, a valid email, and your message. The message should be within 200 characters.</p>
  </div>

  <script>
    // Character counter
    const messageInput = document.getElementById('message');
    const charCount = document.getElementById('charCount');
    messageInput.addEventListener('input', () => {
      charCount.textContent = `${messageInput.value.length} / 200`;
    });

    // Toggle help section
    document.getElementById('toggleHelp').addEventListener('click', () => {
      const helpSection = document.getElementById('helpSection');
      helpSection.style.display = helpSection.style.display === 'none' ? 'block' : 'none';
    });

    // Form validation and submission
    document.getElementById('feedbackForm').addEventListener('submit', (e) => {
      e.preventDefault(); // Prevent page reload

      const name = document.getElementById('name').value.trim();
      const email = document.getElementById('email').value.trim();
      const message = messageInput.value.trim();
      const response = document.getElementById('responseMessage');

      if (!name || !email || !message) {
        alert('Please fill in all fields.');
        return;
      }

      if (!/^\S+@\S+\.\S+$/.test(email)) {
        alert('Please enter a valid email address.');
        return;
      }

      response.textContent = 'Thank you for your feedback!';
      document.getElementById('feedbackForm').reset();
      charCount.textContent = '0 / 200';
    });
  </script>
</body>
</html>
