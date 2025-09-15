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
        }
        
        .donation-option h3 {
            color: #5e35b1;
            margin-bottom: 15px;
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
                    <div class="book-spine" style="background: linear-gradient(45deg, #FF5252, #FF4081);">Fiction</div>
                </div>
                <div class="book">
                    <div class="book-spine" style="background: linear-gradient(45deg, #4CAF50, #8BC34A);">Science</div>
                </div>
                <div class="book">
                    <div class="book-spine" style="background: linear-gradient(45deg, #FF9800, #FFC107);">History</div>
                </div>
                <div class="book">
                    <div class="book-spine" style="background: linear-gradient(45deg, #9C27B0, #673AB7);">Art</div>
                </div>
                <div class="book">
                    <div class="book-spine" style="background: linear-gradient(45deg, #00BCD4, #009688);">Poetry</div>
                </div>
                <div class="book">
                    <div class="book-spine" style="background: linear-gradient(45deg, #3F51B5, #2196F3);">Travel</div>
                </div>
                <div class="book">
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
                    <button class="btn">Learn About Our Youth Programs</button>
                </div>
                <div class="kids-image">
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
                <div class="card">
                    <i class="fas fa-graduation-cap"></i>
                    <h3>Learning Resources</h3>
                    <p>Access our extensive collection of educational materials, from textbooks to research databases.</p>
                </div>
                
                <div class="card">
                    <i class="fas fa-laptop"></i>
                    <h3>Digital Access</h3>
                    <p>Use our computers and free Wi-Fi, or access our digital collection from anywhere with an internet connection.</p>
                </div>
                
                <div class="card">
                    <i class="fas fa-calendar-alt"></i>
                    <h3>Community Events</h3>
                    <p>Join us for author talks, workshops, book clubs, and special events for all ages throughout the year.</p>
                </div>
            </div>
        </div>
        
        <!-- About Us Page -->
        <div class="page-section" id="about">
            <h2>About Our Library</h2>
            <p>Founded in 1995, the Library Reading Room began as a small community initiative with just 200 books. Today, we have grown to become a cherished community resource with over 50,000 physical books and 100,000 digital resources.</p>
            
            <div class="colorful-books">
                <div class="color-book" style="background: linear-gradient(45deg, #FF5252, #FF4081);">Fiction</div>
                <div class="color-book" style="background: linear-gradient(45deg, #4CAF50, #8BC34A);">Science</div>
                <div class="color-book" style="background: linear-gradient(45deg, #FF9800, #FFC107);">History</div>
                <div class="color-book" style="background: linear-gradient(45deg, #9C27B0, #673AB7);">Art</div>
                <div class="color-book" style="background: linear-gradient(45deg, #00BCD4, #009688);">Poetry</div>
                <div class="color-book" style="background: linear-gradient(45deg, #3F51B5, #2196F3);">Travel</div>
            </div>
            
            <p>Our mission has always been to make knowledge and literature accessible to everyone, regardless of their background or financial situation. We believe that access to books and a quiet space for study and reflection is a right, not a privilege.</p>
            
            <div class="quote">
                <i class="fas fa-quote-left"></i>
                Libraries store the energy that fuels the imagination. They open up windows to the world and inspire us to explore and achieve.
                <i class="fas fa-quote-right"></i>
            </div>
        </div>
        
        <!-- Nonprofit Mission Page -->
        <div class="page-section" id="nonprofit">
            <h2>Our Nonprofit Mission</h2>
            <p>As a registered 501(c)(3) nonprofit organization, the Library Reading Room is dedicated to providing free access to educational resources for all members of our community. We are funded through donations, grants, and the generous support of volunteers.</p>
            
            <div class="colorful-books">
                <div class="color-book" style="background: linear-gradient(45deg, #FF6B35, #FF8E53);">Free Access</div>
                <div class="color-book" style="background: linear-gradient(45deg, #4EA1D3, #7BB2D9);">Community</div>
                <div class="color-book" style="background: linear-gradient(45deg, #453F78, #6A67CE);">Education</div>
                <div class="color-book" style="background: linear-gradient(45deg, #FF4081, #E91E63);">Equality</div>
            </div>
            
            <p>Our initiatives include:</p>
            <ul style="text-align: left; margin-left: 30px; line-height: 1.8;">
                <li>Free literacy programs for adults and children</li>
                <li>Community outreach to underserved neighborhoods</li>
                <li>Digital access programs providing free computers and internet</li>
                <li>Multilingual resources for non-native English speakers</li>
                <li>Accessibility services for patrons with disabilities</li>
            </ul>
            
            <button class="btn">Donate to Support Our Mission</button>
            <button class="btn">Volunteer With Us</button>
        </div>
        
        <!-- Free Books Page -->
        <div class="page-section" id="freebooks">
            <h2>Free Books & Resources</h2>
            <p>We are proud to offer a wide selection of free books and resources to our community. Below are some of our most popular free offerings:</p>
            
            <div class="free-books">
                <div class="free-book">
                    <img src="https://placehold.co/200x300/FF5252/white?text=Classics" alt="Classic Literature">
                    <h4>Classic Literature</h4>
                    <p>Timeless works from authors like Austen, Dickens, and Twain</p>
                </div>
                
                <div class="free-book">
                    <img src="https://placehold.co/200x300/4CAF50/white?text=Children" alt="Children's Books">
                    <h4>Children's Books</h4>
                    <p>Engaging stories for young readers of all ages</p>
                </div>
                
                <div class="free-book">
                    <img src="https://placehold.co/200x300/2196F3/white?text=Education" alt="Educational Resources">
                    <h4>Educational Resources</h4>
                    <p>Textbooks and study materials for students</p>
                </div>
                
                <div class="free-book">
                    <img src="https://placehold.co/200x300/9C27B0/white?text=E-books" alt="Digital Library">
                    <h4>Digital Library</h4>
                    <p>Thousands of e-books available for free download</p>
                </div>
            </div>
            
            <p>All our books are available to borrow at no cost. We also have a "Keep It" section where books are available to take home permanently without needing to return them.</p>
            
            <button class="btn">Browse Our Full Collection</button>
            <button class="btn">Download Free E-books</button>
        </div>
        
        <!-- Events Page -->
        <div class="page-section" id="events">
            <h2>Upcoming Events</h2>
            <p>Join us for these exciting upcoming events at the Library Reading Room. All events are free and open to the public.</p>
            
            <div class="events-calendar">
                <div class="event-card">
                    <span class="event-date">June 15</span>
                    <h3>Author Reading: Jane Smith</h3>
                    <p>Join award-winning author Jane Smith as she reads from her latest novel and discusses her writing process.</p>
                    <p><i class="fas fa-clock"></i> 6:00 PM - 7:30 PM</p>
                </div>
                
                <div class="event-card">
                    <span class="event-date">June 22</span>
                    <h3>Children's Story Hour</h3>
                    <p>Bring your little ones for a magical story hour featuring beloved children's books and interactive activities.</p>
                    <p><i class="fas fa-clock"></i> 10:00 AM - 11:00 AM</p>
                </div>
                
                <div class="event-card">
                    <span class="event-date">July 5</span>
                    <h3>Poetry Night</h3>
                    <p>Share your own work or enjoy readings from local poets at our monthly poetry night. All are welcome!</p>
                    <p><i class="fas fa-clock"></i> 7:00 PM - 9:00 PM</p>
                </div>
            </div>
            
            <button class="btn">View Full Events Calendar</button>
        </div>
        
        <!-- Programs Page -->
        <div class="page-section" id="programs">
            <h2>Library Programs</h2>
            <p>We offer a variety of educational and community programs for all ages. Explore our ongoing programs below.</p>
            
            <div class="program-grid">
                <div class="program-card">
                    <h3>Adult Literacy</h3>
                    <p>Our free adult literacy program offers one-on-one tutoring for adults looking to improve their reading and writing skills.</p>
                    <p><strong>Schedule:</strong> Tuesdays & Thursdays, 6-8 PM</p>
                </div>
                
                <div class="program-card">
                    <h3>Homework Help</h3>
                    <p>Students can get free homework assistance from trained volunteers after school in our dedicated study area.</p>
                    <p><strong>Schedule:</strong> Mon-Fri, 3-6 PM</p>
                </div>
                
                <div class="program-card">
                    <h3>Digital Literacy</h3>
                    <p>Learn computer basics, internet skills, and how to use library digital resources in our technology classes.</p>
                    <p><strong>Schedule:</strong> Wednesdays, 10 AM-12 PM</p>
                </div>
                
                <div class="program-card">
                    <h3>Book Clubs</h3>
                    <p>Join one of our many book clubs focusing on different genres and meet fellow reading enthusiasts.</p>
                    <p><strong>Schedule:</strong> Various times throughout the month</p>
                </div>
            </div>
        </div>
        
        <!-- Support Us Page -->
        <div class="page-section" id="support">
            <h2>Support Our Library</h2>
            <p>As a nonprofit organization, we rely on the generosity of our community to continue providing free access to knowledge and resources. There are many ways to support our mission.</p>
            
            <div class="donation-options">
                <div class="donation-option">
                    <h3>Become a Member</h3>
                    <p>Join our membership program with monthly or annual contributions that help sustain our operations.</p>
                    <button class="btn">Learn More</button>
                </div>
                
                <div class="donation-option">
                    <h3>One-Time Donation</h3>
                    <p>Make a one-time financial contribution to support our programs and services.</p>
                    <button class="btn">Donate Now</button>
                </div>
                
                <div class="donation-option">
                    <h3>Volunteer</h3>
                    <p>Share your time and skills by volunteering at the library. We have opportunities for all ages.</p>
                    <button class="btn">Volunteer</button>
                </div>
            </div>
            
            <div class="quote">
                <i class="fas fa-quote-left"></i>
                A library is not a luxury but one of the necessities of life. Your support helps ensure everyone has access to this necessity.
                <i class="fas fa-quote-right"></i>
            </div>
        </div>
        
        <!-- Contact Page -->
        <div class="page-section" id="contact">
            <h2>Contact Us</h2>
            <p>We'd love to hear from you! Whether you have questions, want to volunteer, or need assistance, our team is here to help.</p>
            
            <div class="library-content">
                <div class="card">
                    <i class="fas fa-map-marker-alt"></i>
                    <h3>Visit Us</h3>
                    <p>123 Knowledge Avenue<br>Learning City, LC 12345</p>
                </div>
                
                <div class="card">
                    <i class="fas fa-phone"></i>
                    <h3>Call Us</h3>
                    <p>(555) 123-4567<br>Mon-Fri: 9am-5pm</p>
                </div>
                
                <div class="card">
                    <i class="fas fa-envelope"></i>
                    <h3>Email Us</h3>
                    <p>info@libraryreadingroom.org<br>support@libraryreadingroom.org</p>
                </div>
            </div>
            
            <div class="quote">
                <i class="fas fa-quote-left"></i>
                A library is not a luxury but one of the necessities of life.
                <i class="fas fa-quote-right"></i>
            </div>
        </div>
        
        <div class="footer">
            <p>© 2023 Library Reading Room | Visit us: 123 Knowledge Avenue, Learning City</p>
            <p>A 501(c)(3) Nonprofit Organization | EIN: 12-3456789</p>
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
        
        // Navigation functionality
        const navLinks = document.querySelectorAll('.nav-links a');
        const pageSections = document.querySelectorAll('.page-section');
        
        navLinks.forEach(link => {
            link.addEventListener('click', function(e) {
                e.preventDefault();
                
                // Remove active class from all links
                navLinks.forEach(link => link.classList.remove('active'));
                
                // Add active class to clicked link
                this.classList.add('active');
                
                // Hide all page sections
                pageSections.forEach(section => section.classList.remove('active'));
                
                // Show the selected page section
                const pageId = this.getAttribute('data-page');
                document.getElementById(pageId).classList.add('active');
            });
        });
    </script>
</body>
</html>
