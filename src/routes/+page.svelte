<svelte:head>
	<title>Trillux Advertising Agency</title>
	<meta name="description" content="Elevating brands through strategy, design, and storytelling" />
	<meta name="viewport" content="width=device-width, initial-scale=1" />
	<link rel="preconnect" href="https://fonts.googleapis.com" />
	<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
	<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;500;600;700&family=Inter:wght@300;400;500;600&display=swap" rel="stylesheet" />
</svelte:head>

<!-- Navigation -->
<nav class="navbar">
	<div class="nav-container">
		<a href="#" class="logo">Trillux</a>
		<ul class="nav-links">
			<li><a href="#services">Services</a></li>
			<li><a href="#about">About</a></li>
			<li><a href="#portfolio">Portfolio</a></li>
			<li><a href="#contact" class="nav-cta">Get In Touch</a></li>
		</ul>
	</div>
</nav>

<!-- Hero Section -->
<section class="hero">
	<div class="hero-container">
		<div class="hero-content">
			<p class="pre-heading">Premium Branding & Creative Strategy</p>
			<h1>Your Idea Deserves To Be Seen</h1>
			<p class="hero-subtitle">You don't have a bad idea — you just don't have the right pitching team. We craft compelling narratives that turn vision into recognition.</p>
			<div class="hero-buttons">
				<button class="cta-primary">Start Your Project</button>
				<a href="#portfolio" class="cta-secondary">View Our Work →</a>
			</div>
		</div>
	</div>
	<div class="hero-divider"></div>
</section>

<!-- Services Section -->
<section id="services" class="section light">
	<div class="container">
		<div class="section-header">
			<p class="section-label">What We Offer</p>
			<h2>Services Tailored For Excellence</h2>
			<p class="section-intro">End-to-end creative solutions designed to position your brand at the forefront of your industry.</p>
		</div>
		<div class="services-grid">
			<div class="service-card">
				<div class="card-icon">◈</div>
				<h3>Brand Identity</h3>
				<p>Timeless logos, colour systems, and visual language that communicate your essence with clarity and distinction.</p>
			</div>
			<div class="service-card">
				<div class="card-icon">◇</div>
				<h3>Digital Campaigns</h3>
				<p>Strategic outreach across platforms — precision-targeted, beautifully crafted, and built to convert.</p>
			</div>
			<div class="service-card">
				<div class="card-icon">◎</div>
				<h3>Web Design & Development</h3>
				<p>Elegant, performant, and fully responsive digital homes that leave lasting impressions.</p>
			</div>
			<div class="service-card">
				<div class="card-icon">◆</div>
				<h3>Creative Direction</h3>
				<p>Guiding your brand's visual and narrative journey — from concept to polished execution.</p>
			</div>
		</div>
	</div>
</section>

<!-- About Section -->
<section id="about" class="section dark">
	<div class="container">
		<div class="about-grid">
			<div class="about-content">
				<p class="section-label">Our Philosophy</p>
				<h2>Where Strategy Meets Elegance</h2>
				<div class="divider"></div>
				<p>Trillux was founded on the belief that great advertising is not just about visibility — it's about resonance. Every brand has a story; our craft is refining it, amplifying it, and presenting it to the world with distinction.</p>
				<p>We combine creative intuition with data-backed precision, delivering campaigns that look exceptional and perform exceptionally.</p>
				<a href="#contact" class="text-link">Discover Our Approach →</a>
			</div>
		</div>
	</div>
</section>

