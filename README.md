<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Stealth Squad Latest News</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-image: url('your-fixed-background-image.jpg'); /* Add your background image URL here */
            background-size: cover;
            background-attachment: fixed;
            color: white;
        }
        header {
            background-color: rgba(0, 0, 0, 0.7);
            color: white;
            padding: 1rem;
            text-align: center;
        }
        main {
            padding: 2rem;
            background-color: rgba(0, 0, 0, 0.7);
        }
        #login-form-section, #news-section, #news-form-section, #video-section, #presentation-section, #change-password-section {
            margin-bottom: 2rem;
        }
        #news-list, #video-list, #presentation-list {
            border: 1px solid #ddd;
            padding: 1rem;
            margin-top: 1rem;
        }
        .news-item, .video-item, .presentation-item {
            border-bottom: 1px solid #ddd;
            padding: 1rem 0;
            position: relative;
        }
        .news-item:last-child, .video-item:last-child, .presentation-item:last-child {
            border-bottom: none;
        }
        .delete-button {
            position: absolute;
            right: 0;
            top: 10px;
            background-color: red;
            color: white;
            border: none;
            padding: 5px 10px;
            cursor: pointer;
        }
        #news-content-section {
            display: none;
        }
    </style>
</head>
<body>
    <header>
        <h1>Stealth Squad Latest News</h1>
    </header>
    <main>
        <section id="login-form-section">
            <h2>Admin Login</h2>
            <form id="login-form">
                <label for="admin-username">Username:</label>
                <input type="text" id="admin-username" required>
                <label for="admin-password">Password:</label>
                <input type="password" id="admin-password" required>
                <button type="submit">Login</button>
            </form>
        </section>
        <section id="news-content-section">
            <section id="news-section">
                <h2>Latest News</h2>
                <div id="news-list"></div>
            </section>
            <section id="news-form-section">
                <h2>Add News</h2>
                <form id="news-form">
                    <label for="news-title">Title:</label>
                    <input type="text" id="news-title" required>
                    <label for="news-content">Content:</label>
                    <textarea id="news-content" required></textarea>
                    <button type="submit">Add News</button>
                </form>
            </section>
        </section>
    </main>
    <script>
        const validAdminUsername = 'your-admin-username'; // Replace with your username
        const validAdminPassword = 'your-admin-password'; // Replace with your password

        document.getElementById('login-form').addEventListener('submit', function(event) {
            event.preventDefault();
            const username = document.getElementById('admin-username').value;
            const password = document.getElementById('admin-password').value;

            if (username === validAdminUsername && password === validAdminPassword) {
                document.getElementById('login-form-section').style.display = 'none';
                document.getElementById('news-content-section').style.display = 'block';
            } else {
                alert('Invalid username or password.');
            }
        });

        document.getElementById('news-form').addEventListener('submit', function(event) {
            event.preventDefault();
            const newsTitle = document.getElementById('news-title').value;
            const newsContent = document.getElementById('news-content').value.replace(/\n/g, '<br>');
            
            if (newsTitle && newsContent) {
                const newsList = document.getElementById('news-list');
                const newsItem = document.createElement('div');
                newsItem.classList.add('news-item');
                
                const newsTitleElement = document.createElement('h3');
                newsTitleElement.textContent = newsTitle;
                const newsContentElement = document.createElement('p');
                newsContentElement.innerHTML = newsContent;
                const deleteButton = document.createElement('button');
                deleteButton.textContent = 'Delete';
                deleteButton.classList.add('delete-button');
                
                deleteButton.addEventListener('click', function() {
                    newsList.removeChild(newsItem);
                });
                
                newsItem.appendChild(newsTitleElement);
                newsItem.appendChild(newsContentElement);
                newsItem.appendChild(deleteButton);
                newsList.appendChild(newsItem);
                
                document.getElementById('news-form').reset();
            }
        });
    </script>
</body>
</html>
