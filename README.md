<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <title>Bootstrap Local Setup</title>


    <!-- Bootstrap CSS -->
    <link rel="stylesheet" href="/css/bootstrap.min.css" />
    <link rel="stylesheet" href="card.css" />
    <link href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.3/font/bootstrap-icons.css" rel="stylesheet">
    <style>
        body, html {
          height: 100%;
          background: #000000;
          margin: 0;
          font-family: "Georgia", serif;
        }

        .hero {
          height: 100vh;
          position: relative;
          color: #fff;
          overflow: hidden;

        }

        /* VIDEO BACKGROUND */
        .hero-video {
          position: absolute;
          top: 50%;
          left: 50%;
          min-width: 100%;
          min-height: 100%;
          width: auto;
          height: auto;
          transform: translate(-50%, -50%);
          object-fit: cover;
          z-index: 0;
        }

        /* DARK OVERLAY */
        .hero-overlay {
          position: absolute;
          inset: 0;
          background: rgba(0, 0, 0, 0.45);
          z-index: 1;
        }

        /* LOGO */
        .hero-logo {
          position: absolute;
          top: 30px;
          left: 50%;
          transform: translateX(-50%);
          display: flex;
          flex-direction: column;
          align-items: center;   /* 🔑 centers text under logo */
          text-align: center;
        }

        .hero-logo img {
          height: 48px;
        }

        .logo-text {
          margin-top: 6px;
          font-size: 1.2rem;
          letter-spacing: 2px;
          color: #000; /* use white since hero has dark overlay */
          font-weight: 300;
        }


        /* CENTER TEXT */
        .hero-content {
          position: relative;
          z-index: 2;
          height: 100%;
          text-align: center;
          display: flex;
          flex-direction: column;
          justify-content: center;
        }

        /* MENU PILL POSITION */
        .menu-pill-wrapper {
          position: absolute;
          bottom: 60px; /* small margin from bottom */
          left: 50%;
          transform: translateX(-50%);
          z-index: 3;
        }


        .hero::after {
          content: "";
          position: absolute;
          inset: 0;
          background: rgba(0,0,0,0.45);
        }

        .hero-content {
          position: relative;
          z-index: 2;
          text-align: center;
        }

        .hero h1 {
          font-size: clamp(2.5rem, 5vw, 4rem);
          letter-spacing: 2px;
        }

        .hero p {
          letter-spacing: 3px;
          font-size: 0.9rem;
        }

        /* MENU BUTTON */
        .menu-btn {
          background: #fff;
              color: #000;
              border-radius: 30px;
              padding: 10px 25px;
              border: none;
              font-weight: 500;
            }

            /* OVERLAY */
            .menu-overlay {
              position: fixed;
              height: 85vh;
              inset: 0;
              background: url("/images/nav-container.png") center/cover no-repeat;
              display: flex;
              justify-content: center;
              align-items: center;
              opacity: 0;
              pointer-events: none;
              transition: opacity 0.35s ease;
                  z-index: 999;
                    }

            .menu-overlay.active {
              opacity: 1;
              pointer-events: auto;
            }

            /* MENU PANEL */
            .menu-panel {
              width: 80%;
              height: 60vh;
              display: flex;
              flex-direction: column;
              gap: 22px;
            }

            :root {
              --line-color: rgba(0, 0, 0, 0.8);
              --line-thin: 1px;
              --extension: 12px; /* How far the corners cross */
              --intrude-length: 25px; /* How far the middle line pokes inside */
            }

            .nav-wrapper {
              display: flex;
              flex-direction: column;
              align-items: center;
              justify-content: center;
              gap: 30px;
              padding: 50px;
            }

            .nav-row {
              display: flex;
              gap: 50px;
            }

            .menu-item-sketch {
              position: relative;
              padding: 15px 40px;
              background: rgba(255, 255, 255, 0.9);
              cursor: pointer;
              display: inline-block;
            }

            /* Vertical Lines (Left & Right) */
            .menu-item-sketch::before,
            .menu-item-sketch::after {
              content: "";
              position: absolute;
              top: calc(-1 * var(--extension));
              bottom: calc(-1 * var(--extension));
              width: var(--line-thin);
              background-color: var(--line-color);
            }
            .menu-item-sketch::before { left: 0; }
            .menu-item-sketch::after { right: 0; }

            /* Horizontal Lines (Top & Bottom) */
            .line-h::before,
            .line-h::after {
              content: "";
              position: absolute;
              left: calc(-1 * var(--extension));
              right: calc(-1 * var(--extension));
              height: var(--line-thin);
              background-color: var(--line-color);
            }
            .line-h::before { top: 0; }
            .line-h::after { bottom: 0; }

            .menu-item-sketch a {
              text-decoration: none;
              color: #1a1a1a;
              font-family: "Georgia", serif;
              font-size: 1.1rem;
              letter-spacing: 5px;
              text-transform: uppercase;
              display: block;
              position: relative;
            }

            /* The Inward Intruding Line */
            .menu-item-sketch a::after {
              content: "";
              position: absolute;
              right: -40px; /* Aligns with the right vertical line */
              width: var(--intrude-length);
              height: var(--line-thin);
              background-color: var(--line-color);
              top: 50%;
              transform: translateY(-50%);
              z-index: 2;
            }

            /* === MOBILE STYLES === */
            @media (max-width: 768px) {
                .menu-overlay {
                  position: fixed;
                  height: 100vh;
                }

              .nav-row {
                flex-direction: column; /* Stacks the first 3 items */
                gap: 30px;
                width: 100%;
                align-items: center;
              }

              .nav-wrapper {
                gap: 30px; /* Maintains spacing for the "Locate Us" item */
              }

              .menu-item-sketch {
                width: 100%; /* Optional: makes boxes wider on mobile */
                max-width: 300px;
              }
            }

        /* CLOSE ITEM – SAME STYLE, SLIGHTLY BOLDER */
        .close-item {
          letter-spacing: 5px;
        }

        /* MOBILE */
        @media (max-width: 768px) {
          .menu-panel {
            width: 100%;
            height: 100vh;
          }

          .menu-item-sketch {
            font-size: 0.95rem;
            padding: 16px 18px;
          }
        }


        .menu-pill-wrapper {
          width: 100%;
          display: flex;
          justify-content: center;
        }

        /* BASE */
        .menu-pill {
          background: #fff;
          display: flex;
          align-items: center;
          box-shadow: 0 10px 30px rgba(0,0,0,0.2);

          clip-path: polygon(
            8px 0,
            calc(100% - 8px) 0,
            100% 8px,
            100% calc(100% - 8px),
            calc(100% - 8px) 100%,
            8px 100%,
            0 calc(100% - 8px),
            0 8px
          );

          transform-origin: center center;
        }

        /* TEXT */
        .menu-item {
          padding: 7px 12px;
          font-weight: 300;
          font-size: 1rem;
          letter-spacing: 2px;
          color: #000;
        }

        .menu-divider {
          width: 42px;
          height: 42px;
          font-size: 1.8rem;
          margin: 0 6px;
          display: flex;
          align-items: center;
          justify-content: center;
        }

        /* 📱 MOBILE */
        @media (max-width: 768px) {

          .menu-pill {
            transform: scale(0.85); /* ✅ scale inner, not wrapper */
            box-shadow: 0 6px 18px rgba(0,0,0,0.18);

            clip-path: polygon(
              6px 0,
              calc(100% - 6px) 0,
              100% 6px,
              100% calc(100% - 6px),
              calc(100% - 6px) 100%,
              6px 100%,
              0 calc(100% - 6px),
              0 6px
            );
          }

          .menu-item {
            padding: 6px 10px;
            font-size: 0.8rem;
            letter-spacing: 1.5px;
          }

          .menu-divider {
            width: 34px;
            height: 34px;
            font-size: 1.4rem;
            margin: 0 4px;
          }
        }

        .image-carousel {
          display: flex;
          gap: 19px;
          padding: 0px 12vw; /* Increased padding to allow for the "bow" height */
          overflow-x: scroll;
          cursor: grab;
          scroll-behavior: smooth;
          align-items: center; /* Crucial: keeps the 'pinch' centered */
          min-height: 500px;
        }

        .image-carousel::-webkit-scrollbar {
          display: none;
        }

        .carousel-card {
          flex: 0 0 auto;
          width: 240px;
          height: 380px;
          transition: transform 0.1s ease-out; /* Smoother than changing width/height */
          will-change: transform;
        }

        .carousel-card img {
          width: 100%;
          height: 100%;
          object-fit: cover;
          border-radius: 0px;
          box-shadow: 0 30px 60px rgba(0,0,0,0.25);
        }
        .hero-tagline {
          font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
          letter-spacing: 3px;
          font-weight: 300;
        }
        /* =========================
          MOBILE CAROUSEL SCALING
       ========================= */
    @media (max-width: 768px) {
      .image-carousel {
        gap: 12px;                 /* smaller gap */
        padding: 0px 8vw;         /* tighter padding */
      }

      .carousel-card {
        width: 160px;              /* smaller card */
        height: 260px;
      }

      .carousel-card img {
        box-shadow: 0 18px 36px rgba(0,0,0,0.22);
      }
    }

    /* EXTRA SMALL PHONES */
    @media (max-width: 480px) {

      .image-carousel {
        gap: 10px;
        padding: 24px 6vw;
      }

      .carousel-card {
        width: 140px;
        height: 230px;
      }
    }



        /* BRANDING SECTION */
        .brand-header {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 30px;
            margin-bottom: 50px; /* Space between brand and buttons */
        }

        .brand-text {
            font-family: "Helvetica", sans-serif;
            font-size: clamp(1.5rem, 6vw, 4.5rem);
            letter-spacing: 0.35em;
            font-weight: 400;
        }

        .brand-logo {
            width: clamp(100px, 12vw, 160px);
            height: auto;
        }

        /* NAVIGATION WRAPPER */
        .nav-wrapper {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 30px;
        }

        /* Row of items on Desktop */
        .nav-row {
            display: flex;
            gap: 40px;
        }

        /* SKETCH ITEM STYLE (1px lines) */
        .menu-item-sketch {
            position: relative;
            padding: 15px 40px;
            min-width: 200px;
        }

        /* The Inward Intruding Line */
        .menu-item-sketch a::after {
            content: "";
            position: absolute;
            right: -40px; /* Aligns with right vertical border */
            width: 25px;   /* Pokes 25px inside the box */
            height: 1px;
            background-color: #000;
            top: 50%;
        }

        /* === MOBILE VIEW === */
        @media (max-width: 768px) {
            .brand-header {
                gap: 10px;
                margin-bottom: 30px;
            }

            .brand-text {
                letter-spacing: 0.1em;
            }

            /* Force nav items into one straight column */
            .nav-row {
                flex-direction: column;
                gap: 25px;
                width: 100%;
                align-items: center;
            }
        }
        /* Tablets & below */
