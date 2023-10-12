<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Chat App</title>
    <style>
        /* CSS for Dark Theme */
        body {
            background-color: #1a1a1a;
            color: #ffffff;
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
        }

        /* CSS for Left Pane */
        #left-pane {
            width: 25%;
            height: 100vh;
            float: left;
            background-color: #121212;
        }

        #left-pane-header {
            background-color: #333;
            color: #fff;
            padding: 10px;
        }

        #left-pane-header button {
            width: 80%;
            float: left;
            background-color: #555;
            border: none;
            color: #fff;
            padding: 5px 10px;
            border-radius: 5px;
            cursor: pointer;
        }

        #left-pane-header .icon-button {
            width: 20%;
            float: left;
        }

        #chat-list {
            overflow-y: auto;
            height: calc(100vh - 60px);
            padding: 10px;
        }

        #chat-list .chat-item {
            padding: 5px;
            border-bottom: 1px solid #444;
            cursor: pointer;
        }

        /* CSS for Right Pane */
        #right-pane {
            width: 75%;
            height: 100vh;
            float: left;
            background-color: #1a1a1a;
            display: flex;
            flex-direction: column;
        }

        #right-pane-header {
            background-color: #333;
            color: #fff;
            padding: 10px;
            text-align: center;
        }

        #right-pane .floating-buttons {
            display: flex;
            justify-content: center;
            padding: 10px;
        }

        #right-pane .floating-buttons button {
            background-color: #555;
            border: none;
            color: #fff;
            padding: 5px 10px;
            border-radius: 5px;
            cursor: pointer;
            margin: 0 10px;
        }

        #right-pane .message-list {
            flex-grow: 1;
            overflow-y: auto;
            padding: 20px;
        }

        #right-pane .message-input-container {
            background-color: #333;
            display: flex;
            align-items: center;
            padding: 10px;
        }
        /*  This is message input right pane*/

        #right-pane .message-input {
            /*border-bottom-color rgb(142, 142, 160)
            /*chat gpt : same*/
            flex-grow: 1;
            /*chatgpt:

border-bottom-style none
border-image-outset 0
border-image-repeat stretch
border-image-slice 100%
border-image-source none
border-image-width 1

border-top-width 0px*/

            border: none;
            /*chatgpt:same*/
            padding: 5px 10px;
            /*chatgpt:same*/
            border-radius: 5px;
            /* chatgpt: same*/
            margin-right: 10px;
            /*chatptp:background-color rgb(68, 68, 68)*/
            background-color: #444;
            /*cahtgpt:background-color rgb(68, 68, 68)*/
            color: #fff;
        }

        #right-pane .send-button {
            background-color: #555;
            border: none;
            color: #fff;
            padding: 5px 10px;
            border-radius: 5px;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <!-- Left Pane -->
    <div id="left-pane">
        <div id="left-pane-header">
            <button id="new-chat-button">New Chat</button>
            <div class="icon-button">
                <img src="icon.png" alt="Hide Icon">
            </div>
        </div>
        <div id="chat-list">
            <!-- Chat list will be dynamically populated -->
        </div>
    </div>

    <!-- Right Pane -->
    <div id="right-pane">
        <div id="right-pane-header">
            <div class="floating-buttons">
                <button>Button 1</button>
                <button>Button 2</button>
            </div>
        </div>
        <div class="message-list" id="chat-messages">
            <!-- Chat messages will be displayed here -->
        </div>
        <div class="message-input-container">
            <input type="text" id="message-input" class="message-input" placeholder="Type your message...">
            <button id="send-button" class="send-button">Send</button>
        </div>
    </div>

    <script>
        // Function to create a new chat
        function createNewChat() {
            const chatList = document.getElementById('chat-list');
            const newChat = document.createElement('div');
            newChat.className = 'chat-item';
            newChat.textContent = 'New Chat'; // You can replace this with the actual chat name
            chatList.appendChild(newChat);
        }

        // Function to send a message
        function sendMessage() {
            const messageInput = document.getElementById('message-input');
            const chatMessages = document.getElementById('chat-messages');
            const messageText = messageInput.value;

            if (messageText.trim() !== '') {
                const message = document.createElement('div');
                message.className = 'message';
                message.textContent = messageText;
                chatMessages.appendChild(message);
                messageInput.value = '';
            }
        }

        // Attach event listeners
        document.getElementById('new-chat-button').addEventListener('click', createNewChat);
        document.getElementById('send-button').addEventListener('click', sendMessage);
        document.getElementById('message-input').addEventListener('keydown', function(event) {
            if (event.key === 'Enter') {
                sendMessage();
            }
        });
    </script>
</body>
</html>
