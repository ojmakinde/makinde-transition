<template>
  <div class="app">
    <!-- Hero Section -->
    <header class="hero">
      <div class="hero-inner">
        <div class="hero-text">
          <p class="hero-eyebrow">The Transition</p>
          <h1 class="hero-title">Policy for Progress</h1>
          <p class="hero-description">
            Something nicer than 40 acres and a mule. Real, systemic change.
          </p>
          <p class="hero-campaign">Makinde for President 2028</p>
        </div>
        <div class="hero-photo">
          <img 
            src="/candidate-photo.jpg" 
            alt="Makinde - Presidential Candidate" 
            @error="imageError = true"
            v-show="!imageError"
          />
          <div class="photo-placeholder" v-show="imageError">
            <span>Add your photo to<br/>public/candidate-photo.jpg</span>
          </div>
        </div>
      </div>
    </header>

    <!-- Quote Section -->
    <section class="quote-section">
      <div class="container">
        <blockquote class="main-quote">
          <p>
            Before, black excellence was destroyed through physical violence.
          </p>
          <p>
            Today, black excellence is destroyed through policy.
          </p>
        </blockquote>
        <p class="quote-tagline">
          If our problems are systemic, our solutions must be systemic.
        </p>
      </div>
    </section>

    <!-- Stats Section -->
    <section class="stats-section">
      <div class="container">
        <h2 class="section-eyebrow">The Reality</h2>
        <h3 class="section-title">What <span class="tooltip-trigger">Redlining<span class="tooltip">The government literally drew red lines around Black neighborhoods and told banks: don't invest here. They listened. For 50 years.</span></span> Built</h3>
        <div class="stats-grid">
          <div class="stat-item">
            <span class="stat-number">$23B</span>
            <span class="stat-label">Annual funding gap between white and nonwhite school districts</span>
          </div>
          <div class="stat-item">
            <span class="stat-number">4×</span>
            <span class="stat-label">Higher odds of hospital closure in Black neighborhoods</span>
          </div>
          <div class="stat-item">
            <span class="stat-number">60%</span>
            <span class="stat-label">Black children living in neighborhoods without sidewalks, parks, or rec centers</span>
          </div>
        </div>
      </div>
    </section>

    <!-- Intro Section -->
    <section class="intro-section">
      <div class="container">
        <h2 class="section-eyebrow">The Approach</h2>
        <h3 class="section-title">Policy Implementation</h3>
        <p class="intro-text">
          Our revolutionaries died to show us change was possible. 
          The best way to honor that sacrifice is to finish the work.
          We must immortalize change through policy that outlasts any one of us.
        </p>
      </div>
    </section>

    <!-- Policy Sections -->
    <section class="policies-section">
      <div class="container">
        <h2 class="section-eyebrow">The Policies</h2>
        <h3 class="section-title">Structural Solutions</h3>
        <div class="policy-list">
          <PolicySection
            v-for="section in policySections"
            :key="section.id"
            :section="section"
          />
        </div>
      </div>
    </section>

    <!-- Sources Section -->
    <section class="sources-section">
      <div class="container">
        <h2 class="section-eyebrow">The Research</h2>
        <h3 class="section-title">Sources</h3>
        <ul class="sources-list">
           <li>
            <a href="https://www.transition2025.com/" target="_blank" rel="noopener noreferrer">
              Transition2025 — Inspiration behind the styling of this website.
            </a>
          </li>
          <li>
            <a href="https://www.ncbi.nlm.nih.gov/books/NBK578001/" target="_blank" rel="noopener noreferrer">
              NCBI — Impact of Finances on the Educational Pipeline ($23B funding gap)
            </a>
          </li>
          <li>
            <a href="https://wordinblack.com/2024/01/black-kids-underfunded-public-schools-inequality-factories/" target="_blank" rel="noopener noreferrer">
              Word In Black — Black Students 3.5× More Likely in Underfunded Districts
            </a>
          </li>
          <li>
            <a href="https://biologicalsciences.uchicago.edu/news/hospital-closure-inequality" target="_blank" rel="noopener noreferrer">
              UChicago — Hospital Closures 4× More Likely in Black Communities
            </a>
          </li>
          <li>
            <a href="https://pmc.ncbi.nlm.nih.gov/articles/PMC11144480/" target="_blank" rel="noopener noreferrer">
              PMC — Hospital Closure and Racial/Ethnic Composition
            </a>
          </li>
          <li>
            <a href="https://nlihc.org/resource/study-shows-most-black-children-live-neighborhoods-lacking-amenities-associated-child" target="_blank" rel="noopener noreferrer">
              NLIHC — 60% of Black Children Lack Neighborhood Amenities
            </a>
          </li>
          <li>
            <a href="https://www.audubon.org/news/whiter-neighborhoods-get-more-park-space-new-report-shows" target="_blank" rel="noopener noreferrer">
              Trust for Public Land — 44% Less Park Space in Communities of Color
            </a>
          </li>
          <li>
            <a href="https://www.nationalgeographic.com/science/article/how-nature-deprived-neighborhoods-impact-health-people-of-color" target="_blank" rel="noopener noreferrer">
              National Geographic — Communities of Color 3× More Likely in Nature-Deprived Areas
            </a>
          </li>
          <li>
            <a href="https://www.kff.org/racial-equity-and-health-policy/key-data-on-health-and-health-care-by-race-and-ethnicity/" target="_blank" rel="noopener noreferrer">
              KFF — Key Data on Health and Health Care by Race and Ethnicity
            </a>
          </li>
        </ul>
      </div>
    </section>

    <!-- Footer -->
    <footer class="footer">
      <div class="container">
        <p class="footer-text">Makinde Transition — Built for Progress</p>
      </div>
    </footer>
  </div>
