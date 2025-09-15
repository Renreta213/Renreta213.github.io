<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Beautiful Library Reading Room</title>
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
        
        /* Free Books Section - Enhanced */
        .free-books-section {
            background: rgba(255, 255, 255, 0.9);
            border-radius: 15px;
            padding: 40px;
            margin: 40px 0;
            box-shadow: 0 5px 20px rgba(0, 0, 0, 0.1);
        }
        
        .section-header {
            text-align: center;
            margin-bottom: 40px;
        }
        
        .section-header h2 {
            color: #4527a0;
            font-size: 2.8rem;
            margin-bottom: 15px;
        }
        
        .section-header p {
            color: #5e35b1;
            font-size: 1.2rem;
            max-width: 800px;
            margin: 0 auto;
            text-align: center;
        }
        
        .category-tabs {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 15px;
            margin-bottom: 40px;
        }
        
        .category-tab {
            padding: 12px 25px;
            background: #e1bee7;
            border: none;
            border-radius: 30px;
            font-size: 1.1rem;
            font-weight: 600;
            color: #5e35b1;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 3px 10px rgba(0, 0, 0, 0.1);
        }
        
        .category-tab:hover {
            background: #ce93d8;
            transform: translateY(-3px);
        }
        
        .category-tab.active {
            background: #5e35b1;
            color: white;
        }
        
        .books-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 30px;
            margin-top: 20px;
        }
        
        .book-card {
            background: white;
            border-radius: 15px;
            overflow: hidden;
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
            transition: all 0.3s ease;
            display: flex;
            flex-direction: column;
            height: 100%;
        }
        
        .book-card:hover {
            transform: translateY(-10px) scale(1.02);
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.15);
        }
        
        .book-cover {
            height: 220px;
            overflow: hidden;
            position: relative;
        }
        
        .book-cover img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.5s ease;
        }
        
        .book-card:hover .book-cover img {
            transform: scale(1.1);
        }
        
        .book-category {
            position: absolute;
            top: 15px;
            right: 15px;
            background: rgba(94, 53, 177, 0.9);
            color: white;
            padding: 5px 12px;
            border-radius: 20px;
            font-size: 0.8rem;
            font-weight: 600;
        }
        
        .book-details {
            padding: 20px;
            flex-grow: 1;
            display: flex;
            flex-direction: column;
        }
        
        .book-title {
            color: #4527a0;
            font-size: 1.4rem;
            margin-bottom: 10px;
            font-weight: 700;
        }
        
        .book-author {
            color: #7b1fa2;
            font-size: 1rem;
            margin-bottom: 15px;
            font-style: italic;
        }
        
        .book-description {
            color: #37474f;
            font-size: 0.95rem;
            margin-bottom: 20px;
            line-height: 1.5;
            flex-grow: 1;
        }
        
        .book-actions {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .read-btn {
            background: #5e35b1;
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 8px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            text-decoration: none;
            display: inline-block;
        }
        
        .read-btn:hover {
            background: #4527a0;
            transform: translateY(-2px);
        }
        
        .book-meta {
            display: flex;
            align-items: center;
            color: #78909c;
            font-size: 0.9rem;
        }
        
        .book-meta i {
            margin-right: 5px;
        }
        
        .view-more {
            text-align: center;
            margin-top: 40px;
        }
        
        .view-more-btn {
            background: linear-gradient(45deg, #5e35b1, #9c27b0);
            color: white;
            border: none;
            padding: 15px 35px;
            border-radius: 30px;
            font-size: 1.1rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
        }
        
        .view-more-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.25);
        }
        
        /* Decorative elements */
        .decorative-element {
            width: 100px;
            height: 100px;
            position: absolute;
            opacity: 0.1;
            z-index: -1;
        }
        
        .dec-1 {
            top: 20%;
            left: 5%;
            background: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'%3E%3Cpath fill='%235e35b1' d='M50 10 L75 80 L25 80 Z'/%3E%3C/svg%3E");
            background-size: contain;
            background-repeat: no-repeat;
        }
        
        .dec-2 {
            top: 60%;
            right: 5%;
            background: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'%3E%3Ccircle fill='%23ffeb3b' cx='50' cy='50' r='40'/%3E%3C/svg%3E");
            background-size: contain;
            background-repeat: no-repeat;
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
            
            .books-grid {
                grid-template-columns: 1fr;
            }
            
            .category-tabs {
                flex-direction: column;
                align-items: center;
            }
            
            .category-tab {
                width: 80%;
                margin-bottom: 10px;
            }
        }
    </style>
</head>
<body>
    <div class="floating-books" id="floatingBooks"></div>
    <div class="decorative-element dec-1"></div>
    <div class="decorative-element dec-2"></div>
    
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
                
                <div class="card" onclick="showModal('24/7 Access', 'Our digital resources are available around the clock. Physical reading room open from 8 AM to 10