@media (max-width: 768px) {
  .hero-tagline {
    padding: 1%;
    font-size: 12px;
    letter-spacing: 2.5px;
  }

  h1 {
     font-size: clamp(32px, 6vw, 64px);
    padding: 1%;
    line-height: 1.1;
  }
}

/* Small phones */
@media (max-width: 480px) {
  .hero-tagline {
    font-size: 11px;
    letter-spacing: 2px;
  }

  h1 {
    font-size: 34px;
    line-height: 1.15;
  }
}

        .hero-copy {
          max-width: 880px;
          margin: 0 auto;
          text-align: center;
          color: #ffffff;

          background-image:
          url("/images/background-section-2.png"); /* replace with your image */

          background-size: cover;
          background-position: center;
          background-repeat: no-repeat;
        }
        .hero-copy-2 {
          max-width: 800px;
          margin: 0 auto;
          text-align: center;
          color: #ffffff;
        }

        /* Top line */
        .hero-top {
          font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
          font-size: 15px;
          letter-spacing: 1px;
          margin-bottom: 32px;
          opacity: 0.9;
        }

        /* Middle statement (normal / brand font) */
        .hero-middle {
          font-family: inherit; /* uses site default */
          font-size: 34px;
          font-weight: 400;
          line-height: 1.45;
          margin-bottom: 36px;
        }

        /* Bottom paragraph */
        .hero-bottom {
          font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
          font-size: 20px;
          line-height: 1.7;
          opacity: 0.85;
        }

        @media (max-width: 768px) {
          .hero-copy{
            padding: 10%;
          }
          .hero-middle {
            font-size: 20px;
          }

          .hero-top,
          .hero-bottom {
            font-size: 13px;
          }
        }
        .bg-noodles-image {
          background-image: url("/images/mina-noodles.png"); /* replace */
          background-size: cover;
          background-repeat: no-repeat;

          min-height: 220px; /* important so it’s visible */
        }

        @media (max-width: 768px) {
          .bg-noodles-image {
            min-height: 160px;
          }
        }

    .hero-copy-2 {
        padding-bottom: 100px; /* Space to allow the image to overlap without hitting text */
    }

    .intruder-container {
        display: flex;
        position: relative;
        justify-content: center;
        width: 100%;
    }

    .intruding-image {
        width: 100%; /* Adjust width as needed */
        height: auto;

        /* The Magic: Move up by 35% of the image's height */
        margin-top: -35%;

        /* Positioning */
        position: relative;
        z-index: 1; /* Sits behind the text div */

        /* Optional: Fading effect for a smooth "background" transition */
        mask-image: linear-gradient(to top, rgba(0,0,0,1) 70%, rgba(0,0,0,0));
        -webkit-mask-image: linear-gradient(to top, rgba(0,0,0,1) 70%, rgba(0,0,0,0));
    }
    .intruding-image-2 {
        width: 100%; /* Adjust width as needed */
        height: auto;
        object-fit: cover;

        /* The Magic: Move up by 35% of the image's height */
        margin-top: -25%;

        /* Positioning */
        position: relative;
        z-index: 1; /* Sits behind the text div */
    }
       .intruder-footer {
            position: relative;
            width: 100%;
            min-height: 60vh; /* 👈 gives stable reference height */
        }



        @media (max-width: 768px) {
            .intruder-footer {
                min-height: 75vh; /* taller image on mobile */
            }

            .hours-card-container {
                bottom: 10%;                      /* stays in middle-lower zone */
                transform: translateX(-50%) scale(0.55);
            }
        }

       .footer-copyright {
            position: absolute;
            left: 50%;
            transform: translateX(-50%);
            bottom: 20px; /* space below the card */
            color: black;
            font-size: 0.85rem;
            letter-spacing: 0.08em;
            text-align: center;
            z-index: 2;
            white-space: nowrap;
        }
        @media (max-width: 768px) {
            .footer-copyright {
                font-size: 0.65rem;
                bottom: 8px;
                letter-spacing: 0.06em;
            }
        }

        .footer-copyright::before {
            content: "";
            display: block;
            width: 40px;
            height: 1px;
            background: rgba(255,255,255,0.4);
            margin: 0 auto 6px;
        }



















    </style>
