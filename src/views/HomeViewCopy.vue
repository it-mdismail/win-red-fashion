<template>
  <!-- ===== NAVBAR ===== -->
  <nav class="navbar navbar-expand-lg navbar-dark rb-navbar sticky-top">
    <div class="container">
      <!-- Brand Logo -->
      <a class="navbar-brand d-flex align-items-center gap-2" href="#home">
        <span class="rb-logo-mark">R</span>
        <span class="rb-logo-text">RichBrand</span>
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
          <li class="nav-item"><a class="nav-link active" href="/">Home</a></li>
          <li class="nav-item"><a class="nav-link" href="#shop">Collection</a></li>
          <li class="nav-item"><a class="nav-link" href="#story">Our Atelier</a></li>
          <li class="nav-item"><a class="nav-link" href="#about">About Us</a></li>
        </ul>

        <!-- Right Actions -->
        <div class="d-flex align-items-center gap-2 mt-3 mt-lg-0">
          <button class="btn rb-btn-outline btn-sm" @click="openAuthModal">
            <i class="bi bi-person-circle me-1"></i> Log In
          </button>
          <button class="rb-icon-btn" title="Wishlist">
            <i class="bi bi-heart"></i>
          </button>
          <button class="rb-icon-btn position-relative" title="Cart" @click="openCartDrawer">
            <i class="bi bi-bag"></i>
            <span class="rb-cart-badge">{{ state.cart.length }}</span>
          </button>
        </div>
      </div>
    </div>
  </nav>

  <main>
    <!-- ===== HERO SECTION ===== -->
    <section class="rb-hero" id="home">
      <div class="container">
        <div class="row align-items-center g-5 py-5">
          <!-- Hero Text -->
          <div class="col-lg-6 order-2 order-lg-1">
            <span class="rb-tag mb-3 d-inline-flex align-items-center gap-2">
              <i class="bi bi-stars"></i> Signature Wine Red Edition 2026
            </span>
            <h1 class="rb-heading-xl mb-3">
              Draped in Intoxicating <span class="rb-text-wine">Bordeaux</span> &amp; Pure Luxury
            </h1>
            <p class="rb-body-text mb-4">
              Experience handcrafted mulberry silk dresses, velvet galas, and bespoke virgin wool
              blazers designed in our signature wine red color palette.
            </p>

            <div class="d-flex flex-wrap gap-3 mb-5">
              <a href="#shop" class="btn rb-btn-primary">
                Explore Collection <i class="bi bi-arrow-right ms-1"></i>
              </a>
              <a href="#story" class="btn rb-btn-secondary">
                <i class="bi bi-play-circle me-1"></i> Watch Atelier Story
              </a>
            </div>

            <!-- Stats Row -->
            <div class="row row-cols-3 g-3 rb-stats-row">
              <div class="col text-center">
                <div class="rb-stat-value">12k+</div>
                <div class="rb-stat-label">Couture Clients</div>
              </div>
              <div class="col text-center">
                <div class="rb-stat-value">100%</div>
                <div class="rb-stat-label">Sustainable Silk</div>
              </div>
              <div class="col text-center">
                <div class="rb-stat-value">4.9★</div>
                <div class="rb-stat-label">Global Rating</div>
              </div>
            </div>
          </div>

          <!-- Hero Image -->
          <div class="col-lg-6 order-1 order-lg-2">
            <div class="rb-hero-img-wrapper position-relative">
              <img
                src="https://images.unsplash.com/photo-1566174053879-31528523f8ae?auto=format&fit=crop&w=900&q=80"
                alt="Wine Red Velvet Gown"
                class="img-fluid rb-hero-img"
              />
              <!-- Floating Card -->
              <div class="rb-floating-card d-flex align-items-center gap-3">
                <img
                  src="https://images.unsplash.com/photo-1566174053879-31528523f8ae?auto=format&fit=crop&w=80&q=80"
                  alt="Preview"
                  class="rb-floating-thumb"
                />
                <div>
                  <p class="rb-floating-title mb-0">Velvet Evening Gown</p>
                  <p class="rb-floating-sub mb-0">Hand-stitched Corset</p>
                  <p class="rb-floating-price mb-0">$345.00</p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- ===== FEATURES BAR ===== -->
    <section class="rb-features-bar py-5">
      <div class="container">
        <div class="row row-cols-1 row-cols-sm-2 row-cols-lg-4 g-4">
          <div class="col" v-for="feat in features" :key="feat.title">
            <div class="rb-feature-card d-flex align-items-start gap-3 h-100 p-3">
              <div class="rb-feature-icon flex-shrink-0">
                <i :class="feat.icon"></i>
              </div>
              <div>
                <h5 class="rb-feature-title mb-1">{{ feat.title }}</h5>
                <p class="rb-feature-desc mb-0">{{ feat.desc }}</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- ===== COLLECTION / SHOP SECTION ===== -->
    <section class="rb-shop py-5" id="shop">
      <div class="container">
        <!-- Section Header -->
        <div class="text-center mb-4">
          <span class="rb-subheading">Curated Wardrobe</span>
          <h2 class="rb-heading-lg mt-1">Signature Wine Red Collection</h2>
        </div>

        <!-- Category Filter Tabs -->
        <div class="d-flex flex-wrap justify-content-center gap-2 mb-5">
          <button
            v-for="tab in tabs"
            :key="tab.value"
            class="btn rb-tab-btn"
            :class="{ active: activeTab === tab.value }"
            @click="activeTab = tab.value"
          >
            {{ tab.label }}
          </button>
        </div>

        <!-- Products Grid -->
        <div class="row row-cols-1 row-cols-sm-2 row-cols-lg-3 row-cols-xl-4 g-4">
          <div class="col" v-for="product in filtered" :key="product.id">
            <div class="rb-product-card h-100">
              <!-- Media -->
              <div class="rb-product-media position-relative overflow-hidden">
                <span v-if="product.isNew" class="badge rb-badge-wine position-absolute top-0 start-0 m-2">New</span>
                <span
                  v-if="product.isBestSeller"
                  class="badge rb-badge-gold position-absolute start-0 m-2"
                  :style="product.isNew ? 'top:2rem' : 'top:0'"
                >Best Seller</span>
                <img :src="product.primaryImg" :alt="product.title" class="rb-product-img" loading="lazy" />
                <img :src="product.secondaryImg" :alt="product.title" class="rb-product-img rb-product-img-hover" loading="lazy" />
                <!-- Overlay Actions -->
                <div class="rb-overlay-actions d-flex gap-2">
                  <button class="rb-action-btn" title="Quick View" @click="openPDP(product.id)">
                    <i class="bi bi-eye"></i>
                  </button>
                  <button class="rb-action-btn" title="Wishlist" @click="toggleWishlist(product.id)">
                    <i
                      :class="state.wishlist.includes(product.id) ? 'bi bi-heart-fill' : 'bi bi-heart'"
                      :style="state.wishlist.includes(product.id) ? 'color:var(--wine)' : ''"
                    ></i>
                  </button>
                </div>
              </div>

              <!-- Body -->
              <div class="rb-product-body p-3">
                <span class="rb-product-category">{{ product.category }}</span>
                <h5 class="rb-product-title mt-1" @click="openPDP(product.id)" style="cursor:pointer">
                  {{ product.title }}
                </h5>
                <!-- Rating -->
                <div class="d-flex align-items-center gap-1 mb-2">
                  <i class="bi bi-star-fill rb-star" v-for="s in 4" :key="s"></i>
                  <i class="bi bi-star-half rb-star"></i>
                  <small class="text-muted ms-1">({{ product.reviewsCount }})</small>
                </div>
                <!-- Price + Cart -->
                <div class="d-flex align-items-center justify-content-between">
                  <div>
                    <span class="rb-current-price">৳{{ product.price.toFixed(2) }}</span>
                    <span class="rb-old-price ms-2">৳{{ product.oldPrice.toFixed(2) }}</span>
                  </div>
                  <button class="btn rb-add-cart-btn btn-sm" @click="quickAddToCart(product.id)">
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
    <section class="rb-story py-5" id="story">
      <div class="container">
        <div class="row align-items-center g-5">
          <!-- Content -->
          <div class="col-lg-6">
            <span class="rb-subheading rb-subheading-gold">The Atelier Philosophy</span>
            <h2 class="rb-heading-lg mt-1 mb-3" style="color:#fff">Why We Built Our World Around Wine Red</h2>
            <p class="rb-body-text mb-4" style="color:rgba(255,255,255,0.65)">
              Wine red isn't merely a color; it is a statement of warmth, authority, and sensual
              sophistication. Each garment undergoes meticulous dyeing using organic botanical
              extracts to capture light with rich complexity.
            </p>
            <div class="row g-3 mb-4">
              <div class="col-sm-6">
                <div class="rb-highlight-box p-3">
                  <h6 class="rb-highlight-title">Italian Silk Atelier</h6>
                  <p class="rb-highlight-desc mb-0">Woven in historical mills in Como, Italy for peerless drape.</p>
                </div>
              </div>
              <div class="col-sm-6">
                <div class="rb-highlight-box p-3">
                  <h6 class="rb-highlight-title">Bespoke Tailoring</h6>
                  <p class="rb-highlight-desc mb-0">Precision cut patterns designed for body confidence.</p>
                </div>
              </div>
            </div>
            <a href="#shop" class="btn rb-btn-gold">
              Shop Signature Collection <i class="bi bi-arrow-up-right ms-1"></i>
            </a>
          </div>
          <!-- Image -->
          <div class="col-lg-6">
            <img
              src="https://images.unsplash.com/photo-1594938298603-c8148c4dae35?auto=format&fit=crop&w=900&q=80"
              alt="Tailored Wool Blazer Craftsmanship"
              class="img-fluid rb-story-img"
            />
          </div>
        </div>
      </div>
    </section>

    <!-- ===== ABOUT SECTION ===== -->
    <section class="rb-about py-5" id="about">
      <div class="container">
        <div class="text-center mb-5">
          <span class="rb-subheading">Our Journey</span>
          <h2 class="rb-heading-lg mt-1">Reimagining Modern Luxury Fashion</h2>
          <p class="rb-body-text mx-auto mt-3" style="max-width:600px">
            Founded in 2018, RichBrand Couture emerged from a single desire: to create timeless
            wardrobe mainstays centered on deep burgundy and rich wine tones.
          </p>
        </div>
        <div class="row row-cols-1 row-cols-md-3 g-4">
          <div class="col" v-for="tl in timeline" :key="tl.year">
            <div class="rb-timeline-card text-center p-4 h-100">
              <div class="rb-timeline-year mb-2">{{ tl.year }}</div>
              <h5 class="rb-timeline-title">{{ tl.title }}</h5>
              <p class="rb-body-text mb-0">{{ tl.desc }}</p>
            </div>
          </div>
        </div>
      </div>
    </section>
  </main>

  <!-- ===== FOOTER ===== -->
  <footer class="rb-footer pt-5 pb-3">
    <div class="container">
      <div class="row g-4 mb-4">
        <!-- Brand -->
        <div class="col-12 col-md-4">
          <a href="#home" class="d-inline-flex align-items-center gap-2 mb-3 text-decoration-none">
            <span class="rb-logo-mark">R</span>
            <span class="rb-logo-text">RichBrand</span>
          </a>
          <p class="rb-footer-desc">
            Elevating contemporary wardrobes with signature wine red elegance, sustainable
            craftsmanship, and timeless silhouettes.
          </p>
          <div class="d-flex gap-2 mt-3">
            <a href="#" class="rb-social-btn" aria-label="Instagram"><i class="bi bi-instagram"></i></a>
            <a href="#" class="rb-social-btn" aria-label="Pinterest"><i class="bi bi-pinterest"></i></a>
            <a href="#" class="rb-social-btn" aria-label="Facebook"><i class="bi bi-facebook"></i></a>
            <a href="#" class="rb-social-btn" aria-label="TikTok"><i class="bi bi-tiktok"></i></a>
          </div>
        </div>
        <!-- Shop -->
        <div class="col-6 col-md-2">
          <h6 class="rb-footer-heading mb-3">Shop</h6>
          <ul class="list-unstyled rb-footer-links">
            <li><a href="#shop">Evening Dresses</a></li>
            <li><a href="#shop">Wool Blazers</a></li>
            <li><a href="#shop">Silk Slips</a></li>
            <li><a href="#shop">Cashmere Coats</a></li>
          </ul>
        </div>
        <!-- Services -->
        <div class="col-6 col-md-2">
          <h6 class="rb-footer-heading mb-3">Services</h6>
          <ul class="list-unstyled rb-footer-links">
            <li><a href="#about">Our Story</a></li>
            <li><a href="#" @click.prevent="openAuthModal">My Account</a></li>
            <li><a href="#">Size Guide</a></li>
            <li><a href="#">Shipping &amp; Returns</a></li>
          </ul>
        </div>
        <!-- Newsletter -->
        <div class="col-12 col-md-4">
          <h6 class="rb-footer-heading mb-3">Stay Connected</h6>
          <p class="rb-footer-desc mb-3">
            Subscribe for private trunk show invites and get 10% off your first order.
          </p>
          <div class="input-group">
            <input
              type="email"
              class="form-control rb-newsletter-input"
              placeholder="Enter your email…"
            />
            <button class="btn rb-btn-primary btn-sm rb-newsletter-btn" @click="showToast('Subscribed!')">
              Join
            </button>
          </div>
        </div>
      </div>
      <!-- Bottom -->
      <div class="rb-footer-bottom d-flex flex-column flex-sm-row align-items-center justify-content-between gap-2 pt-4">
        <p class="mb-0 small">© 2026 RichBrand Couture. All rights reserved.</p>
        <div class="d-flex gap-3">
          <span class="small rb-footer-policy">Privacy Policy</span>
          <span class="small rb-footer-policy">Terms of Service</span>
          <span class="small rb-footer-policy">Cookies</span>
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
/* ===== CSS VARIABLES ===== */
.rb-navbar,
main,
footer {
  --wine: #7b1f2e;
  --wine-light: #a0263a;
  --wine-dark: #5a1520;
  --gold: #c9a84c;
  --gold-light: #e2c57e;
  --dark: #1a1a2e;
  --dark-2: #16213e;
  --radius: 12px;
  --radius-lg: 20px;
  --radius-pill: 50px;
  --shadow: 0 4px 24px rgba(0,0,0,0.10);
  --shadow-lg: 0 12px 48px rgba(0,0,0,0.18);
  --transition: all 0.3s ease;
}

