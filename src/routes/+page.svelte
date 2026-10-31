<svelte:head>
	<title>Trillux Advertising Agency</title>
	<meta name="description" content="You don't have a bad idea — you just don't have the right pitching team" />
	<meta name="viewport" content="width=device-width, initial-scale=1" />
</svelte:head>

<header class="hero">
	<nav>
		<div class="logo">Trillux</div>
		<ul>
			<li><a href="#services">Services</a></li>
			<li><a href="#about">About</a></li>
			<li><a href="#contact">Contact</a></li>
		</ul>
	</nav>

	<div class="hero-content">
		<h1>Your Idea Deserves To Be Seen</h1>
		<p>You don't have a bad idea — you just don't have the right pitching team</p>
		<button class="cta">Start Your Project</button>
	</div>
</header>

<section id="services" class="section">
	<h2>What We Do</h2>
	<div class="cards">
		<div class="card">
			<h3>Branding</h3>
			<p>Identity that stands out and sticks</p>
		</div>
		<div class="card">
			<h3>Digital Campaigns</h3>
			<p>Reach the right people, in the right way</p>
		</div>
		<div class="card">
			<h3>Web Design</h3>
			<p>Fast, beautiful, high-converting websites</p>
		</div>
	</div>
</section>

<section id="about" class="section alt">
	<div class="about-wrap">
		<h2>About Trillux</h2>
		<p>We turn raw ideas into campaigns that connect. Strategy, design, and delivery — all under one roof.</p>
	</div>
</section>

<section id="contact" class="section">
	<h2>Get In Touch</h2>
	<form class="contact-form">
		<input type="text" placeholder="Your Name" required />
		<input type="email" placeholder="Email Address" required />
		<textarea rows="5" placeholder="Tell us about your idea…" required></textarea>
		<button type="submit" class="cta">Send Message</button>
	</form>
</section>

<style>
	:global(*) {
		margin: 0;
		padding: 0;
		box-sizing: border-box;
		font-family: system-ui, -apple-system, sans-serif;
	}

	.hero {
		background: linear-gradient(135deg, #1a1a2e, #16213e);
		color: white;
		min-height: 100vh;
		padding: 2rem 4rem;
	}

	nav {
		display: flex;
		justify-content: space-between;
		align-items: center;
		flex-wrap: wrap;
	}

	.logo {
		font-size: 1.5rem;
		font-weight: 700;
		letter-spacing: 1px;
	}

	nav ul {
		display: flex;
		gap: 2rem;
		list-style: none;
		flex-wrap: wrap;
	}

	nav a {
		color: #ccc;
		text-decoration: none;
		transition: color 0.2s ease;
	}

	nav a:hover {
		color: #fff;
	}

	.hero-content {
		margin-top: 6rem;
		max-width: 600px;
	}

	h1 {
		font-size: 3.5rem;
		line-height: 1.2;
		margin-bottom: 1.5rem;
	}

	.hero-content p {
		font-size: 1.2rem;
		color: #aaa;
		margin-bottom: 2rem;
		line-height: 1.6;
	}

	.cta {
		padding: 0.9rem 2.5rem;
		background: #e94560;
		color: white;
		border: none;
		border-radius: 8px;
		font-size: 1rem;
		font-weight: 600;
		cursor: pointer;
		transition: transform 0.2s ease, background 0.2s ease;
	}

	.cta:hover {
		background: #d63854;
		transform: translateY(-2px);
	}

	.section {
		padding: 4rem 2rem;
		background: #fff;
	}

	.section.alt {
		background: #f0f4f8;
	}

	.section h2 {
		text-align: center;
		font-size: 2rem;
		margin-bottom: 3rem;
		color: #1a1a2e;
	}

	.cards {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
		gap: 2rem;
		max-width: 1000px;
		margin: 0 auto;
	}

	.card {
		background: white;
		padding: 2rem;
		border-radius: 12px;
		box-shadow: 0 4px 12px rgba(0, 0, 0, 0.06);
		transition: transform 0.2s ease;
	}

	.card:hover {
		transform: translateY(-4px);
	}

	.card h3 {
		margin-bottom: 0.5rem;
		color: #1a1a2e;
		font-size: 1.25rem;
	}

	.card p {
		color: #555;
		line-height: 1.5;
	}

	.about-wrap {
		max-width: 700px;
		margin: 0 auto;
		text-align: center;
		font-size: 1.1rem;
		color: #333;
		line-height: 1.7;
	}

	.contact-form {
		max-width: 500px;
		margin: 0 auto;
		display: flex;
		flex-direction: column;
		gap: 1rem;
	}

	.contact-form input,
	.contact-form textarea {
		padding: 0.9rem 1rem;
		border: 1px solid #ddd;
		border-radius: 8px;
		font-size: 1rem;
		transition: border-color 0.2s ease;
	}

	.contact-form input:focus,
	.contact-form textarea:focus {
		outline: none;
		border-color: #e94560;
	}

	@media (max-width: 768px) {
		.hero {
			padding: 1.5rem;
		}
		h1 {
			font-size: 2.25rem;
		}
		.hero-content {
			margin-top: 3rem;
		}
		.section {
			padding: 2.5rem 1.5rem;
		}
		nav {
			flex-direction: column;
			gap: 1rem;
		}
	}
</style>
