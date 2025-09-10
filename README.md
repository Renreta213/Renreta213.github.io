<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Library Reading Room with Free Books</title>
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
            padding: 20px;
            overflow-x: hidden;
        }
        
        /* Navigation */
        .navbar {
            background: rgba(255, 255, 255, 0.9);
            border-radius: 10px;
            padding: 15px 30px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            margin-bottom: 30px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .logo {
            font-size: 1.8rem;
            font-weight: 700;
            color: #1565c0;
            display: flex;
            align-items: center;
        }
        
        .logo i {
            margin-right: 10px;
        }
        
        .nav-links {
            display: flex;
            list-style: none;
        }
        
        .nav-links li {
            margin: 0 15px;
        }
        
        .nav-links a {
            text-decoration: none;
            color: #5e35b1;
            font-weight: 600;
            font-size: 1.1rem;
            padding: 8px 15px;
            border-radius: 8px;
            transition: all 0.3s ease;
        }
        
        .nav-links a:hover, .nav-links a.active {
            background: #5e35b1;
            color: white;
        }
        
        .container {
            max-width: 1200px;
            width: 100%;
            margin: 0 auto;
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
            cursor: pointer;
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
            cursor: pointer;
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
            box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.2);
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
            padding: 20px;
            background: rgba(255, 255, 255, 0.7);
            border-radius: 10px;
        }
        
        /* Page sections */
        .page-section {
            display: none;
            background: rgba(255, 255, 255, 0.9);
            border-radius: 15px;
            padding: 30px;
            margin: 20px 0;
            box-shadow: 0 5px 20px rgba(0, 0, 0, 0.1);
        }
        
        .page-section.active {
            display: block;
        }
        
        .page-section h2 {
            color: #4527a0;
            font-size: 2.5rem;
            margin-bottom: 20px;
        }
        
        .page-section p {
            color: #37474f;
            line-height: 1.8;
            font-size: 1.1rem;
            margin-bottom: 20px;
            text-align: left;
        }
        
        .free-books {
            display: flex;
            flex-wrap: wrap;
            gap: 20px;
            justify-content: center;
            margin-top: 30px;
        }
        
        .free-book {
            background: white;
            border-radius: 10px;
            width: 200px;
            padding: 15px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s ease;
            cursor: pointer;
        }
        
        .free-book:hover {
            transform: scale(1.05);
        }
        
        .free-book img {
            width: 100%;
            height: 250px;
            object-fit: cover;
            border-radius: 5px;
            margin-bottom: 10px;
        }
        
        .free-book h4 {
            color: #5e35b1;
            margin-bottom: 5px;
        }
        
        .free-book p {
            font-size: 0.9rem;
            text-align: center;
        }
        
        .btn {
            background: #5e35b1;
            color: white;
            border: none;
            padding: 12px 25px;
            border-radius: 8px;
            font-size: 1.1rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            margin: 10px;
        }
        
        .btn:hover {
            background: #4527a0;
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
        }
        
        /* New colorful book styles */
        .colorful-books {
            display: flex;
            flex-wrap: wrap;
            gap: 20px;
            justify-content: center;
            margin: 40px 0;
        }
        
        .color-book {
            width: 140px;
            height: 180px;
            border-radius: 5px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-weight: bold;
            font-size: 1.2rem;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
            transition: all 0.3s ease;
            cursor: pointer;
            text-align: center;
            padding: 10px;
        }
        
        .color-book:hover {
            transform: rotate(5deg) scale(1.1);
        }
        
        /* Kids reading section */
        .kids-section {
            display: flex;
            flex-wrap: wrap;
            align-items: center;
            justify-content: center;
            gap: 40px;
            margin: 50px 0;
            padding: 30px;
            background: rgba(255, 255, 255, 0.7);
            border-radius: 15px;
        }
        
        .kids-content {
            flex: 1;
            min-width: 300px;
            text-align: left;
        }
        
        .kids-content h2 {
            color: #4527a0;
            font-size: 2.5rem;
            margin-bottom: 20px;
        }
        
        .kids-image {
            flex: 1;
            min-width: 300px;
            border-radius: 15px;
            overflow: hidden;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
            cursor: pointer;
        }
        
        .kids-image img {
            width: 100%;
            height: auto;
            display: block;
            transition: transform 0.5s ease;
        }
        
        .kids-image:hover img {
            transform: scale(1.05);
        }
        
        /* Online books section */
        .online-books {
            background: rgba(255, 255, 255, 0.9);
            border-radius: 15px;
            padding: 30px;
            margin: 40px 0;
            box-shadow: 0 5px 20px rgba(0, 0, 0, 0.1);
        }
        
        .book-category {
            margin-bottom: 40px;
        }
        
        .book-category h3 {
            color: #4527a0;
            font-size: 2rem;
            margin-bottom: 20px;
            padding-bottom: 10px;
            border-bottom: 2px solid #e1bee7;
        }
        
        .book-list {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 20px;
            margin-top: 20px;
        }
        
        .book-item {
            background: white;
            border-radius: 10px;
            padding: 15px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s ease;
            text-align: left;
        }
        
        .book-item:hover {
            transform: translateY(-5px);
        }
        
        .book-item h4 {
            color: #5e35b1;
            margin-bottom: 10px;
            font-size: 1.2rem;
        }
        
        .book-item p {
            color: #37474f;
            font-size: 0.9rem;
            margin-bottom: 15px;
        }
        
        .book-link {
            display: inline-block;
            background: #5e35b1;
            color: white;
            padding: 8px 15px;
            border-radius: 5px;
            text-decoration: none;
            font-weight: 600;
            transition: all 0.3s ease;
        }
        
        .book-link:hover {
            background: #4527a0;
            transform: translateY(-2px);
        }
        
        /* Events page */
        .events-calendar {
            display: flex;
            flex-wrap: wrap;
            gap: 20px;
            justify-content: center;
            margin: 30px 0;
        }
        
        .event-card {
            background: white;
            border-radius: 10px;
            width: 300px;
            padding: 20px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            text-align: left;
            cursor: pointer;
            transition: transform 0.3s ease;
        }
        
        .event-card:hover {
            transform: translateY(-5px);
        }
        
        .event-date {
            background: #5e35b1;
            color: white;
            padding: 10px;
            border-radius: 5px;
            font-weight: bold;
            margin-bottom: 15px;
            display: inline-block;
        }
        
        /* Programs page */
        .program-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 25px;
            margin: 30px 0;
        }
        
        .program-card {
            background: white;
            border-radius: 10px;
            padding: 25px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            text-align: left;
            cursor: pointer;
            transition: transform 0.3s ease;
        }
        
        .program-card:hover {
            transform: translateY(-5px);
        }
        
        .program-card h3 {
            color: #5e35b1;
            margin-bottom: 15px;
            font-size: 1.5rem;
        }
        
        /* Support page */
        .donation-options {
            display: flex;
            flex-wrap: wrap;
            gap: 20px;
            justify-content: center;
            margin: 30px 0;
        }
        
        .donation-option {
            background: white;
            border-radius: 10px;
            width: 250px;
            padding: 25px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            cursor: pointer;
            transition: transform 0.3s ease;
        }
        
        .donation-option:hover {
            transform: translateY(-5px);
        }
        
        .donation-option h3 {
            color: #5e35b1;
            margin-bottom: 15px;
        }
        
        /* Book details modal */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.7);
            z-index: 1000;
            justify-content: center;
            align-items: center;
        }
        
        .modal-content {
            background: white;
            padding: 30px;
            border-radius: 15px;
            max-width: 500px;
            width: 90%;
            box-shadow: 0 5px 30px rgba(0, 0, 0, 0.3);
            position: relative;
        }
        
        .close-modal {
            position: absolute;
            top: 15px;
            right: 15px;
            font-size: 1.5rem;
            cursor: pointer;
            color: #5e35b1;
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
            
            .navbar {
                flex-direction: column;
                padding: 15px;
            }
            
            .nav-links {
                margin-top: 15px;
                flex-wrap: wrap;
                justify-content: center;
            }
            
            .nav-links li {
                margin: 5px;
            }
            
            .kids-section {
                flex-direction: column;
            }
            
            .kids-content {
                text-align: center;
            }
            
            .book-list {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <div class="floating-books" id="floatingBooks"></div>
    
    <!-- Navigation -->
    <nav class="navbar">
        <div class="logo">
            <i class="fas fa-book-reader"></i>
            <span>Library Reading Room</span>
        </div>
        <ul class="nav-links">
            <li><a href="#" class="active" data-page="home">Home</a></li>
            <li><a href="#" data-page="about">About Us</a></li>
            <li><a href="#" data-page="nonprofit">Nonprofit Mission</a></li>
            <li><a href="#" data-page="freebooks">Free Books</a></li>
            <li><a href="#" data-page="events">Events</a></li>
            <li><a href="#" data-page="programs">Programs</a></li>
            <li><a href="#" data-page="support">Support Us</a></li>
            <li><a href="#" data-page="contact">Contact</a></li>
        </ul>
    </nav>
    
    <div class="container">
        <!-- Home Page -->
        <div class="page-section active" id="home">
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
                <div class="card" onclick="showModal('Extensive Collection', 'Explore our vast collection of books, journals, and digital resources covering every topic imaginable.')">
                    <i class="fas fa-book-open"></i>
                    <h3>Extensive Collection</h3>
                    <p>Explore our vast collection of books, journals, and digital resources covering every topic imaginable.</p>
                </div>
                
                <div class="card" onclick="showModal('24/7 Access', 'Our digital resources are available around the clock. Physical reading room open from 8 AM to 10 PM.')">
                    <i class="fas fa-clock"></i>
                    <h3>24/7 Access</h3>
                    <p>Our digital resources are available around the clock. Physical reading room open from 8 AM to 10 PM.</p>
                </div>
                
                <div class="card" onclick="showModal('Community Space', 'Join book clubs, attend author talks, and connect with fellow reading enthusiasts in our welcoming space.')">
                    <i class="fas fa-users"></i>
                    <h3>Community Space</h3>
                    <p>Join book clubs, attend author talks, and connect with fellow reading enthusiasts in our welcoming space.</p>
                </div>
            </div>
            
            <div class="bookshelf">
                <div class="book" onclick="showBookDetail('Fiction', 'Explore imaginative stories from around the world. From classics to contemporary bestsellers.')">
                    <div class="book-spine" style="background: linear-gradient(45deg, #FF5252, #FF4081);">Fiction</div>
                </div>
                <div class="book" onclick="showBookDetail('Science', 'Discover the wonders of the universe with our science collection.')">
                    <div class="book-spine" style="background: linear-gradient(45deg, #4CAF50, #8BC34A);">Science</div>
                </div>
                <div class="book" onclick="showBookDetail('History', 'Journey through time with our historical accounts and biographies.')">
                    <div class="book-spine" style="background: linear-gradient(45deg, #FF9800, #FFC107);">History</div>
                </div>
                <div class="book" onclick="showBookDetail('Art', 'Explore visual arts, music, and creative expression.')">
                    <div class="book-spine" style="background: linear-gradient(45deg, #9C27B0, #673AB7);">Art</div>
                </div>
                <div class="book" onclick="showBookDetail('Poetry', 'Experience the beauty of language through verse.')">
                    <div class="book-spine" style="background: linear-gradient(45deg, #00BCD4, #009688);">Poetry</div>
                </div>
                <div class="book" onclick="showBookDetail('Travel', 'Discover new places and cultures through our travel section.')">
                    <div class="book-spine" style="background: linear-gradient(45deg, #3F51B5, #2196F3);">Travel</div>
                </div>
                <div class="book" onclick="showBookDetail('Biography', 'Read about remarkable lives and inspiring stories.')">
                    <div class="book-spine" style="background: linear-gradient(45deg, #795548, #FF5722);">Biography</div>
                </div>
            </div>
            
            <!-- Kids Reading Section -->
            <div class="kids-section">
                <div class="kids-content">
                    <h2>Inspiring Young Minds</h2>
                    <p>At our library, we believe in nurturing a love for reading from an early age. Our children's section is specially designed to be welcoming and engaging for young readers.</p>
                    <p>We offer weekly storytime sessions, reading challenges, and educational activities that make learning fun. Our dedicated children's librarians are always available to help find the perfect book for every child.</p>
                    <p>Seeing children discover the joy of reading is one of our greatest rewards. We're committed to creating a new generation of lifelong learners and readers.</p>
                    <button class="btn" onclick="showModal('Youth Programs', 'We offer: Storytime every Tuesday and Thursday at 10 AM, Summer Reading Challenge, Homework Help, and Reading Buddies mentorship program.')">Learn About Our Youth Programs</button>
                </div>
                <div class="kids-image" onclick="showModal('Children Reading', 'Our library provides a safe and stimulating environment for children to explore the world of books.')">
                    <img src="https://images.unsplash.com/photo-1481627834876-b7833e8f5570?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1000&q=80" alt="Happy children reading books in the library">
                </div>
            </div>
            
            <div class="quote">
                <i class="fas fa-quote-left"></i>
                There is more treasure in books than in all the pirate's loot on Treasure Island.
                <i class="fas fa-quote-right"></i>
                <p style="text-align: center; margin-top: 15px;">- Walt Disney</p>
            </div>
            
            <div class="library-content">
                <div class="card" onclick="showModal('Learning Resources', 'Access our extensive collection of educational materials, from textbooks to research databases.')">
                    <i class="fas fa-graduation-cap"></i>
                    <h3>Learning Resources</h3>
                    <p>Access our extensive collection of educational materials, from textbooks to research databases.</p>
                </div>
                
                <div class="card" onclick="showModal('Digital Access', 'Use our computers and free Wi-Fi, or access our digital collection from anywhere with an internet connection.')">
                    <i class="fas fa-laptop"></i>
                    <h3>Digital Access</h3>
                    <p>Use our computers and free Wi-Fi, or access our digital collection from anywhere with an internet connection.</p>
                </div>
                
                <div class="card" onclick="showModal('Community Events', 'Join us for author talks, workshops, book clubs, and special events for all ages throughout the year.')">
                    <i class="fas fa-calendar-alt"></i>
                    <h3>Community Events</h3>
                    <p>Join us for author talks, workshops, book clubs, and special events for all ages throughout the year.</p>
                </div>
            </div>
        </div>
        
        <!-- Free Books Page -->
        <div class="page-section" id="freebooks">
            <h2>Free Online Books</h2>
            <p>Discover thousands of free books available online. We've curated collections from reputable sources to help you find your next great read.</p>
            
            <!-- Fiction Books -->
            <div class="online-books">
                <div class="book-category">
                    <h3>Fiction Books</h3>
                    <div class="book-list">
                        <div class="book-item">
                            <h4>Pride and Prejudice</h4>
                            <p>Jane Austen's classic novel about love and society in 19th century England.</p>
                            <a href="https://www.gutenberg.org/ebooks/1342" class="book-link" target="_blank">Read Now</a>
                        </div>
                        <div class="book-item">
                            <h4>Moby Dick</h4>
                            <p>Herman Melville's epic tale of Captain Ahab's obsession with the white whale.</p>
                            <a href="https://www.gutenberg.org/ebooks/2701" class="book-link" target="_blank">Read Now</a>
                        </div>
                        <div class="book-item">
                            <h4>Alice's Adventures in Wonderland</h4>
                            <p>Lewis Carroll's fantastical story of a girl's journey through a magical world.</p>
                            <a href="https://www.gutenberg.org/ebooks/11" class="book-link" target="_blank">Read Now</a>
                        </div>
                        <div class="book-item">
                            <h4>The Adventures of Sherlock Holmes</h4>
                            <p>Arthur Conan Doyle's collection of detective stories featuring Sherlock Holmes.</p>
                            <a href="https://www.gutenberg.org/ebooks/1661" class="book-link" target="_blank">Read Now</a>
                        </div>
                    </div>
                </div>
                
                <!-- Science Books -->
                <div class="book-category">
                    <h3>Science Books</h3>
                    <div class="book-list">
                        <div class="book-item">
                            <h4>On the Origin of Species</h4>
                            <p>Charles Darwin's groundbreaking work on evolution and natural selection.</p>
                            <a href="https://www.gutenberg.org/ebooks/2009" class="book-link" target="_blank">Read Now</a>
                        </div>
                        <div class="book-item">
                            <h4>The Einstein Theory of Relativity</h4>
                            <p>H.A. Lorentz's explanation of Einstein's revolutionary theories.</p>
                            <a href="https://www.gutenberg.org/ebooks/5001" class="book-link" target="_blank">Read Now</a>
                        </div>
                        <div class="book-item">
                            <h4>The Outline of Science</h4>
                            <p>J. Arthur Thomson's comprehensive overview of scientific knowledge.</p>
                            <a href="https://www.gutenberg.org/ebooks/20417" class="book-link" target="_blank">Read Now</a>
                        </div>
                        <div class="book-item">
                            <h4>The Story of the Solar System</h4>
                            <p>George F. Chambers' accessible introduction to astronomy.</p>
                            <a href="https://www.gutenberg.org/ebooks/34714" class="book-link" target="_blank">Read Now</a>
                        </div>
                    </div>
                </div>
                
                <!-- History Books -->
                <div class="book-category">
                    <h3>History Books</h3>
                    <div class="book-list">
                        <div class="book-item">
                            <h4>The History of the Decline and Fall of the Roman Empire</h4>
                            <p>Edward Gibbon's monumental work on Roman history.</p>
                            <a href="https://www.gutenberg.org/ebooks/731" class="book-link" target="_blank">Read Now</a>
                        </div>
                        <div class="book-item">
                            <h4>The Autobiography of Benjamin Franklin</h4>
                            <p>Benjamin Franklin's account of his own life and achievements.</p>
                            <a href="https://www.gutenberg.org/ebooks/148" class="book-link" target="_blank">Read Now</a>
                        </div>
                        <div class="book-item">
                            <h4>Plutarch's Lives</h4>
                            <p>Biographies of famous Greeks and Romans by Plutarch.</p>
                            <a href="https://www.gutenberg.org/ebooks/674" class="book-link" target="_blank">Read Now</a>
                        </div>
                        <div class="book-item">
                            <h4>The History of Herodotus</h4>
                            <p>Herodotus' account of the Greco-Persian Wars.</p>
                            <a href="https://www.gutenberg.org/ebooks/2707" class="book-link" target="_blank">Read Now</a>
                        </div>
                    </div>
                </div>
                
                <!-- Children's Books -->
                <div class="book-category">
                    <h3>Children's Books</h3>
                    <div class="book-list">
                        <div class="book-item">
                            <h4>Peter Pan</h4>
                            <p>J.M. Barrie's classic tale of the boy who wouldn't grow up.</p>
                            <a href="https://www.gutenberg.org/ebooks/16" class="book-link" target="_blank">Read Now</a>
                        </div>
                        <div class="book-item">
                            <h4>The Wonderful Wizard of Oz</h4>
                            <p>L. Frank Baum's magical story of Dorothy's journey to Oz.</p>
                            <a href="https://www.gutenberg.org/ebooks/55" class="book-link" target="_blank">Read Now</a>
                        </div>
                        <div class="book-item">
                            <h4>Anne of Green Gables</h4>
                            <p>L.M. Montgomery's beloved story of an imaginative orphan girl.</p>
                            <a href="https://www.gutenberg.org/ebooks/45" class="book-link" target="_blank">Read Now</a>
                        </div>
                        <div class="book-item">
                            <h4>The Jungle Book</h4>
                            <p>Rudyard Kipling's stories of Mowgli and his animal friends.</p>
                            <a href="https://www.gutenberg.org/ebooks/236" class="book-link" target="_blank">Read Now</a>
                        </div>
                    </div>
                </div>
                
                <!-- Poetry Books -->
                <div class="book-category">
                    <h3>Poetry Collections</h3>
                    <div class="book-list">
                        <div class="book-item">
                            <h4>Leaves of Grass</h4>
                            <p>Walt Whitman's groundbreaking collection of American poetry.</p>
                            <a href="https://www.gutenberg.org/ebooks/1322" class="book-link" target="_blank">Read Now</a>
                        </div>
                        <div class="book-item">
                            <h4>The Complete Poems of Emily Dickinson</h4>
                            <p>Collection of poems by one of America's greatest poets.</p>
                            <a href="https://www.gutenberg.org/ebooks/12242" class="book-link" target="_blank">Read Now</a>
                        </div>
                        <div class="book-item">
                            <h4>Poems by William Wordsworth</h4>
                            <p>Collection of works by the renowned English Romantic poet.</p>
                            <a href="https://www.gutenberg.org/ebooks/12383" class="book-link" target="_blank">Read Now</a>
                        </div>
                        <div class="book-item">
                            <h4>The Raven and Other Poems</h4>
                            <p>Edgar Allan Poe's collection of haunting and lyrical poetry.</p>
                            <a href="https://www.gutenberg.org/ebooks/33338" class="book-link" target="_blank">Read Now</a>
                        </div>
                    </div>
                </div>
            </div>
            
            <div class="quote">
                <i class="fas fa-quote-left"></i>
                The more that you read, the more things you will know. The more that you learn, the more places you'll go.
                <i class="fas fa-quote-right"></i>
                <p style="text-align: center; margin-top: 15px;">- Dr. Seuss</p>
            </div>
            
            <p>All these books are available for free through Project Gutenberg and other public domain sources. We encourage you to explore these literary treasures and discover the joy of reading!</p>
            
            <button class="btn" onclick="window.open('https://www.gutenberg.org/', '_blank')">Explore More Free Books</button>
        </div>
        
        <!-- Other page sections (About, Nonprofit, Events, etc.) would go here -->
        
        <div class="footer">
            <p>© 2023 Library Reading Room | Visit us: 123 Knowledge Avenue, Learning City</p>
            <p>A 501(c)(3) Nonprofit Organization | EIN: 12-3456789</p>
        </div>
    </div>

    <!-- Modal -->
    <div class="modal" id="bookModal">
        <div class="modal-content">
            <span class="close-modal" onclick="closeModal()">&times;</span>
            <h2 id="modalTitle"></h2>
            <p id="modalContent"></p>
            <button class="btn" onclick="closeModal()">Close</button>
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
            const animation