<!-- Portfolio Preview -->
<section id="portfolio" class="section light">
	<div class="container">
		<div class="section-header">
			<p class="section-label">Selected Work</p>
			<h2>Projects That Speak</h2>
		</div>
		<div class="portfolio-grid">
			<div class="portfolio-card">
				<div class="portfolio-image"></div>
				<div class="portfolio-info">
					<h4>Luxe Hospitality Group</h4>
					<p>Brand Identity • Digital Strategy</p>
				</div>
			</div>
			<div class="portfolio-card">
				<div class="portfolio-image"></div>
				<div class="portfolio-info">
					<h4>Meridian Financial</h4>
					<p>Visual Identity • Web Design</p>
				</div>
			</div>
			<div class="portfolio-card">
				<div class="portfolio-image"></div>
				<div class="portfolio-info">
					<h4>Orchid Living</h4>
					<p>Brand Refresh • Campaign</p>
				</div>
			</div>
		</div>
	</div>
</section>

<!-- Contact Section -->
<section id="contact" class="section accent">
	<div class="container contact-container">
		<div class="contact-text">
			<p class="section-label">Let's Begin</p>
			<h2>Ready To Elevate Your Brand?</h2>
			<p>Every great partnership starts with a conversation. Tell us about your vision — we'll handle the rest.</p>
		</div>
		<form class="contact-form">
			<input type="text" placeholder="Your Name" required />
			<input type="email" placeholder="Email Address" required />
			<textarea rows="5" placeholder="Tell us about your project…" required></textarea>
			<button type="submit" class="cta-primary">Send Message</button>
		</form>
	</div>
</section>

<!-- Footer -->
<footer class="footer">
	<div class="container footer-grid">
		<div class="footer-brand">
			<h3>Trillux</h3>
			<p>Premium Advertising & Branding Agency</p>
		</div>
		<div class="footer-links">
			<h4>Quick Links</h4>
			<ul>
				<li><a href="#services">Services</a></li>
				<li><a href="#about">About</a></li>
				<li><a href="#portfolio">Portfolio</a></li>
				<li><a href="#contact">Contact</a></li>
			</ul>
		</div>
		<div class="footer-contact">
			<h4>Contact</h4>
			<p>hello@trillux.agency</p>
		</div>
	</div>
	<div class="footer-bottom">
		<p>© 2026 Trillux Advertising Agency. All rights reserved.</p>
	</div>
</footer>

