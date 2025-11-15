<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>WhatsApp Clone</title>
    <style>
        body { font-family: Arial, sans-serif; margin: 0; padding: 0; background-color: #f0f0f0; }
        .container { max-width: 400px; margin: 0 auto; background-color: white; height: 100vh; display: flex; flex-direction: column; }
        .header { background-color: #075e54; color: white; padding: 10px; text-align: center; }
        .chat-area { flex: 1; padding: 10px; overflow-y: auto; }
        .message { margin-bottom: 10px; }
        .message.sent { text-align: right; }
        .message.received { text-align: left; }
        .bubble { display: inline-block; padding: 8px 12px; border-radius: 10px; max-width: 70%; }
        .bubble.sent { background-color: #dcf8c6; }
        .bubble.received { background-color: #ffffff; border: 1px solid #ddd; }
        .input-area { display: flex; padding: 10px; border-top: 1px solid #ddd; }
        .input-area input { flex: 1; padding: 8px; border: none; outline: none; }
        .input-area button { padding: 8px 12px; background-color: #075e54; color: white; border: none; cursor: pointer; }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h2>Chat with Friend</h2>
        </div>
        <div class="chat-area" id="chatArea">
            <!-- Sample messages -->
            <div class="message received">
                <div class="bubble">Hey, how are you?</div>
            </div>
            <div class="message sent">
                <div class="bubble">I'm good, thanks! How about you?</div>
            </div>
        </div>
        <div class="input-area">
            <input type="text" id="messageInput" placeholder="Type a message...">
            <button onclick="sendMessage()">Send</button>
        </div>
    </div>

    <script>
        function sendMessage() {
            const input = document.getElementById('messageInput');
            const chatArea = document.getElementById('chatArea');
            if (input.value.trim() !== '') {
                const messageDiv = document.createElement('div');
                messageDiv.className = 'message sent';
                messageDiv.innerHTML = `<div class="bubble">${input.value}</div>`;
                chatArea.appendChild(messageDiv);
                input.value = '';
                chatArea.scrollTop = chatArea.scrollHeight; // Auto-scroll
            }
        }
        // Allow sending on Enter key
        document.getElementById('messageInput').addEventListener('keypress', function(e) {
            if (e.key === 'Enter') sendMessage();
        });
    </script>
</body>
</html>
