<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Library Reading Room</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #ffeb3b 0%, #e1bee7 100%);
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            padding: 20px;
            overflow-x: hidden;
        }
        
        .container {
            max-width: 1200px;
            width: 100%;
            text-align: center;
        }
        
        .header {
            margin-bottom: 40px;
        }
        
        h1 {
            font-size: 4.5rem;
            color: #1565c0;
            text-shadow: 3px 3px 6px rgba(0, 0, 0, 0.2);
            margin-bottom: 20px;
            font-weight: 800;
            letter-spacing: 2px;
        }
        
        .tagline {
            font-size: 1.8rem;
            color: #5e35b1;
            margin-bottom: 30px;
            font-weight: 500;
            font-style: italic;
        }
        
        .library-content {
            display: flex;
            justify-content: center;
            gap: 30px;
            flex-wrap: wrap;
            margin-top: 40px;
        }
        
        .card {
            background: rgba(255, 255, 255, 0.9);
            border-radius: 15px;
            padding: 25px;
            width: 300px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.15);
            transition: transform 0.3s ease;
        }
        
        .card:hover {
            transform: translateY(-10px);
        }
        
        .card i {
            font-size: 3rem;
            color: #7b1fa2;
            margin-bottom: 20px;
        }
        
        .card h3 {
            color: #4527a0;
            font-size: 1.8rem;
            margin-bottom: 15px;
        }
        
        .card p {
            color: #37474f;
            line-height: 1.6;
        }
        
        .bookshelf {
            width: 100%;
            height: 200px;
            background: #8d6e63;
            border-radius: 10px;
            margin: 50px 0;
            position: relative;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
            display: flex;
            justify-content: space-around;
            align-items: center;
            padding: 0 20px;
        }
        
        .book {
            width: 60px;
            height: 160px;
            border-radius: 5px;
            position: relative;
            transform: rotate(0deg);
            transition: transform 0.3s ease;
        }
        
        .book:hover {
            transform: rotate(5deg) scale(1.05);
        }
        
        .book-spine {
            width: 100%;
            height: 100%;
            border-radius: 5px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-weight: bold;
            writing-mode: vertical-rl;
            text-orientation: mixed;
            cursor: pointer;
        }
        
        .quote {
            font-size: 1.5rem;
            color: #283593;
            max-width: 800px;
            margin: 40px auto;
            padding: 25px;
            background: rgba(255, 255, 255, 0.7);
            border-radius: 15px;
            border-left: 5px solid #5e35b1;
            text-align: center;
        }
        
        .quote i {
            color: #5e35b1;
            margin: 0 10px;
        }
        
        .floating-books {
            position: absolute;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            pointer-events: none;
            z-index: -1;
        }
        
        .floating-book {
            position: absolute;
            font-size: 3rem;
            color: rgba(55, 71, 79, 0.15);
            animation: float 15s linear infinite;
        }
        
        @keyframes float {
            0% {
                transform: translateY(100vh) rotate(0deg);
            }
            100% {
                transform: translateY(-100px) rotate(360deg);
            }
        }
        
        .footer {
            margin-top: 50px;
            color: #5e35b1;
            font-size: 1.2rem;
        }
        
        @media (max-width: 768px) {
            h1 {
                font-size: 3rem;
            }
            
            .tagline {
                font-size: 1.4rem;
            }
            
            .card {
                width: 100%;
                max-width: 350px;
            }
        }
    </style>
</head>
<body>
    <div class="floating-books" id="floatingBooks"></div>
    
    <div class="container">
        <div class="header">
            <h1>LIBRARY READING ROOM</h1>
            <p class="tagline">A Sanctuary for Knowledge and Imagination</p>
        </div>
        
        <div class="quote">
            <i class="fas fa-quote-left"></i>
            The reading room is a sanctuary where minds expand and imaginations flourish
            <i class="fas fa-quote-right"></i>
        </div>
        
        <div class="library-content">
            <div class="card">
                <i class="fas fa-book-open"></i>
                <h3>Extensive Collection</h3>
                <p>Explore our vast collection of books, journals, and digital resources covering every topic imaginable.</p>
            </div>
            
            <div class="card">
                <i class="fas fa-clock"></i>
                <h3>24/7 Access</h3>
                <p>Our digital resources are available around the clock. Physical reading room open from 8 AM to 10 PM.</p>
            </div>
            
            <div class="card">
                <i class="fas fa-users"></i>
                <h3>Community Space</h3>
                <p>Join book clubs, attend author talks, and connect with fellow reading enthusiasts in our welcoming space.</p>
            </div>
        </div>
        
        <div class="bookshelf">
            <div class="book">
                <div class="book-spine" style="background-color: #3f51b5;">Fiction</div>
            </div>
            <div class="book">
                <div class="book-spine" style="background-color: #009688;">Science</div>
            </div>
            <div class="book">
                <div class="book-spine" style="background-color: #ff5722;">History</div>
            </div>
            <div class="book">
                <div class="book-spine" style="background-color: #673ab7;">Art</div>
            </div>
            <div class="book">
                <div class="book-spine" style="background-color: #e91e63;">Poetry</div>
            </div>
            <div class="book">
                <div class="book-spine" style="background-color: #4caf50;">Travel</div>
            </div>
            <div class="book">
                <div class="book-spine" style="background-color: #ff9800;">Biography</div>
            </div>
        </div>
        
        <div class="footer">
            <p>© 2023 Library Reading Room | Visit us: 123 Knowledge Avenue, Learning City</p>
        </div>
    </div>

    <script>
        // Create floating book icons
        const bookIcons = ['📚', '📖', '📕', '📗', '📘', '📙', '🔖'];
        const floatingBooks = document.getElementById('floatingBooks');
        
        for (let i = 0; i < 20; i++) {
            const book = document.createElement('div');
            book.className = 'floating-book';
            book.textContent = bookIcons[Math.floor(Math.random() * bookIcons.length)];
            
            const left = Math.random() * 100;
            const animationDuration = (Math.random() * 20) + 15;
            const fontSize = (Math.random() * 20) + 30;
            
            book.style.left = `${left}%`;
            book.style.animationDuration = `${animationDuration}s`;
            book.style.fontSize = `${fontSize}px`;
            book.style.opacity = 0.1 + (Math.random() * 0.3);
            book.style.animationDelay = `${Math.random() * 5}s`;
            
            floatingBooks.appendChild(book);
        }
        
        // Add interaction to books on the shelf
        const books = document.querySelectorAll('.book');
        books.forEach(book => {
            book.addEventListener('click', function() {
                this.style.transform = 'rotate(-5deg) scale(1.1)';
                setTimeout(() => {
                    this.style.transform = 'rotate(0deg) scale(1)';
                }, 1000);
            });
        });
    </script>
</body>
</html>
