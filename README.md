<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>West Africa 2025: The Bridge</title>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet">
    <style>
        /* --- HIGH-END DESIGN VARIABLES --- */
        :root {
            --deep-blue: #0f172a;
            --gold: #d4af37;
            --pure-white: #ffffff;
            --glass: rgba(255, 255, 255, 0.1);
            --glass-border: rgba(255, 255, 255, 0.2);
            --text-grey: #94a3b8;
        }

        body {
            margin: 0;
            font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
            background-color: var(--deep-blue);
            color: var(--pure-white);
            overflow-x: hidden;
        }

        /* --- NAVIGATION --- */
        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px 5%;
            background: rgba(15, 23, 42, 0.95);
            backdrop-filter: blur(10px);
            position: sticky;
            top: 0;
            z-index: 1000;
            border-bottom: 1px solid var(--glass-border);
        }

        .logo { font-size: 1.5rem; font-weight: bold; letter-spacing: 2px; }
        .logo span { color: var(--gold); }

        .nav-links button {
            background: none;
            border: none;
            color: var(--text-grey);
            font-size: 1rem;
            margin-left: 30px;
            cursor: pointer;
            transition: 0.3s;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .nav-links button:hover, .nav-links button.active {
            color: var(--pure-white);
            text-shadow: 0 0 10px rgba(255,255,255,0.5);
        }

        .btn-donate-nav {
            background: var(--gold) !important;
            color: var(--deep-blue) !important;
            padding: 10px 25px;
            border-radius: 4px;
            font-weight: bold;
        }

        /* --- CONTENT AREAS --- */
        .section {
            display: none; /* Hidden by default */
            padding: 60px 5%;
            min-height: 80vh;
            animation: fadeIn 0.6s ease-in-out;
        }

        .section.active { display: block; }

        @keyframes fadeIn { from { opacity: 0; transform: translateY(20px); } to { opacity: 1; transform: translateY(0); } }

        /* --- HOME HERO --- */
        .hero-content {
            text-align: center;
            margin-top: 50px;
        }

        h1 { font-size: 4rem; margin-bottom: 10px; line-height: 1.1; }
        .subtitle { font-size: 1.5rem; color: var(--text-grey); margin-bottom: 40px; }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin-top: 50px;
        }

        .stat-card {
            background: var(--glass);
            border: 1px solid var(--glass-border);
            padding: 30px;
            border-radius: 15px;
            text-align: center;
        }

        .stat-number { font-size: 2.5rem; font-weight: bold; color: var(--gold); }

        /* --- ECONOMY TAB --- */
        .split-layout {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 50px;
            align-items: center;
        }

        .chart-container {
            background: var(--glass);
            padding: 40px;
            border-radius: 20px;
            border: 1px solid var(--glass-border);
        }

        .bar-chart { margin-top: 20px; }
        .bar-group { margin-bottom: 20px; }
        .bar-label { display: flex; justify-content: space-between; margin-bottom: 5px; }
        .bar-bg { background: rgba(255,255,255,0.1); height: 10px; border-radius: 5px; width: 100%; }
        .bar-fill { height: 100%; border-radius: 5px; background: var(--gold); width: 0%; transition: width 1.5s ease; }

        /* --- DONATION TAB --- */
        .donate-box {
            max-width: 600px;
            margin: 0 auto;
            background: white;
            color: var(--deep-blue);
            padding: 40px;
            border-radius: 20px;
            text-align: center;
            box-shadow: 0 20px 50px rgba(0,0,0,0.5);
        }

        .gofundme-placeholder {
            border: 2px dashed #ccc;
            background: #f9f9f9;
            padding: 50px;
            margin: 30px 0;
            border-radius: 10px;
        }

        /* --- FOOTER --- */
        footer {
            text-align: center;
            padding: 40px;
            border-top: 1px solid var(--glass-border);
            color: var(--text-grey);
            font-size: 0.9rem;
        }

        /* Mobile Adjustments */
        @media (max-width: 768px) {
            h1 { font-size: 2.5rem; }
            .split-layout { grid-template