</head>
<body>
<!-- HERO -->
<div class="hero d-flex flex-column  align-items-center justify-content-center">
    <!-- Background Video -->
    <video class="hero-video" autoplay muted loop playsinline>
        <source src="images/mina-intro.mp4" type="video/mp4">
        Your browser does not support the video tag.
    </video>
    <div class="hero-overlay"></div>

    <div class="hero-content">
        <div class="hero-logo">
            <img src="images/Logo.png" alt="Logo">
        </div>
        <p class="hero-tagline mb-3">THE ULTIMATE TABLE EXPERIENCE</p>
        <h1>EVERYTHING TASTES<br>LIKE A STORY.</h1>

        <div class="menu-pill-wrapper d-flex justify-content-center">
            <div class="menu-pill d-flex align-items-center">

                <div class="menu-item left">
                    OUR MENU
                </div>

                <div class="menu-divider" style="color: black;" id="openMenu">
                    ☰
                </div>

                <div class="menu-item right" >
                    RESERVATION
                </div>

            </div>
        </div>

    </div>
</div>
<section class="image-carousel-section mb-5">
    <div class="image-carousel" id="imageCarousel">
        <div class="carousel-card"><img src="/images/1.jpg"></div>
        <div class="carousel-card"><img src="/images/2.jpg"></div>
        <div class="carousel-card"><img src="/images/3.jpg"></div>
        <div class="carousel-card"><img src="/images/4.jpg"></div>
        <div class="carousel-card"><img src="/images/5.jpg"></div>
        <div class="carousel-card"><img src="/images/6.png"></div>
    </div>

    <div class="hero-copy">
        <p class="hero-top">
            Calm, Contemporary East & Southeast Asian Kitchen
        </p>

        <h2 class="hero-middle">
            East And Southeast Asian Cuisine, Rooted In<br>
            Tradition And Elevated With Modern Technique<br>
            And Care.
        </h2>

        <p class="hero-bottom">
            Distinct And Quietly Refined, Mina Kitchen Leads<br>
            You Through East & Southeast Asian Flavours<br>
            With Crafted Interiors And Meticulous Detail. Relax<br>
            In Immersive, Serene Spaces And Enjoy Warm,<br>
            Attentive Service
        </p>
    </div>

    <div class="container-fluid px-4">
        <div class="row g-2 p-0">

            <div class="col-6 col-md-3">
                <img src="images/menu-1.jpg" class="img-fluid food-img" alt="Dish 1">
            </div>

            <div class="col-6 col-md-3">
                <img src="images/menu-2.jpg" class="img-fluid food-img" alt="Dish 2">
            </div>

            <div class="col-6 col-md-3">
                <img src="images/menu-3.jpg" class="img-fluid food-img" alt="Dish 3">
            </div>

            <div class="col-6 col-md-3">
                <img src="images/menu-4.jpg" class="img-fluid food-img" alt="Dish 4">
            </div>

        </div>
    </div>

