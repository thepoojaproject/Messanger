<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>WhatsApp Web Clone</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Helvetica, Arial, sans-serif;
        }

        body {
            background-color: #111b21;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            color: #e9edef;
        }

        .whatsapp-container {
            width: 90%;
            max-width: 1600px;
            height: 95vh;
            background-color: #222e35;
            display: flex;
            border-radius: 8px;
            overflow: hidden;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
        }

        /* Sidebar Styles */
        .sidebar {
            width: 30%;
            background-color: #111b21;
            border-right: 1px solid #2a3942;
            display: flex;
            flex-direction: column;
            transition: all 0.3s ease;
        }

        .sidebar-header {
            padding: 10px 16px;
            background-color: #202c33;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .user-profile {
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .avatar {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background-color: #6a7175;
            display: flex;
            align-items: center;
            justify-content: center;
            overflow: hidden;
            cursor: pointer;
        }

        .avatar img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .user-name {
            font-size: 16px;
            font-weight: 500;
        }

        .sidebar-icons {
            display: flex;
            gap: 20px;
            color: #aebac1;
        }

        .sidebar-icons i {
            cursor: pointer;
            font-size: 18px;
            transition: color 0.2s;
        }

        .sidebar-icons i:hover {
            color: #e9edef;
        }

        .search-container {
            padding: 8px 12px;
            background-color: #202c33;
        }

        .search-box {
            background-color: #202c33;
            border-radius: 8px;
            padding: 8px 12px;
            display: flex;
            align-items: center;
            gap: 10px;
            border: 1px solid #2a3942;
        }

        .search-box i {
            color: #8696a0;
        }

        .search-box input {
            background-color: transparent;
            border: none;
            outline: none;
            color: #d1d7db;
            width: 100%;
            font-size: 14px;
        }

        .chats-list {
            flex: 1;
            overflow-y: auto;
        }

        .chat-item {
            display: flex;
            padding: 12px 16px;
            gap: 15px;
            cursor: pointer;
            border-bottom: 1px solid #222d34;
            transition: background-color 0.2s;
        }

        .chat-item.active, .chat-item:hover {
            background-color: #1f2c33;
        }

        .chat-info {
            flex: 1;
            display: flex;
            flex-direction: column;
            justify-content: center;
            gap: 5px;
        }

        .chat-name-time {
            display: flex;
            justify-content: space-between;
        }

        .chat-name {
            font-size: 16px;
            font-weight: 500;
        }

        .chat-time {
            font-size: 12px;
            color: #8696a0;
        }

        .chat-last-message {
            font-size: 14px;
            color: #8696a0;
            display: flex;
            align-items: center;
            gap: 5px;
        }

        .chat-last-message i {
            color: #53bdeb;
        }

        /* Main Chat Area */
        .chat-area {
            flex: 1;
            display: flex;
            flex-direction: column;
            background-image: url('data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iNDAiIGhlaWdodD0iNDAiIHZpZXdCb3g9IjAgMCA0MCA0MCIgZmlsbD0ibm9uZSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KPHBhdGggZD0iTTIwIDM4QzI5Ljk0MTEgMzggMzggMjkuOTQxMSAzOCAyMEMzOCAxMC4wNTg5IDI5Ljk0MTEgMiAyMCAyQzEwLjA1ODkgMiAyIDEwLjA1ODkgMiAyMEMyIDI5Ljk0MTEgMTAuMDU4OSAzOCAyMCAzOFoiIHN0cm9rZT0iIzJhMzk0MiIgc3Ryb2tlLXdpZHRoPSIxIi8+CjxwYXRoIGQ9Ik0yMCAxN0MyMy44NjYgMTcgMjcgMTMuODY2IDI3IDEwQzI3IDYuMTM0MDEgMjMuODY2IDMgMjAgM0MxNi4xMzQgMyAxMyA2LjEzNDAxIDEzIDEwQzEzIDEzLjg2NiAxNi4xMzQgMTcgMjAgMTdaIiBzdHJva2U9IiMyYTM5NDIiIHN0cm9rZS13aWR0aD0iMSIvPgo8cGF0aCBkPSJNNS44NzUxMSAzNC4wMDAyQzcuMTAzNzYgMzAuNjAyMSAxMC4yNDcgMjggMTQgMjhIMjZDMjkuNzUzIDI4IDMyLjg5NjIgMzAuNjAyMSAzNC4xMjQ5IDM0LjAwMDIiIHN0cm9rZT0iIzJhMzk0MiIgc3Ryb2tlLXdpZHRoPSIxIi8+Cjwvc3ZnPgo=');
            background-size: 400px;
            background-color: #0b141a;
            position: relative;
        }

        .chat-header {
            padding: 10px 16px;
            background-color: #202c33;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-left: 1px solid #2a3942;
        }

        .contact-info {
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .contact-status {
            font-size: 13px;
            color: #8696a0;
        }

        .chat-actions {
            display: flex;
            gap: 20px;
            color: #aebac1;
        }

        .chat-actions i {
            cursor: pointer;
            font-size: 18px;
            transition: color 0.2s;
        }

        .chat-actions i:hover {
            color: #e9edef;
        }

        .messages-container {
            flex: 1;
            padding: 20px;
            overflow-y: auto;
            display: flex;
            flex-direction: column;
            gap: 10px;
        }

        .message {
            max-width: 65%;
            padding: 8px 12px;
            border-radius: 7.5px;
            position: relative;
            font-size: 14.5px;
            line-height: 1.4;
            word-wrap: break-word;
        }

        .received {
            background-color: #202c33;
            align-self: flex-start;
            border-top-left-radius: 0;
        }

        .sent {
            background-color: #005c4b;
            align-self: flex-end;
            border-top-right-radius: 0;
        }

        .message-time {
            font-size: 11px;
            color: #8696a0;
            text-align: right;
            margin-top: 2px;
        }

        .message-input-container {
            padding: 10px 16px;
            background-color: #202c33;
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .input-actions {
            display: flex;
            gap: 15px;
            color: #8696a0;
        }

        .input-actions i {
            cursor: pointer;
            font-size: 20px;
            transition: color 0.2s;
        }

        .input-actions i:hover {
            color: #e9edef;
        }

        .message-input {
            flex: 1;
            background-color: #2a3942;
            border-radius: 8px;
            padding: 9px 12px;
            display: flex;
            align-items: center;
        }

        .message-input input {
            background-color: transparent;
            border: none;
            outline: none;
            color: #d1d7db;
            width: 100%;
            font-size: 15px;
        }

        .send-button {
            color: #8696a0;
            cursor: pointer;
            font-size: 20px;
            transition: color 0.2s;
        }

        .send-button:hover {
            color: #e9edef;
        }

        /* Menu and Modal Styles */
        .menu {
            position: absolute;
            background-color: #233138;
            border-radius: 5px;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.5);
            z-index: 100;
            padding: 8px 0;
            min-width: 180px;
            display: none;
        }

        .menu-item {
            padding: 10px 20px;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 15px;
            transition: background-color 0.2s;
        }

        .menu-item:hover {
            background-color: #182229;
        }

        .menu-item i {
            width: 20px;
            text-align: center;
        }

        .modal {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.7);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 1000;
            display: none;
        }

        .modal-content {
            background-color: #2a3942;
            border-radius: 8px;
            padding: 20px;
            width: 90%;
            max-width: 400px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
        }

        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
        }

        .modal-title {
            font-size: 18px;
            font-weight: 500;
        }

        .close-modal {
            color: #8696a0;
            cursor: pointer;
            font-size: 20px;
        }

        .modal-body {
            margin-bottom: 20px;
        }

        .modal-input {
            width: 100%;
            padding: 12px;
            background-color: #1f2c33;
            border: 1px solid #2a3942;
            border-radius: 5px;
            color: #e9edef;
            font-size: 15px;
            margin-bottom: 15px;
        }

        .modal-buttons {
            display: flex;
            justify-content: flex-end;
            gap: 10px;
        }

        .btn {
            padding: 10px 20px;
            border-radius: 5px;
            cursor: pointer;
            font-weight: 500;
            transition: background-color 0.2s;
        }

        .btn-cancel {
            background-color: transparent;
            color: #8696a0;
        }

        .btn-cancel:hover {
            background-color: #1f2c33;
        }

        .btn-primary {
            background-color: #005c4b;
            color: #e9edef;
            border: none;
        }

        .btn-primary:hover {
            background-color: #017561;
        }

        /* Status indicator */
        .status-indicator {
            width: 10px;
            height: 10px;
            border-radius: 50%;
            background-color: #00a884;
            position: absolute;
            bottom: 0;
            right: 0;
            border: 2px solid #111b21;
        }

        .avatar-container {
            position: relative;
            display: inline-block;
        }

        /* Responsive adjustments */
        @media (max-width: 900px) {
            .sidebar {
                width: 40%;
            }
        }

        @media (max-width: 600px) {
            .whatsapp-container {
                width: 100%;
                height: 100vh;
                border-radius: 0;
            }
            
            .sidebar {
                width: 100%;
            }
            
            .chat-area {
                display: none;
            }
            
            .mobile-chat-active .sidebar {
                display: none;
            }
            
            .mobile-chat-active .chat-area {
                display: flex;
            }
        }
    </style>
