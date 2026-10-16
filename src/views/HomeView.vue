<template>
  <!-- ===== NAVBAR ===== -->
  <nav class="navbar navbar-expand-lg navbar-dark sticky-top">
    <div class="container">
      <!-- Brand Logo -->
      <a class="navbar-brand d-flex align-items-center gap-2 text-decoration-none" href="/">
        <span class="navbar-brand-icon rounded-circle d-inline-flex align-items-center justify-content-center fw-bold text-white flex-shrink-0">R</span>
        <span class="navbar-brand-name fw-bold text-white">RichBrand</span>
      </a>

      <!-- Mobile Toggler -->
      <button
        class="navbar-toggler border-0"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#mainNav"
        aria-controls="mainNav"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>

      <!-- Nav Links -->
      <div class="collapse navbar-collapse" id="mainNav">
        <ul class="navbar-nav mx-auto gap-lg-1">
          <li class="nav-item"><a class="nav-link active nav-pill-link" href="/">Home</a></li>
          <li class="nav-item"><a class="nav-link nav-pill-link" href="#shop">Collection</a></li>
          <li class="nav-item"><a class="nav-link nav-pill-link" href="#story">Our Atelier</a></li>
          <li class="nav-item"><a class="nav-link nav-pill-link" href="#about">About Us</a></li>
          <li class="nav-item"><a class="nav-link nav-pill-link" href="../ecommerce">Ecommerce</a></li>
        </ul>

        <!-- Right Actions -->
        <div class="d-flex align-items-center gap-2 mt-3 mt-lg-0">
          <button class="btn btn-sm rounded-pill text-white icon-nav-btn border" @click="openAuthModal">
            <i class="bi bi-person-circle me-1"></i> Log In
          </button>
          <button class="btn btn-sm rounded-circle d-inline-flex align-items-center justify-content-center text-white icon-nav-btn border" title="Wishlist">
            <i class="bi bi-heart"></i>
          </button>
          <button class="btn btn-sm rounded-circle d-inline-flex align-items-center justify-content-center text-white position-relative icon-nav-btn border" title="Cart" @click="openCartDrawer">
            <i class="bi bi-bag"></i>
            <span class="cart-badge position-absolute top-0 start-100 translate-middle badge rounded-pill text-white d-flex align-items-center justify-content-center">{{ state.cart.length }}</span>
          </button>
        </div>
      </div>
    </div>
  </nav>

  <main>
    <!-- ===== HERO SECTION ===== -->
    <section id="home" class="d-flex align-items-center bg-1">
      <div class="container py-5">
        <div class="row align-items-center g-5 py-5">
          <!-- Hero Text -->
          <div class="col-lg-6 order-2 order-lg-1">
            <span class="d-inline-flex align-items-center gap-2 mb-3 rounded-pill text-primary px-3 py-2 bg-2 border-1">
              <i class="bi bi-stars"></i> Signature Wine Red Edition 2026
            </span>
            <h1 class="fw-bold text-white mb-3 lh-sm">
              Draped in Intoxicating <span class="gradient-text">Bordeaux</span> &amp; Pure Luxury
            </h1>
            <p class="mb-4 lh-lg text-light">
              Experience handcrafted mulberry silk dresses, velvet galas, and bespoke virgin wool
              blazers designed in our signature wine red color palette.
            </p>

            <div class="d-flex flex-wrap gap-3 mb-5">
              <a href="#shop" class="btn rounded-pill btn-wine-primary">
                Explore Collection <i class="bi bi-arrow-right ms-1"></i>
              </a>
              <a href="#story" class="btn rounded-pill fw-medium text-light border px-4 py-2">
                <i class="bi bi-play-circle me-1"></i> Watch Atelier Story
              </a>
            </div>

            <!-- Stats Row -->
            <div class="row row-cols-3 g-3 pt-4 hero-stats-row">
              <div class="col text-center">
                <div class="stat-number fw-bold">12k+</div>
                <div class="stat-label mt-1">Couture Clients</div>
              </div>
              <div class="col text-center">
                <div class="stat-number fw-bold">100%</div>
                <div class="stat-label mt-1">Sustainable Silk</div>
              </div>
              <div class="col text-center">
                <div class="stat-number fw-bold">4.9&#9733;</div>
                <div class="stat-label mt-1">Global Rating</div>
              </div>
            </div>
          </div>

          <!-- Hero Image -->
          <div class="col-lg-6 order-1 order-lg-2">
            <div class="position-relative rounded-4">
              <img
                src="https://images.unsplash.com/photo-1566174053879-31528523f8ae?auto=format&fit=crop&w=900&q=80"
                alt="Wine Red Velvet Gown"
                class="hero-main-img img-fluid rounded-4 w-100 shadow-lg"
              />
              <!-- Floating Card -->
              <div class="hero-floating-card position-absolute d-none d-md-flex align-items-center gap-3 rounded-3 p-3">
                <img
                  src="https://images.unsplash.com/photo-1566174053879-31528523f8ae?auto=format&fit=crop&w=80&q=80"
                  alt="Preview"
                  class="hero-floating-thumb rounded-2 flex-shrink-0"
                />
                <div>
                  <p class="mb-0 fw-semibold text-white hero-floating-title">Velvet Evening Gown</p>
                  <p class="mb-0 hero-floating-subtitle">Hand-stitched Corset</p>
                  <p class="mb-0 fw-bold hero-floating-price">$345.00</p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- ===== FEATURES BAR ===== -->
    <section class="py-5 bg-white features-section border-top border-bottom">
      <div class="container">
        <div class="row row-cols-1 row-cols-sm-2 row-cols-lg-4 g-4">
          <div class="col" v-for="feat in features" :key="feat.title">
            <div class="d-flex align-items-start gap-3 h-100 p-3 rounded-3 feature-hover-card">
              <div class="feature-icon d-flex align-items-center justify-content-center rounded-3 flex-shrink-0">
                <i :class="feat.icon"></i>
              </div>
              <div>
                <h5 class="mb-1 fw-semibold feature-title">{{ feat.title }}</h5>
                <p class="mb-0 feature-desc">{{ feat.desc }}</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- ===== COLLECTION / SHOP SECTION ===== -->
    <section class="py-5 shop-section" id="shop">
      <div class="container">
        <!-- Section Header -->
        <div class="text-center mb-4">
          <span class="section-eyebrow d-block text-uppercase fw-bold mb-1">Curated Wardrobe</span>
          <h2 class="section-heading fw-bold">Signature Wine Red Collection</h2>
        </div>

        <!-- Category Filter Tabs -->
        <div class="d-flex flex-wrap justify-content-center gap-2 mb-5">
          <button
            v-for="tab in tabs"
            :key="tab.value"
            class="btn rounded-pill tab-filter-btn"
            :class="activeTab === tab.value ? 'tab-active' : 'tab-inactive'"
            @click="activeTab = tab.value"
          >
            {{ tab.label }}
          </button>
        </div>

        <!-- Products Grid -->
        <div class="row row-cols-1 row-cols-sm-2 row-cols-lg-3 row-cols-xl-4 g-4">
          <div class="col" v-for="product in filtered" :key="product.id">
            <div class="card h-100 border-0 rounded-3 overflow-hidden shadow-sm product-card">
              <!-- Media -->
              <div class="product-media position-relative overflow-hidden">
                <span v-if="product.isNew" class="badge-new badge rounded-pill position-absolute top-0 start-0 m-2">New</span>
                <span
                  v-if="product.isBestSeller"
                  class="badge-bestseller badge rounded-pill position-absolute start-0 m-2"
                  :class="product.isNew ? 'top-new-offset' : 'top-0'"
                >Best Seller</span>
                <img :src="product.primaryImg" :alt="product.title" class="product-img position-absolute w-100 h-100" loading="lazy" />
                <img :src="product.secondaryImg" :alt="product.title" class="product-img product-img-hover position-absolute w-100 h-100" loading="lazy" />
                <!-- Overlay Actions -->
                <div class="product-overlay-actions d-flex gap-2 position-absolute">
                  <button class="btn btn-sm rounded-circle d-flex align-items-center justify-content-center overlay-action-btn" title="Quick View" @click="openPDP(product.id)">
                    <i class="bi bi-eye"></i>
                  </button>
                  <button class="btn btn-sm rounded-circle d-flex align-items-center justify-content-center overlay-action-btn" title="Wishlist" @click="toggleWishlist(product.id)">
                    <i
                      :class="[state.wishlist.includes(product.id) ? 'bi bi-heart-fill' : 'bi bi-heart', state.wishlist.includes(product.id) ? 'wishlist-active' : '']"
                    ></i>
                  </button>
                </div>
              </div>

              <!-- Body -->
              <div class="card-body p-3">
                <span class="product-category text-uppercase fw-bold">{{ product.category }}</span>
                <h5 class="product-title fw-semibold mt-1 mb-2 product-title-hover" @click="openPDP(product.id)">
                  {{ product.title }}
                </h5>
                <!-- Rating -->
                <div class="d-flex align-items-center gap-1 mb-2">
                  <i class="bi bi-star-fill star-icon" v-for="s in 4" :key="s"></i>
                  <i class="bi bi-star-half star-icon"></i>
                  <small class="text-muted ms-1">({{ product.reviewsCount }})</small>
                </div>
                <!-- Price + Cart -->
                <div class="d-flex align-items-center justify-content-between">
                  <div>
                    <span class="product-price fw-bold">৳{{ product.price.toFixed(2) }}</span>
                    <span class="product-old-price ms-2 text-decoration-line-through">৳{{ product.oldPrice.toFixed(2) }}</span>
                  </div>
                  <button class="btn btn-sm rounded-pill fw-semibold btn-add-cart" @click="quickAddToCart(product.id)">
                    + Cart
                  </button>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- ===== STORY / BRAND BANNER ===== -->
    <section class="py-5 story-section" id="story">
      <div class="container">
        <div class="row align-items-center g-5">
          <!-- Content -->
          <div class="col-lg-6">
            <span class="story-eyebrow d-block text-uppercase fw-bold mb-1">The Atelier Philosophy</span>
            <h2 class="section-heading story-heading fw-bold mt-1 mb-3">Why We Built Our World Around Wine Red</h2>
            <p class="story-body mb-4 lh-lg">
              Wine red is not merely a color; it is a statement of warmth, authority, and sensual
              sophistication. Each garment undergoes meticulous dyeing using organic botanical
              extracts to capture light with rich complexity.
            </p>
            <div class="row g-3 mb-4">
              <div class="col-sm-6">
                <div class="p-3 rounded-3 highlight-box">
                  <h6 class="highlight-box-title fw-bold mb-1">Italian Silk Atelier</h6>
                  <p class="mb-0 highlight-box-desc">Woven in historical mills in Como, Italy for peerless drape.</p>
                </div>
              </div>
              <div class="col-sm-6">
                <div class="p-3 rounded-3 highlight-box">
                  <h6 class="highlight-box-title fw-bold mb-1">Bespoke Tailoring</h6>
                  <p class="mb-0 highlight-box-desc">Precision cut patterns designed for body confidence.</p>
                </div>
              </div>
            </div>
            <a href="#shop" class="btn rounded-pill fw-bold btn-wine-gold">
              Shop Signature Collection <i class="bi bi-arrow-up-right ms-1"></i>
            </a>
          </div>
          <!-- Image -->
          <div class="col-lg-6">
            <img
              src="https://images.unsplash.com/photo-1594938298603-c8148c4dae35?auto=format&fit=crop&w=900&q=80"
              alt="Tailored Wool Blazer Craftsmanship"
              class="story-img img-fluid rounded-4 w-100 shadow-lg"
            />
          </div>
        </div>
      </div>
    </section>

    <!-- ===== ABOUT SECTION ===== -->
    <section class="py-5 about-section" id="about">
      <div class="container">
        <div class="text-center mb-5">
          <span class="section-eyebrow d-block text-uppercase fw-bold mb-1">Our Journey</span>
          <h2 class="section-heading fw-bold mt-1">Reimagining Modern Luxury Fashion</h2>
          <p class="about-intro mx-auto mt-3 lh-lg">
            Founded in 2018, RichBrand Couture emerged from a single desire: to create timeless
            wardrobe mainstays centered on deep burgundy and rich wine tones.
          </p>
        </div>
        <div class="row row-cols-1 row-cols-md-3 g-4">
          <div class="col" v-for="tl in timeline" :key="tl.year">
            <div class="card border-0 rounded-3 shadow-sm text-center p-4 h-100 timeline-card">
              <div class="timeline-year fw-bolder lh-1 mb-2">{{ tl.year }}</div>
              <h5 class="timeline-title fw-bold">{{ tl.title }}</h5>
              <p class="mb-0 lh-lg timeline-desc">{{ tl.desc }}</p>
            </div>
          </div>
        </div>
      </div>
    </section>
  </main>

  <!-- ===== FOOTER ===== -->
  <footer class="pt-5 pb-3 site-footer">
    <div class="container">
      <div class="row g-4 mb-4">
        <!-- Brand -->
        <div class="col-12 col-md-4">
          <a href="#home" class="d-inline-flex align-items-center gap-2 mb-3 text-decoration-none">
            <span class="footer-brand-icon rounded-circle d-inline-flex align-items-center justify-content-center fw-bold text-white">R</span>
            <span class="footer-brand-name fw-bold text-white">RichBrand</span>
          </a>
          <p class="footer-tagline">
            Elevating contemporary wardrobes with signature wine red elegance, sustainable
            craftsmanship, and timeless silhouettes.
          </p>
          <div class="d-flex gap-2 mt-3">
            <a href="#" class="social-btn rounded-circle d-inline-flex align-items-center justify-content-center text-decoration-none" aria-label="Instagram"><i class="bi bi-instagram"></i></a>
            <a href="#" class="social-btn rounded-circle d-inline-flex align-items-center justify-content-center text-decoration-none" aria-label="Pinterest"><i class="bi bi-pinterest"></i></a>
            <a href="#" class="social-btn rounded-circle d-inline-flex align-items-center justify-content-center text-decoration-none" aria-label="Facebook"><i class="bi bi-facebook"></i></a>
            <a href="#" class="social-btn rounded-circle d-inline-flex align-items-center justify-content-center text-decoration-none" aria-label="TikTok"><i class="bi bi-tiktok"></i></a>
          </div>
        </div>
        <!-- Shop -->
        <div class="col-6 col-md-2">
          <h6 class="footer-col-heading text-uppercase fw-bold mb-3">Shop</h6>
          <ul class="list-unstyled d-flex flex-column gap-2">
            <li><a href="#shop" class="footer-link">Evening Dresses</a></li>
            <li><a href="#shop" class="footer-link">Wool Blazers</a></li>
            <li><a href="#shop" class="footer-link">Silk Slips</a></li>
            <li><a href="#shop" class="footer-link">Cashmere Coats</a></li>
          </ul>
        </div>
        <!-- Services -->
        <div class="col-6 col-md-2">
          <h6 class="footer-col-heading text-uppercase fw-bold mb-3">Services</h6>
          <ul class="list-unstyled d-flex flex-column gap-2">
            <li><a href="#about" class="footer-link">Our Story</a></li>
            <li><a href="#" class="footer-link" @click.prevent="openAuthModal">My Account</a></li>
            <li><a href="#" class="footer-link">Size Guide</a></li>
            <li><a href="#" class="footer-link">Shipping &amp; Returns</a></li>
          </ul>
        </div>
        <!-- Newsletter -->
        <div class="col-12 col-md-4">
          <h6 class="footer-col-heading text-uppercase fw-bold mb-3">Stay Connected</h6>
          <p class="footer-tagline mb-3">
            Subscribe for private trunk show invites and get 10% off your first order.
          </p>
          <div class="input-group">
            <input
              type="email"
              class="form-control newsletter-input"
              placeholder="Enter your email..."
            />
            <button class="btn btn-wine-primary newsletter-btn btn-sm" @click="showToast('Subscribed!')">
              Join
            </button>
          </div>
        </div>
      </div>
      <!-- Bottom -->
      <div class="footer-bottom d-flex flex-column flex-sm-row align-items-center justify-content-between gap-2 pt-4">
        <p class="mb-0 small">&#169; 2026 RichBrand Couture. All rights reserved.</p>
        <div class="d-flex gap-3">
          <span class="small footer-policy-link">Privacy Policy</span>
          <span class="small footer-policy-link">Terms of Service</span>
          <span class="small footer-policy-link">Cookies</span>
        </div>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  name: 'HomeView',

  data() {
    return {
      activeTab: 'all',

      tabs: [
        { label: 'All Designs', value: 'all' },
        { label: 'Best Sellers 🔥', value: 'bestsellers' },
        { label: 'New Arrivals ✨', value: 'new' },
        { label: 'Eveningwear', value: 'eveningwear' },
        { label: 'Wool & Outerwear', value: 'outerwear' },
      ],

      features: [
        { icon: 'bi bi-truck', title: 'Express Worldwide Shipping', desc: 'Complimentary shipping on orders over $150' },
        { icon: 'bi bi-tree', title: 'Sustainable Craftsmanship', desc: 'Ethically sourced organic silk & virgin wool' },
        { icon: 'bi bi-arrow-repeat', title: '30-Day Atelier Returns', desc: 'Hassle-free size exchanges and returns' },
        { icon: 'bi bi-gem', title: '24/7 Private Concierge', desc: 'Personal styling assistance on call' },
      ],

      timeline: [
        { year: '2018', title: 'The Atelier Genesis', desc: 'Started as a private custom dressmaking studio specializing in deep red silks and hand-tailored tuxedos.' },
        { year: '2021', title: 'Runway Debut', desc: "Unveiled the 'Monochrome Wine' ready-to-wear runway collection in Paris, receiving international acclaim." },
        { year: '2026', title: 'Sustainable Luxury Era', desc: 'Transitioned to 100% certified organic mulberry silk, eco-friendly dye processes, and zero-waste packaging.' },
      ],

      state: {
        wishlist: [],
        cart: [],
      },

      products: [
        {
          id: 1,
          title: 'Velvet Evening Gown',
          category: 'Eveningwear',
          price: 345.00,
          oldPrice: 420.00,
          reviewsCount: 218,
          isNew: true,
          isBestSeller: false,
          tags: ['eveningwear', 'new'],
          primaryImg: 'https://images.unsplash.com/photo-1566174053879-31528523f8ae?auto=format&fit=crop&w=600&q=80',
          secondaryImg: 'https://images.unsplash.com/photo-1515886657613-9f3515b0c78f?auto=format&fit=crop&w=600&q=80',
        },
        {
          id: 2,
          title: 'Bordeaux Wool Blazer',
          category: 'Outerwear',
          price: 289.00,
          oldPrice: 360.00,
          reviewsCount: 134,
          isNew: false,
          isBestSeller: true,
          tags: ['outerwear', 'bestsellers'],
          primaryImg: 'https://images.unsplash.com/photo-1594938298603-c8148c4dae35?auto=format&fit=crop&w=600&q=80',
          secondaryImg: 'https://images.unsplash.com/photo-1594938298603-c8148c4dae35?auto=format&fit=crop&w=600&q=80',
        },
        {
          id: 3,
          title: 'Mulberry Silk Slip Dress',
          category: 'Eveningwear',
          price: 198.00,
          oldPrice: 260.00,
          reviewsCount: 92,
          isNew: true,
          isBestSeller: true,
          tags: ['eveningwear', 'new', 'bestsellers'],
          primaryImg: 'https://images.unsplash.com/photo-1515886657613-9f3515b0c78f?auto=format&fit=crop&w=600&q=80',
          secondaryImg: 'https://images.unsplash.com/photo-1566174053879-31528523f8ae?auto=format&fit=crop&w=600&q=80',
        },
        {
          id: 4,
          title: 'Cashmere Long Coat',
          category: 'Outerwear',
          price: 475.00,
          oldPrice: 580.00,
          reviewsCount: 67,
          isNew: false,
          isBestSeller: true,
          tags: ['outerwear', 'bestsellers'],
          primaryImg: 'https://images.unsplash.com/photo-1539109136881-3be0616acf4b?auto=format&fit=crop&w=600&q=80',
          secondaryImg: 'https://images.unsplash.com/photo-1539109136881-3be0616acf4b?auto=format&fit=crop&w=600&q=80',
        },
        {
          id: 5,
          title: 'Wine Red Mini Dress',
          category: 'Eveningwear',
          price: 155.00,
          oldPrice: 200.00,
          reviewsCount: 310,
          isNew: true,
          isBestSeller: false,
          tags: ['eveningwear', 'new'],
          primaryImg: 'https://images.unsplash.com/photo-1496747611176-843222e1e57c?auto=format&fit=crop&w=600&q=80',
          secondaryImg: 'https://images.unsplash.com/photo-1496747611176-843222e1e57c?auto=format&fit=crop&w=600&q=80',
        },
        {
          id: 6,
          title: 'Draped Satin Blouse',
          category: 'Tops',
          price: 120.00,
          oldPrice: 155.00,
          reviewsCount: 45,
          isNew: false,
          isBestSeller: false,
          tags: ['all'],
          primaryImg: 'https://images.unsplash.com/photo-1525507119028-ed4c629a60a3?auto=format&fit=crop&w=600&q=80',
          secondaryImg: 'https://images.unsplash.com/photo-1525507119028-ed4c629a60a3?auto=format&fit=crop&w=600&q=80',
        },
        {
          id: 7,
          title: 'Corset Brocade Skirt',
          category: 'Eveningwear',
          price: 210.00,
          oldPrice: 280.00,
          reviewsCount: 88,
          isNew: false,
          isBestSeller: true,
          tags: ['eveningwear', 'bestsellers'],
          primaryImg: 'https://images.unsplash.com/photo-1549062572-544a64fb0c56?auto=format&fit=crop&w=600&q=80',
          secondaryImg: 'https://images.unsplash.com/photo-1549062572-544a64fb0c56?auto=format&fit=crop&w=600&q=80',
        },
        {
          id: 8,
          title: 'Virgin Wool Trench',
          category: 'Outerwear',
          price: 390.00,
          oldPrice: 480.00,
          reviewsCount: 52,
          isNew: true,
          isBestSeller: false,
          tags: ['outerwear', 'new'],
          primaryImg: 'https://images.unsplash.com/photo-1520975916090-3105956dac38?auto=format&fit=crop&w=600&q=80',
          secondaryImg: 'https://images.unsplash.com/photo-1520975916090-3105956dac38?auto=format&fit=crop&w=600&q=80',
        },
      ],
    }
  },

  computed: {
    filtered() {
      if (this.activeTab === 'all') return this.products
      return this.products.filter(p => p.tags.includes(this.activeTab))
    },
  },

  methods: {
    openAuthModal() { alert('Connect your auth component here.') },
    openCartDrawer() { alert('Connect your cart component here.') },
    openPDP(id) { alert(`Product detail page for ID: ${id}`) },
    toggleWishlist(id) {
      const idx = this.state.wishlist.indexOf(id)
      if (idx === -1) this.state.wishlist.push(id)
      else this.state.wishlist.splice(idx, 1)
    },
    quickAddToCart(id) {
      this.state.cart.push(id)
      this.showToast('Added to cart!')
    },
    showToast(msg) { alert(msg) },
  },
}
</script>