</section>
<section class="py-5 overflow-hidden">
    <div class="container-fluid px-0">
        <div class="row g-0">

            <div class="col-3 col-lg-2 bg-noodles-image">
            </div>

            <div class="col-6 col-lg-8 d-flex flex-column justify-content-center align-items-center text-center" style="color:white;">
                <p class="hero-middle mb-4">Taste Our Meals and Get A Taste Of Asian Scenery</p>
                <p class="hero-tagline my-4">BREAKFAST</p>
                <p class="hero-tagline my-4">LUNCH</p>
                <p class="hero-tagline my-4">ALA CARTE</p>
                <p class="hero-tagline my-4">SUSHI</p>
                <p class="hero-tagline my-4">COCKTAILS</p>
                <div class="mt-4">
                    <img src="/images/mina-pot.png"
                         alt="Bowl of Noodles"
                         class="img-fluid"
                         style="max-width: 300px; height: auto; filter: drop-shadow(0px 20px 30px rgba(0,0,0,0.5));">
                </div>

            </div>

            <div class="col-3 col-lg-2">
            </div>

        </div>
    </div>
</section>
<section class="overflow-hidden" style="color:white; background-color: #000;">

    <div class="hero-copy-2 position-relative" style="z-index: 2;">
        <div class="text-center container">
            <p class="hero-middle mb-2">Our Story</p>

            <div class="hero-bottom-container">
                <p class="hero-bottom">
                    Discover the fresh, bold flavours of East and Southeast Asia at Mina’s Table.<br>
                    Our seasonal menu celebrates bright herbs, slow‑simmered depth<br>
                    and a touch of charcoal smoke, with plates that balance<br>
                    richness and freshness in every bite.<br><br>

                    Save room for dessert—light textures and gentle sweetness you’ll remember.<br>
                    Craving something classic? You’ll find comfort‑forward favourites<br>
                    alongside thoughtful, modern plates, with extensive gluten‑free, vegetarian<br>
                    and vegan choices all prepared with care and priced to welcome everyone.<br><br>

                    Join us in the dining room and let us take care of the rest.<br>
                    Reserve a table and enjoy the season’s menu in a<br>
                    warm, modern teahouse setting.
                </p>
            </div>
        </div>
    </div>

    <div class="intruder-container">
        <img src="/images/mina-lovers.png" class="intruding-image" alt="Background Element">
    </div>
    <div class="intruder-container intruder-footer">
        <img src="/images/mina-footer.png" class="intruding-image-2" alt="Background Element">
        <div class="hours-card-container">

            <!-- HOURS -->
            <div class="hours-card">
                <span class="corner tl"></span>
                <span class="corner tr"></span>
                <span class="corner bl"></span>
                <span class="corner br"></span>

                <div class="hours-row">
                    <div class="day">Monday</div>
                    <div class="time">Closed</div>
                </div>
                <div class="hours-row">
                    <div class="day">Tuesday</div>
                    <div class="time">Closed</div>
                </div>
                <div class="hours-row">
                    <div class="day">Wednesday</div>
                    <div class="time">10am - 9pm</div>
                </div>
                <div class="hours-row">
                    <div class="day">Thursday</div>
                    <div class="time">10am - 9pm</div>
                </div>
                <div class="hours-row">
                    <div class="day">Friday</div>
                    <div class="time">10am - 9pm</div>
                </div>
                <div class="hours-row">
                    <div class="day">Saturday</div>
                    <div class="time">10am - 9pm</div>
                </div>
                <div class="hours-row mb-0">
                    <div class="day">Sunday</div>
                    <div class="time">10am - 9pm</div>
                </div>
            </div>

            <!-- SOCIALS -->
            <div class="socials">
                <span class="corner tl"></span>
                <span class="corner tr"></span>
                <span class="corner bl"></span>
                <span class="corner br"></span>

                <div class="socials-title">SOCIALS</div>

                <div class="icons">
                    <a href="#"><i class="bi bi-facebook"></i></a>
                    <a href="#"><i class="bi bi-instagram"></i></a>
                </div>
            </div>

        </div>
        <p class="footer-copyright">
            © 2025 Mina’s Table. All rights reserved.
        </p>
    </div>

