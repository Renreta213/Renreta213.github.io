<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>West Africa Vision 2025 | Progress & Relief</title>
    <style>
        :root {
            --primary: #1a5e37; /* Forest Green - growth */
            --secondary: #e67e22; /* Burnt Orange - action */
            --dark: #2c3e50;
            --light: #f4f7f6;
        }

        body { font-family: 'Helvetica Neue', Arial, sans-serif; margin: 0; color: #333; background: var(--light); }
        
        /* Navigation */
        nav { background: white; padding: 20px 5%; display: flex; justify-content: space-between; box-shadow: 0 2px 10px rgba(0,0,0,0.1); position: sticky; top: 0; z-index: 100; }
        .logo { font-weight: bold; font-size: 1.5rem; color: var(--primary); }
        .nav-links a { margin-left: 20px; text-decoration: none; color: var(--dark); font-weight: 500; }

        /* Hero Section */
        .hero { 
            background: linear-gradient(rgba(0,0,0,0.7), rgba(0,0,0,0.7)), url('https://images.unsplash.com/photo-1531206715517-5c0ba140b2b8?auto=format&fit=crop&q=80&w=1600');
            background-size: cover; height: 70vh; display: flex; flex-direction: column; justify-content: center; align-items: center; color: white; text-align: center;
        }
        .hero h1 { font-size: 3.5rem; margin-bottom: 10px; }
        .hero p { font-size: 1.2rem; max-width: 700px; }

        /* Economic Section */
        .economic-box { padding: 60px 10%; background: white; }
        .stat-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 20px; margin-top: 30px; }
        .stat-card { background: var(--light); padding: 30px; border-radius: 10px; text-align: center; border-bottom: 5px solid var(--primary); }
        .stat-card h3 { color: var(--primary); font-size: 2rem; margin: 0; }

        /* Support/GoFundMe Section */
        .support-section { padding: 60px 10%; text-align: center; background: var(--dark); color: white; }
        .gofundme-placeholder { 
            background: rgba(255,255,255,0.1); border: 2px dashed var(--secondary); padding: 40px; border-radius: 15px; margin: 30px auto; max-width: 600px;
        }
        .btn-cta { 
            background: var(--secondary); color: white; padding: 18px 40px; text-decoration: none; border-radius: 50px; font-weight: bold; font-size: 1.2rem; display: inline-block; transition: transform 0.2s;
        }
        .btn-cta:hover { transform: scale(1.05); }

        footer { text-align: center; padding: 40px; font-size: 0.9rem; color: #777; }
    </style>
</head>
<body>

    <nav>
        <div class="logo">WEST AFRICA VISION</div>
        <div class="nav-links">
            <a href="#economics">Economic Stability</a>
            <a href="#support">Support Our Mission</a>
        </div>
    </nav>

    <section class="hero">
        <h1>Resilience & Growth</h1>
        <p>West Africa is the next global growth hub. While the economy stabilizes, we ensure no community is left behind during the transition.</p>
        <br>
        <a href="#support" class="btn-cta">SUPPORT THE CAUSE</a>
    </section>

    <section id="economics" class="economic-box">
        <h2 style="text-align: center;">2025 Economic Outlook</h2>
        <p style="text-align: center; max-width: 800px; margin: 0 auto;">Despite global pressures, the West African Economic and Monetary Union (WAEMU) is projected to grow by <b>5.9% in 2025</b>. We are seeing a historic shift toward industrialization and digital trade.</p>
        
        <div class="stat-grid">
            <div class="stat-card">
                <h3>7.0%</h3>
                <p>GDP Growth in Benin</p>
            </div>
            <div class="stat-card">
                <h3>10%</h3>
                <p>Growth in Senegal</p>
            </div>
            <div class="stat-card">
                <h3>AfCFTA</h3>
                <p>Regional Integration</p>
            </div>
        </div>
    </section>

    <section id="support" class="support-section">
        <h2>Direct Support & Humanitarian Aid</h2>
        <p>Economic numbers are rising, but the human cost of displacement in the Sahel remains high. Your contribution provides immediate food, water, and medical aid.</p>
        
        <div class="gofundme-placeholder">
            <h3>Support Our GoFundMe</h3>
            <p>Help us reach our goal of $50,000 for regional relief.</p>
            <a href="YOUR_GOFUNDME_LINK_HERE" class="btn-cta">DONATE VIA GOFUNDME</a>
        </div>
    </section>

    <footer>
        <p>&copy; 2025 West Africa Vision Project. Data sourced from IMF and World Bank Regional Outlooks.</p>
    </footer>

</body>
</html>
