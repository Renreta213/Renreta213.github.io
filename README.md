<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>West Africa Relief | Support & Awareness</title>
    <style>
        /* CSS - The Design */
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            margin: 0;
            line-height: 1.6;
            color: #333;
        }

        header {
            background: #2c3e50;
            color: white;
            padding: 1rem 5%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            position: sticky;
            top: 0;
            z-index: 1000;
        }

        .logo { font-size: 1.5rem; font-weight: bold; }

        .hero {
            background: linear-gradient(rgba(0,0,0,0.6), rgba(0,0,0,0.6)), 
                        url('https://images.unsplash.com/photo-1488521787991-ed7bbaae773c?auto=format&fit=crop&q=80&w=1600');
            background-size: cover;
            background-position: center;
            height: 80vh;
            color: white;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            padding: 0 20px;
        }

        .hero h1 { font-size: 3rem; margin-bottom: 1rem; }

        .btn-donate {
            background: #e67e22;
            color: white;
            padding: 15px 30px;
            text-decoration: none;
            font-size: 1.2rem;
            border-radius: 5px;
            font-weight: bold;
            transition: background 0.3s;
        }

        .btn-donate:hover { background: #d35400; }

        .container { padding: 4rem 10%; }

        .grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            margin-top: 2rem;
        }

        .card {
            background: #f9f9f9;
            padding: 2rem;
            border-radius: 8px;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
        }

        footer {
            background: #2c3e50;
            color: white;
            text-align: center;
            padding: 2rem;
            margin-top: 2rem;
        }
    </style>
</head>
<body>

    <header>
        <div class="logo">West Africa Relief</div>
        <nav>
            <a href="#about" style="color:white; text-decoration:none; margin-left:20px;">The Crisis</a>
            <a href="#donate" style="color:white; text-decoration:none; margin-left:20px;">Donate</a>
        </nav>
    </header>

    <section class="hero">
        <h1>Support Families in West Africa</h1>
        <p>Providing food, water, and hope to those facing displacement and hardship.</p>
        <a href="#donate" class="btn-donate">DONATE NOW</a>
    </section>

    <section id="about" class="container">
        <h2 style="text-align:center;">The Current Situation</h2>
        <p>In 2025, West Africa faces unique challenges. From the impact of regional instability to the effects of climate change on food supplies, millions are in need of basic necessities. Our goal is to provide immediate aid and long-term awareness for these resilient communities.</p>
        
        <div class="grid">
            <div class="card">
                <h3>Emergency Food Aid</h3>
                <p>We deliver essential nutrition to families in regions hit hardest by food shortages.</p>
            </div>
            <div class="card">
                <h3>Clean Water Access</h3>
                <p>Building sustainable water systems to prevent disease and support local health.</p>
            </div>
            <div class="card">
                <h3>Medical Support</h3>
                <p>Funding mobile clinics and essential supplies for displaced populations.</p>
            </div>
        </div>
    </section>

    <section id="donate" class="container" style="background:#f4f4f4; text-align:center;">
        <h2>Make a Difference Today</h2>
        <p>100% of public donations go directly to relief efforts on the ground.</p>
        <div style="margin-top:20px; border: 2px dashed #999; padding: 40px;">
            <p>[Secure Donation Gateway Embed Point]</p>
        </div>
    </section>

    <footer>
        <p>&copy; 2025 West Africa Relief Mission. All rights reserved.</p>
    </footer>

</body>
</html>