<style>
	:global(*) {
		margin: 0;
		padding: 0;
		box-sizing: border-box;
	}

	:global(body) {
		font-family: 'Inter', sans-serif;
		color: #1a1a2e;
		line-height: 1.6;
		background: #fcfcfd;
	}

	h1, h2, h3, h4 {
		font-family: 'Playfair Display', serif;
		font-weight: 600;
		line-height: 1.2;
	}

	/* Navbar */
	.navbar {
		position: absolute;
		width: 100%;
		top: 0;
		z-index: 100;
		padding: 2rem 4rem;
	}

	.nav-container {
		max-width: 1400px;
		margin: 0 auto;
		display: flex;
		justify-content: space-between;
		align-items: center;
	}

	.logo {
		font-family: 'Playfair Display', serif;
		font-size: 1.75rem;
		font-weight: 700;
		color: white;
		text-decoration: none;
		letter-spacing: 1px;
	}

	.nav-links {
		display: flex;
		align-items: center;
		gap: 3rem;
		list-style: none;
	}

	.nav-links a {
		color: rgba(255,255,255,0.8);
		text-decoration: none;
		font-size: 0.95rem;
		font-weight: 400;
		transition: color 0.3s ease;
	}

	.nav-links a:hover {
		color: white;
	}

	.nav-cta {
		padding: 0.75rem 1.75rem;
		border: 1px solid rgba(255,255,255,0.3);
		border-radius: 2px;
	}

	.nav-cta:hover {
		border-color: white;
		background: rgba(255,255,255,0.1);
	}

	/* Hero */
	.hero {
		background: linear-gradient(135deg, #0f0f1a 0%, #1a1a2e 50%, #252545 100%);
		min-height: 100vh;
		display: flex;
		align-items: center;
		padding: 0 4rem;
		position: relative;
		overflow: hidden;
	}

	.hero::before {
		content: '';
		position: absolute;
		top: 0;
		right: 0;
		width: 50%;
		height: 100%;
		background: radial-gradient(circle at top right, rgba(233, 69, 96, 0.08), transparent 60%);
		pointer-events: none;
	}

	.hero-container {
		max-width: 1400px;
		margin: 0 auto;
		width: 100%;
		padding-top: 4rem;
	}

	.hero-content {
		max-width: 700px;
	}

	.pre-heading {
		color: #b8b8d4;
		font-size: 0.9rem;
		letter-spacing: 3px;
		text-transform: uppercase;
		margin-bottom: 1.5rem;
		font-weight: 500;
	}

	.hero h1 {
		font-size: 4rem;
		color: white;
		margin-bottom: 1.5rem;
	}

	.hero-subtitle {
		font-size: 1.15rem;
		color: #a8a8c4;
		margin-bottom: 2.5rem;
		line-height: 1.8;
		max-width: 600px;
	}

	.hero-buttons {
		display: flex;
		gap: 1.5rem;
		align-items: center;
		flex-wrap: wrap;
	}

	.cta-primary {
		padding: 1rem 2.5rem;
		background: #e94560;
		color: white;
		border: none;
		border-radius: 2px;
		font-size: 1rem;
		font-weight: 600;
		cursor: pointer;
		transition: all 0.3s ease;
		letter-spacing: 0.5px;
	}

	.cta-primary:hover {
		background: #d63854;
		transform: translateY(-2px);
		box-shadow: 0 10px 30px rgba(233, 69, 96, 0.25);
	}

	.cta-secondary {
		color: white;
		text-decoration: none;
		font-size: 1rem;
		padding: 1rem 0;
		border-bottom: 1px solid transparent;
		transition: border-color 0.3s ease;
	}

	.cta-secondary:hover {
		border-bottom-color: white;
	}

	.hero-divider {
		position: absolute;
		bottom: 0;
		left: 4rem;
		width: 60px;
		height: 3px;
		background: #e94560;
	}

	/* Sections Base */
	.section {
		padding: 6rem 2rem;
	}

	.section.light {
		background: #fcfcfd;
	}

	.section.dark {
		background: #12121f;
		color: white;
	}

	.section.accent {
		background: #f7f7fa;
	}

	.container {
		max-width: 1200px;
		margin: 0 auto;
	}

	.section-header {
		text-align: center;
		margin-bottom: 4rem;
	}

	.section-label {
		color: #e94560;
		font-size: 0.85rem;
		letter-spacing: 2px;
		text-transform: uppercase;
		margin-bottom: 1rem;
		font-weight: 600;
	}

	.section h2 {
		font-size: 2.5rem;
		margin-bottom: 1rem;
	}

	.section-intro {
		max-width: 600px;
		margin: 0 auto;
		color: #666;
		font-size: 1.05rem;
	}

	.section.dark .section-intro {
		color: #a0a0c0;
	}

	/* Services Grid */
	.services-grid {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
		gap: 2.5rem;
	}

	.service-card {
		background: white;
		padding: 2.5rem;
		box-shadow: 0 2px 20px rgba(0,0,0,0.04);
		transition: transform 0.3s ease, box-shadow 0.3s ease;
		border-radius: 2px;
	}

	.service-card:hover {
		transform: translateY(-6px);
		box-shadow: 0 12px 40px rgba(26, 26, 46, 0.08);
	}

	.card-icon {
		font-size: 1.75rem;
		color: #e94560;
		margin-bottom: 1.5rem;
	}

	.service-card h3 {
		font-size: 1.25rem;
		margin-bottom: 1rem;
		color: #1a1a2e;
	}

	.service-card p {
		color: #555;
		line-height: 1.7;
		font-size: 0.95rem;
	}

	/* About Section */
	.about-grid {
		max-width: 700px;
	}

	.about-content .section-label {
		margin-bottom: 0.75rem;
	}

	.about-content h2 {
		margin-bottom: 1.5rem;
	}

	.divider {
		width: 60px;
		height: 3px;
		background: #e94560;
		margin-bottom: 2rem;
	}

	.about-content p {
		margin-bottom: 1.5rem;
		color: #c0c0d8;
		font-size: 1.05rem;
		line-height: 1.8;
	}

	.text-link {
		color: #e94560;
		text-decoration: none;
		font-weight: 600;
		display: inline-block;
		margin-top: 1rem;
		border-bottom: 1px solid transparent;
		transition: border-color 0.2s ease;
	}

	.text-link:hover {
		border-bottom-color: #e94560;
	}

	/* Portfolio */
	.portfolio-grid {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
		gap: 2rem;
	}

	.portfolio-card {
		background: white;
		overflow: hidden;
		box-shadow: 0 4px 20px rgba(0,0,0,0.06);
		transition: transform 0.3s ease;
	}

	.portfolio-card:hover {
		transform: translateY(-8px);
	}

	.portfolio-image {
		height: 220px;
		background: linear-gradient(135deg, #1a1a2e, #e94560);
		opacity: 0.9;
	}

	.portfolio-info {
		padding: 1.75rem;
	}

	.portfolio-info h4 {
		font-size: 1.15rem;
		margin-bottom: 0.5rem;
		color: #1a1a2e;
	}

	.portfolio-info p {
		color: #777;
		font-size: 0.9rem;
	}

	/* Contact */
	.contact-container {
		display: grid;
		grid-template-columns: 1fr 1fr;
		gap: 4rem;
		align-items: start;
	}

	.contact-text h2 {
		margin-bottom: 1.5rem;
	}

	.contact-text p {
		color: #555;
		font-size: 1.05rem;
		line-height: 1.8;
	}

	.contact-form {
		display: flex;
		flex-direction: column;
		gap: 1rem;
	}

	.contact-form input,
	.contact-form textarea {
		padding: 1rem 1.25rem;
		border: 1px solid #e0e0e8;
		border-radius: 2px;
		font-size: 1rem;
		background: white;
		transition: border-color 0.2s ease;
		font-family: inherit;
	}

	.contact-form input:focus,
	.contact-form textarea:focus {
		outline: none;
		border-color: #e94560;
	}

	/* Footer */
	.footer {
		background: #0f0f1a;
		color: white;
		padding: 4rem 2rem 2rem;
	}

	.footer-grid {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
		gap: 3rem;
		margin-bottom: 3rem;
	}

	.footer-brand h3 {
		font-family: 'Playfair Display', serif;
		font-size: 1.5rem;
		margin-bottom: 1rem;
	}

	.footer-brand p {
		color: #888;
		font-size: 0.9rem;
	}

	.footer-links h4,
	.footer-contact h4 {
		font-family: 'Inter', sans-serif;
		font-size: 0.9rem;
		text-transform: uppercase;
		letter-spacing: 1px;
		margin-bottom: 1rem;
		color: #888;
	}

	.footer-links ul {
		list-style: none;
		display: flex;
		flex-direction: column;
		gap: 0.75rem;
	}

	.footer-links a {
		color: #bbb;
		text-decoration: none;
		transition: color 0.2s ease;
	}

	.footer-links a:hover {
		color: white;
	}

	.footer-contact p {
		color: #bbb;
	}

	.footer-bottom {
		text-align: center;
		padding-top: 2rem;
		border-top: 1px solid #222;
		color: #666;
		font-size: 0.85rem;
	}

	/* Responsive */
	@media (max-width: 900px) {
		.navbar, .hero {
			padding: 1.5rem;
		}

		.nav-links {
			gap: 1.5rem;
		}

		.hero h1 {
			font-size: 2.5rem;
		}

		.contact-container {
			grid-template-columns: 1fr;
		}
	}

	@media (max-width: 640px) {
		.nav-links {
			display: none;
		}

		.hero h1 {
			font-size: 2rem;
		}

		.section {
			padding: 4rem 1.5rem;
		}

		.section h2 {
			font-size: 1.75rem;
		}
	}
</style>