<style scoped>
.bg-1{
  background:linear-gradient(135deg,#1a1a2e 0%,#16213e 60%,#2a0a12 100%);
}
.bg-2{
  background:#7b1f2e2e;
}
.border-1{
  border:1px solid #7b1f2e80;
}
.navbar{
  background:#1a1a2ef7;
  backdrop-filter:blur(14px);
  border-bottom:1px solid #7b1f2e59;
  padding:.85rem 0;z-index:1030;
}
.navbar-btn{
  width:36px;
  height:36px;
  border:1px solid #ffffff40;
  background:transparent;
  background:linear-gradient(135deg,#a0263a,#5a1520);
}
/* Gradient text (hero heading accent) */
.gradient-text {
  background: linear-gradient(135deg, #a0263a, #c9a84c);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

/* Branded primary button */
.btn-wine-primary {
  background: linear-gradient(135deg, #a0263a, #5a1520);
  color: #fff !important;
  border: none;
  padding: .75rem 1.75rem;
  font-weight: 600;
  font-family: 'Poppins', sans-serif;
  font-size: .9rem;
  box-shadow: 0 6px 20px rgba(123,31,46,0.4);
  transition: all .3s;
}
.btn-wine-primary:hover {
  transform: translateY(-2px);
  box-shadow: 0 10px 30px rgba(123,31,46,0.55);
  color: #fff !important;
}

/* Gold button */
.btn-wine-gold {
  background: linear-gradient(135deg, #c9a84c, #e2c57e);
  color: #1a1a2e !important;
  border: none;
  padding: .75rem 1.75rem;
  font-size: .9rem;
  transition: all .3s;
}
.btn-wine-gold:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 24px rgba(201,168,76,0.45);
  color: #1a1a2e !important;
}

/* Nav pill links */
.nav-pill-link {
  font-family: 'Poppins', sans-serif;
  font-size: .875rem;
  font-weight: 500;
  color: rgba(255,255,255,0.75) !important;
  padding: .45rem .9rem !important;
  border-radius: 50px;
  transition: all .3s;
}
.nav-pill-link:hover,
.nav-pill-link.active {
  color: #fff !important;
  background: rgba(123,31,46,0.28);
}

/* Icon nav buttons */
.icon-nav-btn { transition: all .3s; }
.icon-nav-btn:hover {
  background: #7b1f2e !important;
  border-color: #7b1f2e !important;
}

/* Feature card hover */
.feature-hover-card { transition: all .3s; }
.feature-hover-card:hover { background: #fdf4f6; }

/* Tab filter buttons */
.tab-filter-btn {
  font-family: 'Poppins', sans-serif;
  font-size: .82rem;
  font-weight: 500;
  transition: all .3s;
}
.tab-inactive { color: #888; background: #fff; border: 1px solid #e2e2e2; }
.tab-inactive:hover { border-color: #a0263a; color: #7b1f2e; }
.tab-active { background: #7b1f2e !important; border-color: #7b1f2e !important; color: #fff !important; }

/* Product card lift */
.product-card { transition: all .32s; }
.product-card:hover { transform: translateY(-7px); box-shadow: 0 18px 44px rgba(0,0,0,0.13) !important; }

/* Product image hover swap */
.product-img { transition: opacity .45s ease, transform .45s ease; }
.product-img-hover { opacity: 0; }
.product-media:hover .product-img:not(.product-img-hover) { opacity: 0; transform: scale(1.05); }
.product-media:hover .product-img-hover { opacity: 1; transform: scale(1.05); }

/* Product overlay actions */
.product-overlay-actions { opacity: 0; transition: all .3s; }
.product-media:hover .product-overlay-actions { opacity: 1; }

/* Overlay action button */
.overlay-action-btn { transition: all .25s; cursor: pointer; }
.overlay-action-btn:hover { background: #7b1f2e !important; color: #fff !important; }

/* Product title hover */
.product-title-hover { transition: color .2s; }
.product-title-hover:hover { color: #7b1f2e !important; }

/* Story highlight boxes */
.highlight-box {
  background: rgba(255,255,255,0.05);
  border: 1px solid rgba(255,255,255,0.12);
  transition: all .3s;
}
.highlight-box:hover { background: rgba(123,31,46,0.18); border-color: rgba(123,31,46,0.4); }

/* Timeline card hover */
.timeline-card { transition: all .3s; border-top: 4px solid #7b1f2e; }
.timeline-card:hover { transform: translateY(-6px); box-shadow: 0 14px 36px rgba(0,0,0,0.13) !important; }

/* Social buttons */
.social-btn { transition: all .25s; }
.social-btn:hover { background: #7b1f2e !important; color: #fff !important; }

/* Footer links */
.footer-link { transition: all .25s; }
.footer-link:hover { color: #a0263a !important; padding-left: 4px; }

/* Footer policy links */
.footer-policy-link { cursor: pointer; transition: color .2s; }
.footer-policy-link:hover { color: rgba(255,255,255,0.7); }

/* Newsletter input */
.newsletter-input::placeholder { color: rgba(255,255,255,0.35); }
.newsletter-input:focus {
  background: rgba(255,255,255,0.1) !important;
  border-color: #a0263a !important;
  box-shadow: none !important;
  color: #fff !important;
}

/* =============================================
   NAVBAR BRAND
   ============================================= */
.navbar-brand-icon {
  width: 36px;
  height: 36px;
  background: linear-gradient(135deg, #a0263a, #5a1520);
  font-size: 1rem;
  font-family: 'Poppins', sans-serif;
}
.navbar-brand-name {
  font-family: 'Poppins', sans-serif;
  font-size: 1.2rem;
}
.cart-badge {
  font-size: .65rem;
  min-width: 16px;
  height: 16px;
  background: #a0263a;
}

/* =============================================
   HERO STATS
   ============================================= */
.hero-stats-row {
  border-top: 1px solid rgba(255, 255, 255, 0.12);
}
.stat-number {
  font-family: 'Poppins', sans-serif;
  font-size: 1.5rem;
  color: #a0263a;
}
.stat-label {
  font-size: .75rem;
  color: rgba(255, 255, 255, 0.5);
}
.hero-main-img {
  height: 520px;
  object-fit: cover;
}
.hero-floating-card {
  bottom: 2rem;
  left: -2rem;
  background: rgba(22, 33, 62, 0.94);
  backdrop-filter: blur(16px);
  border: 1px solid rgba(123, 31, 46, 0.4);
  box-shadow: 0 12px 40px rgba(0, 0, 0, 0.3);
  min-width: 220px;
}
.hero-floating-thumb {
  width: 52px;
  height: 52px;
  object-fit: cover;
}
.hero-floating-title {
  font-family: 'Poppins', sans-serif;
  font-size: .85rem;
}
.hero-floating-subtitle {
  font-size: .72rem;
  color: rgba(255, 255, 255, 0.5);
}
.hero-floating-price {
  font-size: .88rem;
  color: #a0263a;
}

/* =============================================
   FEATURES BAR
   ============================================= */
.features-section { border-color: #f0e8ea !important; }
.feature-icon {
  width: 50px;
  height: 50px;
  background: rgba(123, 31, 46, 0.08);
  font-size: 1.3rem;
  color: #7b1f2e;
}
.feature-title {
  font-family: 'Poppins', sans-serif;
  font-size: .88rem;
  color: #1a1a2e;
}
.feature-desc {
  font-size: .8rem;
  color: #888;
}

/* =============================================
   SHOP SECTION
   ============================================= */
.shop-section { background: #f9f7f8; }
.section-eyebrow {
  font-family: 'Poppins', sans-serif;
  font-size: .75rem;
  letter-spacing: 2.5px;
  color: #7b1f2e;
}
.section-heading {
  font-family: 'Poppins', sans-serif;
  font-size: clamp(1.5rem, 3vw, 2.2rem);
  color: #1a1a2e;
}
.product-media {
  height: 280px;
  background: #f5f0f1;
}
.product-img { object-fit: cover; }
.badge-new { background: #7b1f2e; font-size: .68rem; }
.badge-bestseller { background: #c9a84c; color: #1a1a2e; font-size: .68rem; }
.top-new-offset { top: 2rem; }
.overlay-action-btn {
  width: 36px;
  height: 36px;
  background: rgba(255, 255, 255, 0.94);
  border: none;
  font-size: .9rem;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.14);
}
.wishlist-active { color: #7b1f2e; }
.product-overlay-actions { bottom: .75rem; right: .75rem; }
.product-category { font-size: .7rem; letter-spacing: 1px; color: #7b1f2e; }
.product-title {
  font-family: 'Poppins', sans-serif;
  font-size: .93rem;
  color: #1a1a2e;
  line-height: 1.3;
  cursor: pointer;
}
.star-icon { color: #c9a84c; font-size: .72rem; }
.product-price { font-family: 'Poppins', sans-serif; font-size: .98rem; color: #7b1f2e; }
.product-old-price { font-size: .8rem; color: #bbb; }
.btn-add-cart {
  background: #7b1f2e;
  color: #fff;
  border: none;
  font-size: .75rem;
  padding: .38rem .85rem;
  transition: all .25s;
}
.btn-add-cart:hover { background: #a0263a; color: #fff; }

/* =============================================
   STORY SECTION
   ============================================= */
.story-section { background: linear-gradient(135deg, #1a1a2e, #16213e); }
.story-eyebrow {
  font-family: 'Poppins', sans-serif;
  font-size: .75rem;
  letter-spacing: 2.5px;
  color: #c9a84c;
}
.story-heading { font-size: clamp(1.5rem, 3vw, 2.2rem); color: #fff; }
.story-body { font-family: 'Poppins', sans-serif; color: rgba(255, 255, 255, 0.65); }
.story-img { height: 460px; object-fit: cover; }
.highlight-box-title { font-family: 'Poppins', sans-serif; font-size: .9rem; color: #fff; }
.highlight-box-desc { font-size: .8rem; color: rgba(255, 255, 255, 0.58); }

/* =============================================
   ABOUT SECTION
   ============================================= */
.about-section { background: #f9f7f8; }
.about-intro { max-width: 600px; color: rgba(0, 0, 0, 0.55); font-family: 'Poppins', sans-serif; }
.timeline-year { font-family: 'Poppins', sans-serif; font-size: 2.2rem; color: #a0263a; }
.timeline-title { font-family: 'Poppins', sans-serif; font-size: 1rem; color: #1a1a2e; }
.timeline-desc { color: rgba(0, 0, 0, 0.55); font-family: 'Poppins', sans-serif; }

/* =============================================
   FOOTER
   ============================================= */
.site-footer { background: #1a1a2e; color: rgba(255, 255, 255, 0.65); }
.footer-brand-icon {
  width: 36px;
  height: 36px;
  background: linear-gradient(135deg, #a0263a, #5a1520);
  font-size: 1rem;
  font-family: 'Poppins', sans-serif;
}
.footer-brand-name { font-family: 'Poppins', sans-serif; font-size: 1.2rem; }
.footer-tagline { font-size: .85rem; color: rgba(255, 255, 255, 0.52); line-height: 1.7; }
.footer-col-heading {
  font-family: 'Poppins', sans-serif;
  font-size: .82rem;
  color: #fff;
  letter-spacing: 1px;
}
.footer-link {
  font-size: .84rem;
  color: rgba(255, 255, 255, 0.52);
  text-decoration: none;
}
.footer-bottom {
  border-top: 1px solid rgba(255, 255, 255, 0.1);
  color: rgba(255, 255, 255, 0.38);
}
.newsletter-input {
  background: rgba(255, 255, 255, 0.07);
  border: 1px solid rgba(255, 255, 255, 0.14);
  color: #fff;
  font-size: .84rem;
}
.newsletter-btn { border-radius: 0 50px 50px 0 !important; }
.social-btn {
  width: 36px;
  height: 36px;
  background: rgba(255, 255, 255, 0.08);
  color: rgba(255, 255, 255, 0.65);
  font-size: .88rem;
}
</style>