</template>

<script>
import PolicySection from './components/PolicySection.vue'

export default {
  name: 'App',
  components: {
    PolicySection
  },
  data() {
    return {
      imageError: false,
      policySections: [
        {
          id: 'education',
          title: 'Education',
          subtitle: 'Decouple School Funding from Property Taxes',
          content: {
            problem: `School funding is tied to property taxes. People in poorer areas automatically get worse teachers, and Black teachers who may be interested in teaching and focusing on Black students may ultimately have to shift focus to schools in more affluent areas with fewer Black students. Our talent is quite literally getting priced out.`,
            solution: `Decouple school funding from property taxes and redirect funding to ensure equitable distribution of resources. Implement state-level funding formulas that allocate resources based on student need rather than local wealth. This ensures that all students, regardless of their zip code, have access to quality education and dedicated teachers who understand their needs.`,
            impact: `Better education for your children. Every child deserves access to quality teachers and resources, not just those in affluent neighborhoods. When we fund schools equitably, we invest in the future of every community.`
          }
        },
        {
          id: 'healthcare',
          title: 'Healthcare',
          subtitle: 'Eliminate Employment-Based Access Barriers',
          content: {
            problem: `Poverty is closely correlated with poor health outcomes. Black people have a 29% five-year mortality rate from heart attacks compared to 18% for White patients. Black maternal mortality is the highest in the nation at 69.9 deaths per 100,000 live births. Access to life-saving care should NOT be dependent on quality of employment.`,
            solution: `Expand Medicaid in all states. Currently 10 states have not expanded, and the three states with the largest Black populations (Texas, Florida, Georgia) are among them. Implement community health clinics in underserved areas for young people, increase funding for preventative care programs, and address the shortage of healthcare facilities in Black neighborhoods.`,
            impact: `Proportionate funding for people. Healthcare is a human right, not a privilege tied to employment or economic status. When we ensure access to care, we help people choose better. We drop the rate of young pregnancies and increase the quality of the lives people lead.`
          }
        },
        {
          id: 'built-environment',
          title: 'Built Environment',
          subtitle: 'Invest in Community Infrastructure',
          content: {
            problem: `60% of Black children live in neighborhoods lacking sidewalks, parks, recreational centers, and libraries. Predominantly white neighborhoods have 44% more park space per resident. That historical disinvestment is visible today in crumbling sidewalks, missing streetlights, and absent greenspace.`,
            solution: `Invest in development of sidewalks and bike lanes. Incentivize greenspace development, restoration of vacant lots, and rehabilitation of older buildings through tax and zoning structures. Expand public transportation routes to connect underserved neighborhoods.`,
            impact: `Stronger foundations for community. When neighborhoods have safe streets to walk, parks to gather, and infrastructure that works, children develop better and build stronger communities.`
          }
        }
      ]
    }
  }
}
</script>