</section>


    <!-- SECOND NAV -->
    <div class="menu-overlay" id="menuOverlay">
        <div class="menu-panel">
            <div class="brand-header">
                <span class="brand-text">MINA'S</span>
                <div class="logo-wrapper">
                    <img src="/images/mina-food.png" alt="Logo" class="brand-logo">
                </div>
                <span class="brand-text">TABLE</span>
            </div>
            <nav class="nav-wrapper">
                <div class="nav-row">
                    <div class="menu-item-sketch">
                        <div class="line-h"></div>
                        <a href="#">Home Page</a>
                    </div>

                    <div class="menu-item-sketch">
                        <div class="line-h"></div>
                        <a href="#">Menu</a>
                    </div>

                    <div class="menu-item-sketch">
                        <div class="line-h"></div>
                        <a href="#">Reservation</a>
                    </div>
                </div>

                <div class="nav-row">
                    <div class="menu-item-sketch">
                        <div class="line-h"></div>
                        <a href="#">Locate Us</a>
                    </div>

                    <div class="menu-item-sketch close-item" id="closeMenu">
                        <div class="line-h"></div>
                        <a href="#">Close</a>
                    </div>
                </div>

            </nav>

        </div>
    </div>


<!-- Bootstrap JS (includes Popper) -->
<script src="/js/bootstrap.bundle.min.js"></script>
<script>
    const openMenu = document.getElementById("openMenu");
    const closeMenu = document.getElementById("closeMenu");
    const menuOverlay = document.getElementById("menuOverlay");

    openMenu.addEventListener("click", () => {
      menuOverlay.classList.add("active");
    });

    closeMenu.addEventListener("click", () => {
      menuOverlay.classList.remove("active");
    });