/* ===== NAVBAR ===== */
.rb-navbar {
  background: rgba(26, 26, 46, 0.97) !important;
  backdrop-filter: blur(14px);
  border-bottom: 1px solid rgba(123, 31, 46, 0.35);
  padding: 0.85rem 0;
  z-index: 1030;
}

.rb-logo-mark {
  width: 36px;
  height: 36px;
  border-radius: 50%;
  background: linear-gradient(135deg, #a0263a, #5a1520);
  color: #fff;
  font-weight: 800;
  font-size: 1rem;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  font-family: 'Poppins', sans-serif;
  flex-shrink: 0;
}

.rb-logo-text {
  font-family: 'Poppins', sans-serif;
  font-weight: 700;
  font-size: 1.2rem;
  color: #fff;
}

.navbar-nav .nav-link {
  font-family: 'Poppins', sans-serif;
  font-size: 0.875rem;
  font-weight: 500;
  color: rgba(255,255,255,0.75) !important;
  padding: 0.45rem 0.9rem !important;
  border-radius: 50px;
  transition: all 0.3s ease;
}
.navbar-nav .nav-link:hover,
.navbar-nav .nav-link.active {
  color: #fff !important;
  background: rgba(123,31,46,0.28);
}

.rb-btn-outline {
  border: 1px solid rgba(255,255,255,0.38);
  color: #fff;
  border-radius: 50px;
  font-size: 0.82rem;
  transition: all 0.3s ease;
  background: transparent;
}
.rb-btn-outline:hover { background: #7b1f2e; border-color: #7b1f2e; color: #fff; }

.rb-icon-btn {
  width: 36px;
  height: 36px;
  border-radius: 50%;
  background: transparent;
  border: 1px solid rgba(255,255,255,0.25);
  color: #fff;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  font-size: 1rem;
  cursor: pointer;
  transition: all 0.3s ease;
}
.rb-icon-btn:hover { background: #7b1f2e; border-color: #7b1f2e; }

.rb-cart-badge {
  position: absolute;
  top: -5px;
  right: -5px;
  background: #a0263a;
  color: #fff;
  font-size: 0.6rem;
  width: 16px;
  height: 16px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
}

/* ===== HERO ===== */
.rb-hero {
  background: linear-gradient(135deg, #1a1a2e 0%, #16213e 60%, #2a0a12 100%);
  min-height: 90vh;
  display: flex;
  align-items: center;
}

.rb-tag {
  background: rgba(123,31,46,0.18);
  border: 1px solid rgba(123,31,46,0.5);
  color: #e8a0b0;
  font-size: 0.78rem;
  font-weight: 500;
  padding: 0.4rem 1rem;
  border-radius: 50px;
  font-family: 'Poppins', sans-serif;
}

.rb-heading-xl {
  font-family: 'Poppins', sans-serif;
  font-size: clamp(1.9rem, 4.5vw, 3rem);
  font-weight: 700;
  color: #fff;
  line-height: 1.22;
}

.rb-text-wine {
  background: linear-gradient(135deg, #a0263a, #c9a84c);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.rb-body-text {
  color: rgba(255,255,255,0.65);
  font-family: 'Poppins', sans-serif;
  font-size: 1rem;
  line-height: 1.75;
}

/* Buttons */
.rb-btn-primary {
  background: linear-gradient(135deg, #a0263a, #5a1520);
  color: #fff;
  border: none;
  padding: 0.75rem 1.75rem;
  border-radius: 50px;
  font-weight: 600;
  font-family: 'Poppins', sans-serif;
  font-size: 0.9rem;
  transition: all 0.3s ease;
  box-shadow: 0 6px 20px rgba(123,31,46,0.4);
}
.rb-btn-primary:hover {
  transform: translateY(-2px);
  box-shadow: 0 10px 30px rgba(123,31,46,0.55);
  color: #fff;
}

.rb-btn-secondary {
  background: rgba(255,255,255,0.08);
  color: #fff;
  border: 1px solid rgba(255,255,255,0.28);
  padding: 0.75rem 1.75rem;
  border-radius: 50px;
  font-weight: 500;
  font-family: 'Poppins', sans-serif;
  font-size: 0.9rem;
  transition: all 0.3s ease;
}
.rb-btn-secondary:hover { background: rgba(255,255,255,0.14); color: #fff; }

.rb-btn-gold {
  background: linear-gradient(135deg, #c9a84c, #e2c57e);
  color: #1a1a2e;
  border: none;
  padding: 0.75rem 1.75rem;
  border-radius: 50px;
  font-weight: 700;
  font-family: 'Poppins', sans-serif;
  font-size: 0.9rem;
  transition: all 0.3s ease;
}
.rb-btn-gold:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 24px rgba(201,168,76,0.45);
  color: #1a1a2e;
}

/* Stats */
.rb-stats-row {
  border-top: 1px solid rgba(255,255,255,0.12);
  padding-top: 1.5rem;
}
.rb-stat-value {
  font-family: 'Poppins', sans-serif;
  font-size: 1.5rem;
  font-weight: 700;
  color: #a0263a;
}
.rb-stat-label {
  font-size: 0.75rem;
  color: rgba(255,255,255,0.5);
  margin-top: 0.15rem;
}

/* Hero image */
.rb-hero-img-wrapper { border-radius: 20px; }
.rb-hero-img {
  border-radius: 20px;
  width: 100%;
  height: 520px;
  object-fit: cover;
  box-shadow: 0 12px 48px rgba(0,0,0,0.28);
}

/* Floating card */
.rb-floating-card {
  position: absolute;
  bottom: 2rem;
  left: -2rem;
  background: rgba(22,33,62,0.94);
  backdrop-filter: blur(16px);
  border: 1px solid rgba(123,31,46,0.4);
  border-radius: 12px;
  padding: 0.85rem 1rem;
  box-shadow: 0 12px 40px rgba(0,0,0,0.3);
  min-width: 220px;
}
.rb-floating-thumb {
  width: 52px;
  height: 52px;
  border-radius: 8px;
  object-fit: cover;
}
.rb-floating-title { font-family: 'Poppins',sans-serif; font-size: 0.85rem; font-weight: 600; color: #fff; }
.rb-floating-sub { font-size: 0.72rem; color: rgba(255,255,255,0.5); }
.rb-floating-price { font-size: 0.88rem; font-weight: 700; color: #a0263a; }

/* ===== FEATURES BAR ===== */
.rb-features-bar {
  background: #fff;
  border-top: 1px solid #f0e8ea;
  border-bottom: 1px solid #f0e8ea;
}
.rb-feature-card {
  border-radius: 12px;
  transition: all 0.3s ease;
}
.rb-feature-card:hover { background: #fdf4f6; }
.rb-feature-icon {
  width: 50px;
  height: 50px;
  background: rgba(123,31,46,0.08);
  border-radius: 12px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.3rem;
  color: #7b1f2e;
}
.rb-feature-title {
  font-family: 'Poppins',sans-serif;
  font-size: 0.88rem;
  font-weight: 600;
  color: #1a1a2e;
}
.rb-feature-desc { font-size: 0.8rem; color: #888; }

/* ===== SECTION LABELS ===== */
.rb-subheading {
  font-family: 'Poppins',sans-serif;
  font-size: 0.75rem;
  font-weight: 700;
  letter-spacing: 2.5px;
  text-transform: uppercase;
  color: #7b1f2e;
  display: block;
}
.rb-subheading-gold { color: #c9a84c !important; }
.rb-heading-lg {
  font-family: 'Poppins',sans-serif;
  font-size: clamp(1.5rem, 3vw, 2.2rem);
  font-weight: 700;
  color: #1a1a2e;
  line-height: 1.25;
}

/* ===== SHOP ===== */
.rb-shop { background: #f9f7f8; }

.rb-tab-btn {
  font-family: 'Poppins',sans-serif;
  font-size: 0.82rem;
  font-weight: 500;
  color: #888;
  background: #fff;
  border: 1px solid #e2e2e2;
  border-radius: 50px;
  padding: 0.45rem 1.1rem;
  transition: all 0.3s ease;
}
.rb-tab-btn:hover { border-color: #a0263a; color: #7b1f2e; }
.rb-tab-btn.active { background: #7b1f2e; border-color: #7b1f2e; color: #fff; }

/* Product Card */
.rb-product-card {
  background: #fff;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 2px 14px rgba(0,0,0,0.07);
  transition: all 0.32s ease;
}
.rb-product-card:hover {
  transform: translateY(-7px);
  box-shadow: 0 18px 44px rgba(0,0,0,0.13);
}

.rb-product-media {
  height: 280px;
  background: #f5f0f1;
  position: relative;
}

.rb-product-img {
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: opacity 0.45s ease, transform 0.45s ease;
}
.rb-product-img-hover { opacity: 0; }
.rb-product-media:hover .rb-product-img:not(.rb-product-img-hover) { opacity: 0; transform: scale(1.05); }
.rb-product-media:hover .rb-product-img-hover { opacity: 1; transform: scale(1.05); }

.rb-overlay-actions {
  position: absolute;
  bottom: 0.75rem;
  right: 0.75rem;
  opacity: 0;
  transition: all 0.3s ease;
}
.rb-product-media:hover .rb-overlay-actions { opacity: 1; }

.rb-action-btn {
  width: 36px;
  height: 36px;
  border-radius: 50%;
  background: rgba(255,255,255,0.94);
  border: none;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 0.9rem;
  cursor: pointer;
  transition: all 0.25s ease;
  box-shadow: 0 2px 8px rgba(0,0,0,0.14);
}
.rb-action-btn:hover { background: #7b1f2e; color: #fff; }

.rb-badge-wine {
  background: #7b1f2e !important;
  font-size: 0.68rem;
  border-radius: 50px;
  padding: 0.28rem 0.6rem;
}
.rb-badge-gold {
  background: #c9a84c !important;
  color: #1a1a2e;
  font-size: 0.68rem;
  border-radius: 50px;
  padding: 0.28rem 0.6rem;
}

.rb-product-category {
  font-size: 0.7rem;
  font-weight: 700;
  letter-spacing: 1px;
  text-transform: uppercase;
  color: #7b1f2e;
}
.rb-product-title {
  font-family: 'Poppins',sans-serif;
  font-size: 0.93rem;
  font-weight: 600;
  color: #1a1a2e;
  line-height: 1.3;
  margin: 0.2rem 0;
  transition: color 0.2s;
}
.rb-product-title:hover { color: #7b1f2e; }
.rb-star { color: #c9a84c; font-size: 0.72rem; }
.rb-current-price { font-family: 'Poppins',sans-serif; font-size: 0.98rem; font-weight: 700; color: #7b1f2e; }
.rb-old-price { font-size: 0.8rem; color: #bbb; text-decoration: line-through; }
.rb-add-cart-btn {
  background: #7b1f2e;
  color: #fff;
  border: none;
  border-radius: 50px;
  font-size: 0.75rem;
  font-weight: 600;
  padding: 0.38rem 0.85rem;
  transition: all 0.25s ease;
}
.rb-add-cart-btn:hover { background: #5a1520; color: #fff; transform: scale(1.05); }

/* ===== STORY SECTION ===== */
.rb-story { background: linear-gradient(135deg, #1a1a2e, #16213e); }

.rb-highlight-box {
  background: rgba(255,255,255,0.05);
  border: 1px solid rgba(255,255,255,0.12);
  border-radius: 12px;
  transition: all 0.3s ease;
}
.rb-highlight-box:hover { background: rgba(123,31,46,0.18); border-color: rgba(123,31,46,0.4); }
.rb-highlight-title { font-family: 'Poppins',sans-serif; font-size: 0.9rem; font-weight: 700; color: #fff; }
.rb-highlight-desc { font-size: 0.8rem; color: rgba(255,255,255,0.58); }

.rb-story-img {
  border-radius: 20px;
  width: 100%;
  height: 460px;
  object-fit: cover;
  box-shadow: 0 12px 48px rgba(0,0,0,0.3);
}

/* ===== ABOUT ===== */
.rb-about { background: #f9f7f8; }
.rb-timeline-card {
  background: #fff;
  border-radius: 12px;
  box-shadow: 0 2px 14px rgba(0,0,0,0.07);
  border-top: 4px solid #7b1f2e;
  transition: all 0.3s ease;
}
.rb-timeline-card:hover { transform: translateY(-6px); box-shadow: 0 14px 36px rgba(0,0,0,0.13); }
.rb-timeline-year { font-family: 'Poppins',sans-serif; font-size: 2.2rem; font-weight: 800; color: #a0263a; line-height: 1; }
.rb-timeline-title { font-family: 'Poppins',sans-serif; font-size: 1rem; font-weight: 700; color: #1a1a2e; }

/* ===== FOOTER ===== */
.rb-footer { background: #1a1a2e; color: rgba(255,255,255,0.65); }
.rb-footer .rb-logo-text { color: #fff; }
.rb-footer .rb-logo-mark { background: linear-gradient(135deg, #a0263a, #5a1520); }
.rb-footer-desc { font-size: 0.85rem; color: rgba(255,255,255,0.52); line-height: 1.7; }
.rb-footer-heading {
  font-family: 'Poppins',sans-serif;
  font-size: 0.82rem;
  font-weight: 700;
  color: #fff;
  text-transform: uppercase;
  letter-spacing: 1px;
}
.rb-footer-links { display: flex; flex-direction: column; gap: 0.55rem; }
.rb-footer-links a { font-size: 0.84rem; color: rgba(255,255,255,0.52); text-decoration: none; transition: all 0.25s ease; }
.rb-footer-links a:hover { color: #a0263a; padding-left: 4px; }

.rb-social-btn {
  width: 36px;
  height: 36px;
  border-radius: 50%;
  background: rgba(255,255,255,0.08);
  color: rgba(255,255,255,0.65);
  display: inline-flex;
  align-items: center;
  justify-content: center;
  font-size: 0.88rem;
  text-decoration: none;
  transition: all 0.25s ease;
}
.rb-social-btn:hover { background: #7b1f2e; color: #fff; }

.rb-newsletter-input {
  background: rgba(255,255,255,0.07) !important;
  border: 1px solid rgba(255,255,255,0.14) !important;
  color: #fff !important;
  font-size: 0.84rem;
}
.rb-newsletter-input::placeholder { color: rgba(255,255,255,0.35); }
.rb-newsletter-input:focus { background: rgba(255,255,255,0.1) !important; border-color: #a0263a !important; box-shadow: none !important; }
.rb-newsletter-btn { border-radius: 0 50px 50px 0 !important; }

.rb-footer-bottom { border-top: 1px solid rgba(255,255,255,0.1); color: rgba(255,255,255,0.38); }
.rb-footer-policy { cursor: pointer; transition: color 0.2s; }
.rb-footer-policy:hover { color: rgba(255,255,255,0.7); }

/* ===== RESPONSIVE ===== */
@media (max-width: 991.98px) {
  .rb-hero { min-height: auto; padding: 2.5rem 0; }
  .rb-hero-img { height: 380px; }
  .rb-floating-card { left: 0; bottom: 1rem; }
  .rb-story-img { height: 320px; }
}
@media (max-width: 767.98px) {
  .rb-hero-img { height: 280px; }
  .rb-floating-card { display: none !important; }
  .rb-product-media { height: 240px; }
}
</style>