<style scoped>
.app {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}

/* Hero Section */
.hero {
  background: var(--primary-color);
  color: white;
  padding: 100px 24px;
}

.hero-inner {
  max-width: 1200px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 80px;
  align-items: center;
}

.hero-text {
  text-align: left;
}

.hero-eyebrow {
  font-size: 1rem;
  font-weight: 500;
  text-transform: uppercase;
  letter-spacing: 0.15em;
  margin-bottom: 24px;
  opacity: 0.85;
}

.hero-title {
  font-size: clamp(2.5rem, 5vw, 4rem);
  font-weight: 700;
  margin-bottom: 24px;
  letter-spacing: -0.03em;
  line-height: 1.1;
}

.hero-description {
  font-size: 1.25rem;
  font-weight: 400;
  opacity: 0.9;
  line-height: 1.6;
  margin-bottom: 32px;
}

.hero-campaign {
  display: inline-block;
  font-size: 1rem;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.1em;
  padding: 14px 28px;
  border: 2px solid rgba(255,255,255,0.8);
  border-radius: 4px;
  margin: 0;
}

.hero-photo {
  display: flex;
  justify-content: center;
}

.hero-photo img {
  width: 100%;
  max-width: 400px;
  aspect-ratio: 4 / 5;
  object-fit: cover;
  border-radius: 8px;
  box-shadow: 0 25px 50px rgba(0, 0, 0, 0.4);
}

.photo-placeholder {
  width: 100%;
  max-width: 400px;
  aspect-ratio: 4 / 5;
  border-radius: 8px;
  border: 3px dashed rgba(255,255,255,0.3);
  background: rgba(255,255,255,0.05);
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  padding: 24px;
}

.photo-placeholder span {
  font-size: 1rem;
  opacity: 0.5;
  line-height: 1.6;
}

/* Quote Section */
.quote-section {
  background: var(--bg-light);
  padding: 100px 24px;
  border-bottom: 1px solid var(--border-color);
}

.main-quote {
  max-width: 900px;
  margin: 0 auto 32px;
  padding: 0;
}

.main-quote p {
  font-size: clamp(1.25rem, 2.5vw, 1.75rem);
  line-height: 1.7;
  color: var(--text-color);
  font-weight: 400;
  font-style: italic;
  text-align: center;
}

.quote-tagline {
  font-size: 1.25rem;
  font-weight: 600;
  color: var(--primary-color);
  text-align: center;
  margin: 0;
}

/* Stats Section */
.stats-section {
  background: white;
  padding: 100px 24px;
  border-bottom: 1px solid var(--border-color);
}

.section-eyebrow {
  font-size: 0.875rem;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.15em;
  color: var(--accent-color);
  margin-bottom: 16px;
  text-align: center;
}

.section-title {
  font-size: clamp(2rem, 5vw, 3rem);
  font-weight: 700;
  color: var(--primary-color);
  margin-bottom: 60px;
  text-align: center;
  letter-spacing: -0.02em;
  line-height: 1.2;
}

/* Tooltip */
.tooltip-trigger {
  position: relative;
  border-bottom: 2px dotted var(--accent-color);
  cursor: help;
  transition: var(--transition);
}

.tooltip-trigger:hover {
  color: var(--accent-color);
}