</script>

<script>
    const carousel = document.getElementById("imageCarousel");

    let isDown = false;
    let startX;
    let scrollLeft;

    // Smooth drag
    carousel.addEventListener("mousedown", e => {
      isDown = true;
      startX = e.pageX;
      scrollLeft = carousel.scrollLeft;
    });

    ["mouseup", "mouseleave"].forEach(evt =>
      carousel.addEventListener(evt, () => isDown = false)
    );

    carousel.addEventListener("mousemove", e => {
      if (!isDown) return;
      e.preventDefault();
      carousel.scrollLeft = scrollLeft - (e.pageX - startX) * 1.4;
    });

    function updateScale() {
      const cards = document.querySelectorAll(".carousel-card");
      const carouselRect = carousel.getBoundingClientRect();

      // 1. Calculate how far we've scrolled (0 to 1)
      const maxScroll = carousel.scrollWidth - carousel.clientWidth;
      const scrollProgress = carousel.scrollLeft / maxScroll;

      // 2. Define where the "pinch point" is.
      // We map scrollProgress (0 to 1) to a position across the container.
      // This makes the "pinch" move from left to right as you scroll.
      const pinchX = carouselRect.left + (carouselRect.width * scrollProgress);

      cards.forEach(card => {
        const rect = card.getBoundingClientRect();
        const cardCenter = rect.left + rect.width / 2;

        // 3. Distance from the moving pinch point
        const distanceToPinch = Math.abs(cardCenter - pinchX);
        const maxDistance = carouselRect.width;

        // 4. Calculate Scale
        // t = 0 at the pinch point, t = 1 far away.
        const t = Math.min(distanceToPinch / maxDistance, 1);

        // Base scale is 0.7 (small at pinch), max scale is 1.1 (large at edges)
        const minScale = 0.7;
        const maxScale = 1.1;
        const scale = minScale + (maxScale - minScale) * t;

        // Apply the transform
        card.style.transform = `scale(${scale})`;

        // Optional: Add a slight vertical offset to enhance the "bow" look
        const bowY = Math.pow(t, 2) * 20;
        card.style.transform += ` translateY(${bowY}px)`;
      });
    }


    carousel.addEventListener("scroll", updateScale);
    window.addEventListener("resize", updateScale);
    updateScale();
</script>


</body>
</html>