</head>
<body>
    <div class="whatsapp-container">
        <!-- Sidebar with chats list -->
        <div class="sidebar">
            <div class="sidebar-header">
                <div class="user-profile">
                    <div class="avatar-container">
                        <div class="avatar">
                            <i class="fas fa-user" style="color: #fff;"></i>
                        </div>
                        <div class="status-indicator"></div>
                    </div>
                    <div class="user-name">You</div>
                </div>
                <div class="sidebar-icons">
                    <i class="fas fa-users" id="status-icon"></i>
                    <i class="fas fa-circle-notch" id="new-chat-icon"></i>
                    <i class="fas fa-comment-alt" id="chat-icon"></i>
                    <i class="fas fa-ellipsis-v" id="menu-icon"></i>
                </div>
            </div>
            
            <div class="search-container">
                <div class="search-box">
                    <i class="fas fa-search"></i>
                    <input type="text" id="search-input" placeholder="Search or start new chat">
                </div>
            </div>
            
            <div class="chats-list" id="chats-list">
                <!-- Chat items will be populated by JavaScript -->
            </div>
        </div>
        
        <!-- Main chat area -->
        <div class="chat-area">
            <div class="chat-header">
                <div class="contact-info">
                    <div class="avatar">
                        <i class="fas fa-user" style="color: #fff;"></i>
                    </div>
                    <div>
                        <div class="chat-name" id="active-chat-name">Select a chat</div>
                        <div class="contact-status" id="active-chat-status">Click on a chat to start messaging</div>
                    </div>
                </div>
                <div class="chat-actions">
                    <i class="fas fa-search" id="chat-search-icon"></i>
                    <i class="fas fa-paperclip" id="attach-icon"></i>
                    <i class="fas fa-ellipsis-v" id="chat-menu-icon"></i>
                </div>
            </div>
            
            <div class="messages-container" id="messages-container">
                <!-- Messages will be populated by JavaScript -->
                <div class="welcome-message">
                    <div class="message received">
                        Welcome to WhatsApp Web Clone! Select a conversation from the sidebar to start chatting.
                        <div class="message-time">Just now</div>
                    </div>
                </div>
            </div>
            
            <div class="message-input-container">
                <div class="input-actions">
                    <i class="far fa-grin" id="emoji-icon"></i>
                    <i class="fas fa-paperclip" id="message-attach-icon"></i>
                </div>
                <div class="message-input">
                    <input type="text" id="message-input" placeholder="Type a message" disabled>
                </div>
                <div class="send-button">
                    <i class="fas fa-microphone" id="mic-icon"></i>
                </div>
            </div>
        </div>
    </div>

    <!-- Menu for sidebar options -->
    <div class="menu" id="sidebar-menu">
        <div class="menu-item" id="menu-profile">
            <i class="fas fa-user"></i>
            <span>Profile</span>
        </div>
        <div class="menu-item" id="menu-archived">
            <i class="fas fa-archive"></i>
            <span>Archived</span>
        </div>
        <div class="menu-item" id="menu-starred">
            <i class="fas fa-star"></i>
            <span>Starred Messages</span>
        </div>
        <div class="menu-item" id="menu-settings">
            <i class="fas fa-cog"></i>
            <span>Settings</span>
        </div>
        <div class="menu-item" id="menu-logout">
            <i class="fas fa-sign-out-alt"></i>
            <span>Log out</span>
        </div>
    </div>

    <!-- Menu for chat options -->
    <div class="menu" id="chat-menu">
        <div class="menu-item" id="chat-menu-contact">
            <i class="fas fa-user"></i>
            <span>Contact Info</span>
        </div>
        <div class="menu-item" id="chat-menu-media">
            <i class="fas fa-images"></i>
            <span>Media, Links and Docs</span>
        </div>
        <div class="menu-item" id="chat-menu-search">
            <i class="fas fa-search"></i>
            <span>Search</span>
        </div>
        <div class="menu-item" id="chat-menu-mute">
            <i class="fas fa-bell-slash"></i>
            <span>Mute Notifications</span>
        </div>
        <div class="menu-item" id="chat-menu-clear">
            <i class="fas fa-trash"></i>
            <span>Clear Chat</span>
        </div>
    </div>

    <!-- Modal for new chat -->
    <div class="modal" id="new-chat-modal">
        <div class="modal-content">
            <div class="modal-header">
                <div class="modal-title">New Chat</div>
                <div class="close-modal" id="close-new-chat-modal">&times;</div>
            </div>
            <div class="modal-body">
                <input type="text" class="modal-input" id="new-chat-input" placeholder="Search contacts">
                <div id="contacts-list">
                    <!-- Contacts will be populated by JavaScript -->
                </div>
            </div>
            <div class="modal-buttons">
                <button class="btn btn-cancel" id="cancel-new-chat">Cancel</button>
                <button class="btn btn-primary" id="create-chat" disabled>Create</button>
            </div>
        </div>
    </div>

    <!-- Modal for profile -->
    <div class="modal" id="profile-modal">
        <div class="modal-content">
            <div class="modal-header">
                <div class="modal-title">Your Profile</div>
                <div class="close-modal" id="close-profile-modal">&times;</div>
            </div>
            <div class="modal-body">
                <div style="text-align: center; margin-bottom: 20px;">
                    <div class="avatar" style="width: 80px; height: 80px; margin: 0 auto 15px;">
                        <i class="fas fa-user" style="color: #fff; font-size: 40px;"></i>
                    </div>
                    <div style="font-size: 18px; font-weight: 500;">Your Name</div>
                    <div style="color: #8696a0; font-size: 14px;">+1 234 567 890</div>
                </div>
                <input type="text" class="modal-input" placeholder="Your name" value="Your Name">
                <input type="text" class="modal-input" placeholder="About" value="Hey there! I am using WhatsApp.">
            </div>
            <div class="modal-buttons">
                <button class="btn btn-cancel" id="cancel-profile">Cancel</button>
                <button class="btn btn-primary" id="save-profile">Save</button>
            </div>
        </div>
    </div>

    <script>
        // Chat data
        const chats = [
            {
                id: 1,
                name: "Alex Johnson",
                status: "online",
                lastMessage: "Hey, are we still meeting tomorrow?",
                lastTime: "10:42 AM",
                messages: [
                    { text: "Hey there! How's it going?", time: "10:30 AM", sent: false },
                    { text: "Pretty good! Just finished that project we were talking about.", time: "10:32 AM", sent: true },
                    { text: "That's awesome! Did you get the feedback from the client?", time: "10:33 AM", sent: false },
                    { text: "Yes, they loved it! Only a few minor changes requested.", time: "10:35 AM", sent: true },
                    { text: "Great news! Are we still meeting tomorrow to discuss the next steps?", time: "10:42 AM", sent: false }
                ]
            },
            {
                id: 2,
                name: "Sarah Williams",
                status: "last seen today at 09:15",
                lastMessage: "Thanks for your help with the project!",
                lastTime: "Yesterday",
                messages: [
                    { text: "Hi Sarah! I've finished the design mockups.", time: "Yesterday", sent: true },
                    { text: "That's great! Can you share them with me?", time: "Yesterday", sent: false },
                    { text: "Sure, I'll email them to you right now.", time: "Yesterday", sent: true },
                    { text: "Thanks for your help with the project!", time: "Yesterday", sent: false }
                ]
            },
            {
                id: 3,
                name: "Work Group",
                status: "5 participants",
                lastMessage: "Michael: The meeting has been rescheduled",
                lastTime: "Yesterday",
                messages: [
                    { text: "Hello team! We have a meeting scheduled for tomorrow at 10 AM.", time: "2 days ago", sent: false },
                    { text: "I might be a few minutes late, I have a doctor's appointment.", time: "2 days ago", sent: true },
                    { text: "No problem, we can start without you.", time: "2 days ago", sent: false },
                    { text: "The meeting has been rescheduled to 11 AM due to conflicts.", time: "Yesterday", sent: false }
                ]
            },
            {
                id: 4,
                name: "Mom",
                status: "last seen today at 08:30",
                lastMessage: "Call me when you get a chance",
                lastTime: "Sunday",
                messages: [
                    { text: "Hi honey, how are you doing?", time: "Sunday", sent: false },
                    { text: "I'm good mom! Just busy with work.", time: "Sunday", sent: true },
                    { text: "Don't work too hard. Call me when you get a chance.", time: "Sunday", sent: false }
                ]
            },
            {
                id: 5,
                name: "David Miller",
                status: "last seen yesterday at 19:45",
                lastMessage: "Let's catch up this weekend",
                lastTime: "Saturday",
                messages: [
                    { text: "Hey David, long time no see!", time: "Saturday", sent: true },
                    { text: "I know! How have you been?", time: "Saturday", sent: false },
                    { text: "Pretty good, just busy with work. Let's catch up this weekend!", time: "Saturday", sent: true }
                ]
            }
        ];

        // Contacts for new chat
        const contacts = [
            { id: 6, name: "Emma Wilson", status: "online" },
            { id: 7, name: "James Brown", status: "last seen today at 11:20" },
            { id: 8, name: "Olivia Davis", status: "last seen yesterday at 16:45" },
            { id: 9, name: "Lucas Miller", status: "online" },
            { id: 10, name: "Sophia Garcia", status: "last seen today at 09:30" }
        ];

        // DOM Elements
        const chatsList = document.getElementById('chats-list');
        const messagesContainer = document.getElementById('messages-container');
        const messageInput = document.getElementById('message-input');
        const activeChatName = document.getElementById('active-chat-name');
        const activeChatStatus = document.getElementById('active-chat-status');
        const searchInput = document.getElementById('search-input');
        const sidebarMenu = document.getElementById('sidebar-menu');
        const chatMenu = document.getElementById('chat-menu');
        const newChatModal = document.getElementById('new-chat-modal');
        const profileModal = document.getElementById('profile-modal');
        const contactsList = document.getElementById('contacts-list');
        const newChatInput = document.getElementById('new-chat-input');

        // State
        let activeChatId = null;
        let menuOpen = null;

        // Initialize the app
        function init() {
            renderChatList();
            setupEventListeners();
        }

        // Render chat list
        function renderChatList(filter = '') {
            chatsList.innerHTML = '';
            
            const filteredChats = chats.filter(chat => 
                chat.name.toLowerCase().includes(filter.toLowerCase())
            );
            
            if (filteredChats.length === 0) {
                chatsList.innerHTML = '<div style="text-align: center; padding: 20px; color: #8696a0;">No chats found</div>';
                return;
            }
            
            filteredChats.forEach(chat => {
                const chatItem = document.createElement('div');
                chatItem.className = `chat-item ${activeChatId === chat.id ? 'active' : ''}`;
                chatItem.dataset.id = chat.id;
                
                chatItem.innerHTML = `
                    <div class="avatar">
                        <i class="fas fa-user" style="color: #fff;"></i>
                    </div>
                    <div class="chat-info">
                        <div class="chat-name-time">
                            <div class="chat-name">${chat.name}</div>
                            <div class="chat-time">${chat.lastTime}</div>
                        </div>
                        <div class="chat-last-message">
                            <i class="fas fa-check-double"></i>
                            <span>${chat.lastMessage}</span>
                        </div>
                    </div>
                `;
                
                chatsList.appendChild(chatItem);
            });
        }

        // Render messages for active chat
        function renderMessages(chatId) {
            messagesContainer.innerHTML = '';
            
            const chat = chats.find(c => c.id === chatId);
            if (!chat) return;
            
            chat.messages.forEach(message => {
                const messageEl = document.createElement('div');
                messageEl.className = `message ${message.sent ? 'sent' : 'received'}`;
                messageEl.innerHTML = `
                    ${message.text}
                    <div class="message-time">${message.time}</div>
                `;
                messagesContainer.appendChild(messageEl);
            });
            
            // Scroll to bottom
            messagesContainer.scrollTop = messagesContainer.scrollHeight;
        }

        // Set active chat
        function setActiveChat(chatId) {
            activeChatId = chatId;
            const chat = chats.find(c => c.id === chatId);
            
            if (chat) {
                activeChatName.textContent = chat.name;
                activeChatStatus.textContent = chat.status;
                messageInput.disabled = false;
                messageInput.placeholder = "Type a message";
                renderMessages(chatId);
                
                // Update active state in chat list
                document.querySelectorAll('.chat-item').forEach(item => {
                    if (parseInt(item.dataset.id) === chatId) {
                        item.classList.add('active');
                    } else {
                        item.classList.remove('active');
                    }
                });
                
                // For mobile view
                document.querySelector('.whatsapp-container').classList.add('mobile-chat-active');
            }
        }

        // Send a new message
        function sendMessage() {
            const text = messageInput.value.trim();
            if (!text || !activeChatId) return;
            
            const chat = chats.find(c => c.id === activeChatId);
            if (!chat) return;
            
            // Add message to chat
            const now = new Date();
            const time = now.toLocaleTimeString([], {hour: '2-digit', minute:'2-digit'});
            
            chat.messages.push({
                text: text,
                time: time,
                sent: true
            });
            
            // Update last message and time
            chat.lastMessage = text;
            chat.lastTime = time;
            
            // Clear input
            messageInput.value = '';
            
            // Re-render
            renderMessages(activeChatId);
            renderChatList(searchInput.value);
            
            // Simulate reply after a short delay
            setTimeout(() => {
                const replies = [
                    "That's interesting!",
                    "I see what you mean.",
                    "Let me think about that.",
                    "Sounds good to me!",
                    "I'll get back to you on that."
                ];
                const randomReply = replies[Math.floor(Math.random() * replies.length)];
                
                chat.messages.push({
                    text: randomReply,
                    time: new Date().toLocaleTimeString([], {hour: '2-digit', minute:'2-digit'}),
                    sent: false
                });
                
                chat.lastMessage = randomReply;
                chat.lastTime = new Date().toLocaleTimeString([], {hour: '2-digit', minute:'2-digit'});
                
                renderMessages(activeChatId);
                renderChatList(searchInput.value);
            }, 1000 + Math.random() * 2000);
        }

        // Setup event listeners
        function setupEventListeners() {
            // Chat item clicks
            chatsList.addEventListener('click', (e) => {
                const chatItem = e.target.closest('.chat-item');
                if (chatItem) {
                    setActiveChat(parseInt(chatItem.dataset.id));
                }
            });
            
            // Send message on Enter
            messageInput.addEventListener('keypress', (e) => {
                if (e.key === 'Enter') {
                    sendMessage();
                }
            });
            
            // Search functionality
            searchInput.addEventListener('input', (e) => {
                renderChatList(e.target.value);
            });
            
            // Menu toggles
            document.getElementById('menu-icon').addEventListener('click', (e) => {
                toggleMenu(sidebarMenu, e.target);
            });
            
            document.getElementById('chat-menu-icon').addEventListener('click', (e) => {
                toggleMenu(chatMenu, e.target);
            });
            
            // New chat modal
            document.getElementById('new-chat-icon').addEventListener('click', () => {
                openNewChatModal();
            });
            
            document.getElementById('close-new-chat-modal').addEventListener('click', closeNewChatModal);
            document.getElementById('cancel-new-chat').addEventListener('click', closeNewChatModal);
            
            // Profile modal
            document.getElementById('menu-profile').addEventListener('click', () => {
                closeMenu();
                openProfileModal();
            });
            
            document.getElementById('close-profile-modal').addEventListener('click', closeProfileModal);
            document.getElementById('cancel-profile').addEventListener('click', closeProfileModal);
            document.getElementById('save-profile').addEventListener('click', () => {
                alert('Profile saved!');
                closeProfileModal();
            });
            
            // Contact search in new chat modal
            newChatInput.addEventListener('input', (e) => {
                renderContacts(e.target.value);
            });
            
            // Close menus when clicking outside
            document.addEventListener('click', (e) => {
                if (!e.target.closest('.menu') && !e.target.closest('.sidebar-icons i') && !e.target.closest('.chat-actions i')) {
                    closeMenu();
                }
            });
            
            // Clear chat
            document.getElementById('chat-menu-clear').addEventListener('click', () => {
                if (activeChatId) {
                    if (confirm('Are you sure you want to clear this chat?')) {
                        const chat = chats.find(c => c.id === activeChatId);
                        if (chat) {
                            chat.messages = [];
                            renderMessages(activeChatId);
                        }
                    }
                }
                closeMenu();
            });
            
            // Logout
            document.getElementById('menu-logout').addEventListener('click', () => {
                if (confirm('Are you sure you want to log out?')) {
                    alert('Logged out successfully!');
                    closeMenu();
                }
            });
        }

        // Toggle menu visibility
        function toggleMenu(menu, button) {
            if (menuOpen === menu) {
                closeMenu();
                return;
            }
            
            closeMenu();
            menuOpen = menu;
            
            const rect = button.getBoundingClientRect();
            menu.style.top = `${rect.bottom + 5}px`;
            menu.style.right = `${window.innerWidth - rect.right}px`;
            menu.style.display = 'block';
        }

        // Close open menu
        function closeMenu() {
            if (menuOpen) {
                menuOpen.style.display = 'none';
                menuOpen = null;
            }
        }

        // Open new chat modal
        function openNewChatModal() {
            newChatModal.style.display = 'flex';
            renderContacts();
            newChatInput.value = '';
            document.getElementById('create-chat').disabled = true;
        }

        // Close new chat modal
        function closeNewChatModal() {
            newChatModal.style.display = 'none';
        }

        // Open profile modal
        function openProfileModal() {
            profileModal.style.display = 'flex';
        }

        // Close profile modal
        function closeProfileModal() {
            profileModal.style.display = 'none';
        }

        // Render contacts for new chat
        function renderContacts(filter = '') {
            contactsList.innerHTML = '';
            
            const filteredContacts = contacts.filter(contact => 
                contact.name.toLowerCase().includes(filter.toLowerCase())
            );
            
            if (filteredContacts.length === 0) {
                contactsList.innerHTML = '<div style="text-align: center; padding: 10px; color: #8696a0;">No contacts found</div>';
                return;
            }
            
            filteredContacts.forEach(contact => {
                const contactItem = document.createElement('div');
                contactItem.className = 'chat-item';
                contactItem.dataset.id = contact.id;
                
                contactItem.innerHTML = `
                    <div class="avatar">
                        <i class="fas fa-user" style="color: #fff;"></i>
                    </div>
                    <div class="chat-info">
                        <div class="chat-name-time">
                            <div class="chat-name">${contact.name}</div>
                        </div>
                        <div class="chat-last-message">
                            <span>${contact.status}</span>
                        </div>
                    </div>
                `;
                
                contactItem.addEventListener('click', () => {
                    // In a real app, this would create a new chat
                    alert(`Starting a new chat with ${contact.name}`);
                    closeNewChatModal();
                });
                
                contactsList.appendChild(contactItem);
            });
        }

        // Initialize the app
        init();
    </script>
</body>
</html>