.tooltip {
  position: absolute;
  bottom: calc(100% + 12px);
  left: 50%;
  transform: translateX(-50%);
  width: 320px;
  padding: 16px 20px;
  background: var(--primary-color);
  color: white;
  font-size: 0.95rem;
  font-weight: 400;
  line-height: 1.6;
  letter-spacing: 0;
  border-radius: 8px;
  box-shadow: 0 10px 40px rgba(0, 0, 0, 0.2);
  opacity: 0;
  visibility: hidden;
  transition: opacity 0.25s ease, visibility 0.25s ease;
  z-index: 100;
  pointer-events: none;
}

.tooltip::after {
  content: '';
  position: absolute;
  top: 100%;
  left: 50%;
  transform: translateX(-50%);
  border: 8px solid transparent;
  border-top-color: var(--primary-color);
}

.tooltip-trigger:hover .tooltip {
  opacity: 1;
  visibility: visible;
}

.stats-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 48px;
  max-width: 1100px;
  margin: 0 auto;
}

.stat-item {
  text-align: center;
}

.stat-number {
  display: block;
  font-size: clamp(3rem, 6vw, 4.5rem);
  font-weight: 700;
  color: var(--primary-color);
  line-height: 1;
  margin-bottom: 16px;
  letter-spacing: -0.02em;
}

.stat-label {
  font-size: 1rem;
  color: var(--text-light);
  line-height: 1.5;
  max-width: 280px;
  margin: 0 auto;
}

/* Intro Section */
.intro-section {
  background: var(--primary-color);
  color: white;
  padding: 100px 24px;
  text-align: center;
}

.intro-section .section-eyebrow {
  color: rgba(255, 255, 255, 0.7);
}

.intro-section .section-title {
  color: white;
  margin-bottom: 40px;
}

.intro-text {
  font-size: 1.35rem;
  max-width: 700px;
  margin: 0 auto 32px;
  line-height: 1.7;
  opacity: 0.9;
}

.intro-highlight {
  font-size: 1.75rem;
  font-weight: 700;
  margin: 0;
  letter-spacing: -0.01em;
}

/* Policies Section */
.policies-section {
  background: white;
  padding: 100px 24px;
}

.policy-list {
  max-width: 1000px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  gap: 0;
}

/* Sources Section */
.sources-section {
  background: var(--bg-light);
  padding: 100px 24px;
  border-top: 1px solid var(--border-color);
}

.sources-list {
  list-style: none;
  padding: 0;
  max-width: 800px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.sources-list li {
  padding: 0;
}

.sources-list a {
  font-size: 1.1rem;
  color: var(--primary-color);
  text-decoration: none;
  transition: var(--transition);
  display: inline-block;
  border-bottom: 2px solid transparent;
}

.sources-list a:hover {
  color: var(--accent-color);
  border-bottom-color: var(--accent-color);
}

/* Footer */
.footer {
  background: var(--primary-color);
  color: white;
  padding: 60px 24px;
  text-align: center;
}

.footer-text {
  font-size: 1rem;
  opacity: 0.8;
  margin: 0;
}

/* Responsive */
@media (max-width: 900px) {
  .hero-inner {
    grid-template-columns: 1fr;
    gap: 50px;
    text-align: center;
  }

  .hero-text {
    text-align: center;
    order: 2;
  }

  .hero-photo {
    order: 1;
  }

  .hero-photo img,
  .photo-placeholder {
    max-width: 280px;
  }
}

@media (max-width: 768px) {
  .hero {
    padding: 80px 20px 60px;
  }

  .hero-campaign {
    padding: 12px 20px;
    font-size: 0.9rem;
  }

  .quote-section,
  .stats-section,
  .intro-section,
  .policies-section,
  .sources-section {
    padding: 70px 20px;
  }

  .section-title {
    margin-bottom: 40px;
  }

  .stats-grid {
    gap: 40px;
  }

  .tooltip {
    width: 260px;
    font-size: 0.875rem;
    padding: 14px 16px;
  }
}
</style>
