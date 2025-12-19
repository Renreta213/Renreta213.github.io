<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>West Africa 2025 | Growth & Aid Initiative</title>
    <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;700;800&family=Open+Sans:wght@400;600&display=swap" rel="stylesheet">
    
    <style>
        /* --- CORE STYLING --- */
        :root {
            --primary: #004d40; /* Deep Teal - Professional */
            --accent: #d4af37; /* Gold - Wealth/Economy */
            --text: #333;
            --bg: #f8f9fa;
        }

        * { box-sizing: border-box; transition: all 0.3s ease; }
        
        body {
            font-family: 'Open Sans', sans-serif;
            margin: 0;
            background-color: var(--bg);
            color: var(--text);
            overflow-x: hidden;
        }

        h1, h2, h3 { font-family: 'Montserrat', sans-serif; }

        /* --- NAVIGATION --- */
        nav {
            background: white;
            padding: 1rem 5%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            box-shadow: 0 2px 15px rgba(0,0,0,0.1);
            position: sticky;
            top: 0;
            z-index: 1000;
        }

        .logo {
            font-size: 1.5rem;
            font-weight: 800;
            color: var(--primary);
            letter-spacing: -1px;
            display: flex;
            align-items: center;
        }

        .logo span { color: var(--accent); margin-left: 5px; }

        .nav-links button {
            background: none;
            border: none;
            font-size: 1rem;
            font-weight: 600;
            margin-left: 25px;
            cursor: pointer;
            color: #555;
            position: relative;
        }

        .nav-links button:hover, .nav-links button.active {
            color: var(--primary);
        }

        .nav-links button.active::after {
            content: '';
            display: block;
            width: 100%;
            height: 3px;
            background: var(--accent);
            position: absolute;
            bottom: -5px;
        }

        .donate-btn-nav {
            background-color: var(--primary) !important;
            color: white !important;
            padding: 10px 20px;
            border-radius: 50px;
        }

        .donate-btn-nav:hover { background-color: #00695c !important; transform: scale(1.05); }

        /* --- PAGE SYSTEM --- */
        .page-content { display: none; animation: fadeIn 0.8s; }
        .page-content.active-page { display: block; }

        @keyframes fadeIn { from { opacity: 0; transform: translateY(10px); } to { opacity: 1; transform: translateY(0); } }

        /* --- HERO SECTION (HOME) --- */
        .hero {
            height: 85vh;
            background: linear-gradient(rgba(0,50,0,0.7), rgba(0,0,0,0.6)), url('https://images.unsplash.com/photo-1516026672322-bc52d61a55d5?auto=format&fit=crop&q=80&w=1920');
            background-size: cover;
            background-position: center;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            color: white;
        }

        .hero h1 { font-size: 4rem; margin-bottom: 1rem; text-shadow: 2px 2px 10px rgba(0,0,0,0.5); }
        .hero p { font-size: 1.3rem; max-width: 700px; margin: 0 auto 2rem auto; }
        
        .cta-button {
            padding: 15px 40px;
            background: var(--accent);
            color: #000;
            font-weight: 800;
            text-decoration: none;
            border-radius: 5px;
            font-size: 1.1rem;
            border: 2px solid var(--accent);
        }
        
        .cta-button:hover { background: transparent; color: white; }

        /* --- ECONOMICS PAGE STYLES --- */
        .econ-header {
            background: var(--primary);
            color: white;
            padding: 80px 10%;
            text-align: center;
        }

        .data-container {
            max-width: 1100px;
            margin: -50px auto 50px auto;
            background: white;
            padding: 40px;
            border-radius: 10px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 40px;
        }

        .chart-box h3 { margin-bottom: 20px; border-bottom: 2px solid #eee; padding-bottom: 10px; }
        
        .progress-bar { background: #eee; height: 25px; border-radius: 5px; margin-bottom: 25px; position: relative; }
        .fill { background: var(--primary); height: 100%; border-radius: 5px; display: flex; align-items: center; padding-left: 10px; color: white; font-size: 0.8rem; width: 0; transition: width 1.5s ease-in-out; }
        .fill.senegal { width: 85%; background: #27ae60; }
        .fill.benin { width: 90%; background: #2ecc71; }
        .fill.ivory { width: 75%; background: #16a085; }

        /* --- MISSION PAGE STYLES --- */
        .mission-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 20px;
            padding: 50px 10%;
        }

        .mission-card {
            background: white;
            padding: 30px;
            border-top: 5px solid var(--accent);
            box-shadow: 0 5px 15px rgba(0,0,0,0.05);
        }

        /* --- DONATE PAGE STYLES --- */
        .donate-split {
            display: flex;
            flex-wrap: wrap;
            height: 90vh;
        }
        
        .donate-left {
            flex: 1;
            background: #f4f4f4;
            padding: 50px;
            display: flex;
            flex-direction: column;
            justify-content: center;
        }

        .donate-right {
            flex: 1;
            background: var(--primary);
            color: white;
            display: flex;
            align-items: center;
            justify-content: center;
            flex-direction: column;
            padding: 20px;
        }

        .gofundme-box {
            background: white;
            padding: 40px;
            border-radius: 10px;
            text-align: center;
            color: #333;
            max-width: 400px;
        }

        /* --- FOOTER --- */
        footer { background: #222; color: #aaa; padding: 40px; text-align: center; margin-top: 50px; }
        
        @media (max-width: 768px) {
            .hero h1 { font-size: 2.5rem; }
            .data-container { grid-template-columns: 1fr; margin-top: 20px; }
            .mission-grid { grid-template-columns: 1fr; }
            .donate-split { flex-direction: column; height: auto; }
        }
    </style>
</head>
<body>

    <nav>
        <div class="logo">WEST AFRICA <span>RISING</span></div>
        <div class="nav-links">
            <button onclick="showPage('home')" class="active" id="btn-home">Home</button>
            <button onclick="showPage('economics')" id="btn-economics">Economy</button>
            <button onclick="showPage('mission')" id="btn-mission">Our Mission</button>
            <button onclick="showPage('donate')" class="donate-btn-nav" id="btn-donate">Donate</button>
        </div>
    </nav>

    <div id="home" class="page-content active-page">
        <section class="hero">
            <div>
                <h1>A Region in Transformation.</h1>
                <p>Bridging the gap between explosive economic potential and humanitarian necessity.</p>
                <button onclick="showPage('donate')" class="cta-button">SUPPORT THE CAUSE</button>
                <button onclick="showPage('economics')" class="cta-button" style="background:transparent; border:2px solid white; color:white; margin-left:10px;">VIEW DATA</button>
            </div>
        </section>
        <div style="padding: 60px 10%; text-align: center;">
            <h2 style="font-size: 2.5rem; color: var(--primary);">Why West Africa? Why Now?</h2>
            <p style="max-width: 800px; margin: 0 auto; font-size: 1.1rem; line-height: 1.8;">
                The narrative of West Africa is changing. It is home to some of the world's fastest-growing economies. 
                Yet, climate shocks and regional instability threaten to derail this progress. We exist to stabilize the foundation 
                so the future can be built.
            </p>
        </div>
    </div>

    <div id="economics" class="page-content">
        <div class="econ-header">
            <h1>Economic Powerhouse</h1>
            <p>Data shows West Africa is resilient. Investment now yields stability for decades.</p>
        </div>
        
        <div class="data-container">
            <div class="text-side">
                <h2 style="color:var(--primary)">The 2025 Growth Trajectory</h2>
                <p>While much of the global economy slows, West African nations are accelerating. The <b>WAEMU</b> region is projected to outperform global averages.</p>
                <ul style="line-height: 2;">
                    <li><strong>Strategic Resources:</strong> Lithium, Gold, and Cocoa markets are surging.</li>
                    <li><strong>Tech Hubs:</strong> Lagos and Accra are attracting billions in Fintech capital.</li>
                    <li><strong>Infrastructure:</strong> New port expansions in Togo and Nigeria facilitate global trade.</li>
                </ul>
            </div>
            <div class="chart-box">
                <h3>Projected GDP Growth (2025)</h3>
                
                <p><strong>Benin</strong> (Rising Agricultural Tech)</p>
                <div class="progress-bar"><div class="fill benin">7.0% Growth</div></div>

                <p><strong>Senegal</strong> (Energy Sector Expansion)</p>
                <div class="progress-bar"><div class="fill senegal">6.5% Growth</div></div>

                <p><strong>Ivory Coast</strong> (Trade & Exports)</p>
                <div class="progress-bar"><div class="fill ivory">6.0% Growth</div></div>
                
                <small style="color:#777;">*Data sourced from IMF Regional Economic Outlook</small>
            </div>
        </div>
    </div>

    <div id="mission" class="page-content">
        <div style="text-align: center; padding: 60px 10%; background: #fff;">
            <h1 style="color: var(--primary); font-size: 3rem;">Where We Step In</h1>
            <p>Economic growth cannot sustain itself if the people are hungry. Our organization focuses on the humanitarian floor.</p>
        </div>

        <div class="mission-grid">
            <div class="mission-card">
                <h3 style="color: var(--primary);">Food Security</h3>
                <p>In the Sahel, climate change has disrupted harvest cycles. We provide drought-resistant seeds and emergency food parcels to keep farmers on their land.</p>
            </div>
            <div class="mission-card">
                <h3 style="color: var(--primary);">Displacement Aid</h3>
                <p>Regional conflicts have displaced thousands. We create "Stability Zones" offering temporary shelter, clean water, and schooling for children.</p>
            </div>
            <div class="mission-card">
                <h3 style="color: var(--primary);">Medical Access</h3>
                <p>Economic stability requires a healthy workforce. We fund mobile clinics that travel to rural areas outside the reach of city hospitals.</p>
            </div>
        </div>
    </div>

    <div id="donate" class="page-content">
        <div class="donate-split">
            <div class="donate-left">
                <h1 style="color: var(--primary); font-size: 3rem;">Join the Movement</h1>
                <p style="font-size: 1.2rem;">We are raising <strong>$50,000</strong> to deploy mobile clinics and food aid to the northern border regions.</p>
                
                <h3 style="margin-top: 30px;">How funds are used:</h3>
                <ul>
                    <li>$50 provides a family with clean water for a month.</li>
                    <li>$100 supplies emergency medical kits.</li>
                    <li>$500 sponsors a rural farming co-op.</li>
                </ul>
            </div>
            
            <div class="donate-right">
                <div class="gofundme-box">
                    <h2 style="color: #000;">Support via GoFundMe</h2>
                    <p>Secure, transparent, and direct.</p>
                    
                    <div style="background: #f4f4f4; padding: 20px; border: 2px dashed #ccc; margin: 20px 0;">
                        <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/e/e6/GoFundMe_logo.svg/2560px-GoFundMe_logo.svg.png" width="150" alt="GoFundMe">
                        <p style="margin-top:10px; font-weight:bold;">Campaign: West Africa Relief 2025</p>
                    </div>

                    <a href="#" class="cta-button" style="display:block; margin-top:20px;">GO TO DONATION PAGE</a>
                </div>
            </div>
        </div>
    </div>

    <footer>
        <p>&copy; 2025 West Africa Rising Initiative. All Rights Reserved.</p>
        <p>A non-profit dedicated to the stability and health of the ECOWAS region.</p>
    </footer>

    <script>
        function showPage(pageId) {
            // Hide all pages
            const pages = document.querySelectorAll('.page-content');
            pages.forEach(page => page.classList.remove('active-page'));
            
            // Deactivate all nav buttons
            const buttons = document.querySelectorAll('.nav-links button');
            buttons.forEach(btn => btn.classList.remove('active'));

            // Show selected page
            document.getElementById(pageId).classList.add('active-page');
            
            // Highlight selected button
            document.getElementById('btn-' + pageId).classList.add('active');

            // Scroll to top
            window.scrollTo(0, 0);
        }
    </script>

</body>
</html>
