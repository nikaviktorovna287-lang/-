<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="description" content="Крафтовая пекарня «Пан Пышка» — свежий хлеб на закваске, круассаны, багеты и десерты. Утренние акции и программа лояльности.">
  <title>Пан Пышка — крафтовая пекарня</title>
  <style>
    /* ---------- ПЕРЕМЕННЫЕ ---------- */
    :root {
      --gold: #d4a373;
      --gold-dark: #b8834f;
      --wheat: #e9d8b6;
      --cream: #faf3e0;
      --chocolate: #6b4f3a;
      --dark-choco: #4a2e1e;
      --warm-white: #fffcf5;
      --bg: #fdf8f0;
      --text-muted: #7b5e47;

      --shadow-sm: 0 8px 20px rgba(107, 79, 58, 0.08);
      --shadow-md: 0 14px 30px rgba(107, 79, 58, 0.12);
      --shadow-lg: 0 22px 45px rgba(107, 79, 58, 0.18);

      --radius-sm: 14px;
      --radius-md: 24px;
      --radius-lg: 36px;

      --transition: 0.35s cubic-bezier(0.22, 1, 0.36, 1);
      --container: 1200px;
    }

    /* ---------- СБРОС ---------- */
    *,
    *::before,
    *::after {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    html {
      scroll-behavior: smooth;
      -webkit-text-size-adjust: 100%;
    }

    body {
      font-family: 'Segoe UI', 'Roboto', system-ui, -apple-system, sans-serif;
      background-color: var(--bg);
      color: var(--dark-choco);
      line-height: 1.6;
      overflow-x: hidden;
    }

    img, svg {
      max-width: 100%;
      display: block;
    }

    a {
      color: inherit;
      text-decoration: none;
    }

    ul {
      list-style: none;
    }

    button {
      font: inherit;
      border: none;
      background: none;
      cursor: pointer;
      color: inherit;
    }

    /* ---------- КОНТЕЙНЕР ---------- */
    .container {
      width: 100%;
      max-width: var(--container);
      margin: 0 auto;
      padding: 0 24px;
    }

    /* ---------- ШАПКА ---------- */
    .navbar {
      position: sticky;
      top: 0;
      z-index: 100;
      background-color: rgba(250, 243, 224, 0.9);
      backdrop-filter: blur(12px);
      -webkit-backdrop-filter: blur(12px);
      box-shadow: 0 4px 14px rgba(107, 79, 58, 0.07);
      transition: var(--transition);
    }

    .nav-container {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 24px;
      padding: 14px 24px;
      max-width: var(--container);
      margin: 0 auto;
    }

    .logo {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      font-size: 1.6rem;
      font-weight: 800;
      color: var(--chocolate);
      letter-spacing: -0.5px;
      transition: var(--transition);
    }

    .logo:hover {
      transform: translateY(-1px);
      color: var(--gold-dark);
    }

    .logo__icon {
      font-size: 1.9rem;
      line-height: 1;
    }

    .nav-links {
      display: flex;
      align-items: center;
      gap: 28px;
    }

    .nav-links a {
      position: relative;
      font-weight: 600;
      font-size: 1rem;
      color: var(--dark-choco);
      padding: 6px 0;
      transition: color var(--transition);
    }

    .nav-links a::after {
      content: '';
      position: absolute;
      left: 0;
      bottom: 0;
      width: 100%;
      height: 2px;
      background: var(--gold);
      transform: scaleX(0);
      transform-origin: right;
      transition: transform var(--transition);
      border-radius: 2px;
    }

    .nav-links a:hover {
      color: var(--gold-dark);
    }

    .nav-links a:hover::after {
      transform: scaleX(1);
      transform-origin: left;
    }

    /* Бургер */
    .nav-toggle {
      display: none;
      flex-direction: column;
      gap: 5px;
      padding: 8px;
      border-radius: 10px;
      transition: background var(--transition);
    }

    .nav-toggle:hover {
      background: var(--wheat);
    }

    .nav-toggle span {
      width: 24px;
      height: 2.5px;
      background: var(--chocolate);
      border-radius: 3px;
      transition: var(--transition);
    }

    /* ---------- ГЕРОЙ ---------- */
    .hero {
      position: relative;
      overflow: hidden;
      padding: 90px 0 110px;
      background:
        radial-gradient(1200px 600px at 85% 15%, rgba(212, 163, 115, 0.35), transparent 60%),
        linear-gradient(135deg, #f7e9d7 0%, #f1dfc5 100%);
      border-bottom: 2px dashed rgba(212, 163, 115, 0.35);
    }

    .hero::before {
      content: '';
      position: absolute;
      inset: 0;
      background-image:
        radial-gradient(circle at 10% 20%, rgba(255, 255, 255, 0.6) 0 2px, transparent 3px),
        radial-gradient(circle at 80% 70%, rgba(255, 255, 255, 0.5) 0 2px, transparent 3px);
      background-size: 120px 120px, 180px 180px;
      opacity: 0.5;
      pointer-events: none;
    }

    .hero::after {
      content: "🌾🥖🥐";
      position: absolute;
      right: 4%;
      bottom: 6%;
      font-size: clamp(4rem, 9vw, 9rem);
      opacity: 0.12;
      transform: rotate(8deg);
      pointer-events: none;
      white-space: nowrap;
      filter: blur(0.4px);
    }

    .hero__content {
      position: relative;
      z-index: 2;
      max-width: 680px;
    }

    .hero__badge {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      background: rgba(255, 255, 255, 0.7);
      border: 1px solid rgba(212, 163, 115, 0.5);
      color: var(--chocolate);
      font-weight: 600;
      font-size: 0.9rem;
      padding: 8px 16px;
      border-radius: 999px;
      margin-bottom: 22px;
      box-shadow: var(--shadow-sm);
    }

    .hero h1 {
      font-size: clamp(2.2rem, 6vw, 3.8rem);
      font-weight: 800;
      line-height: 1.15;
      margin-bottom: 22px;
      text-shadow: 2px 2px 0 rgba(212, 163, 115, 0.18);
    }

    .hero h1 .highlight {
      position: relative;
      color: var(--gold-dark);
      white-space: nowrap;
    }

    .hero h1 .highlight::after {
      content: '';
      position: absolute;
      left: -2px;
      right: -2px;
      bottom: 4px;
      height: 14px;
      background: rgba(212, 163, 115, 0.35);
      border-radius: 8px;
      z-index: -1;
      transform: skewX(-8deg);
    }

    .hero p {
      font-size: clamp(1rem, 2.2vw, 1.2rem);
      color: #5f4633;
      margin-bottom: 34px;
      max-width: 540px;
    }

    .hero__actions {
      display: flex;
      flex-wrap: wrap;
      gap: 14px;
      align-items: center;
    }

    .btn {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 10px;
      padding: 16px 36px;
      border-radius: 999px;
      font-weight: 700;
      font-size: 1.05rem;
      letter-spacing: 0.3px;
      transition: var(--transition);
      border: 2px solid transparent;
      cursor: pointer;
      will-change: transform;
    }

    .btn--primary {
      background: var(--chocolate);
      color: #fff;
      box-shadow: 0 10px 22px rgba(107, 79, 58, 0.25);
    }

    .btn--primary:hover,
    .btn--primary:focus-visible {
      background: var(--gold);
      color: var(--dark-choco);
      border-color: var(--chocolate);
      transform: translateY(-4px);
      box-shadow: 0 18px 32px rgba(212, 163, 115, 0.4);
      outline: none;
    }

    .btn--ghost {
      background: rgba(255, 255, 255, 0.7);
      color: var(--chocolate);
      border-color: rgba(107, 79, 58, 0.25);
    }

    .btn--ghost:hover,
    .btn--ghost:focus-visible {
      background: #fff;
      border-color: var(--gold);
      transform: translateY(-4px);
      box-shadow: var(--shadow-md);
      outline: none;
    }

    /* ---------- СЕКЦИИ ---------- */
    section {
      padding: 80px 0;
    }

    .section-head {
      text-align: center;
      margin-bottom: 52px;
    }

    .section-title {
      display: inline-block;
      position: relative;
      font-size: clamp(1.8rem, 4vw, 2.4rem);
      font-weight: 800;
      color: var(--dark-choco);
      margin-bottom: 14px;
      letter-spacing: -0.5px;
    }

    .section-title::after {
      content: '';
      display: block;
      width: 72px;
      height: 4px;
      background: linear-gradient(90deg, var(--gold), var(--wheat));
      border-radius: 4px;
      margin: 12px auto 0;
    }

    .section-subtitle {
      max-width: 640px;
      margin: 0 auto;
      color: var(--text-muted);
      font-size: 1.05rem;
    }

    /* ---------- О НАС ---------- */
    .about-grid {
      display: grid;
      grid-template-columns: 1.1fr 0.9fr;
      gap: 56px;
      align-items: center;
    }

    .about-text .accent {
      display: inline-block;
      background: var(--wheat);
      color: var(--dark-choco);
      padding: 6px 16px;
      border-radius: 999px;
      font-weight: 600;
      font-size: 0.9rem;
      margin-bottom: 16px;
    }

    .about-text h3 {
      font-size: clamp(1.5rem, 3vw, 1.9rem);
      color: var(--chocolate);
      margin-bottom: 18px;
      line-height: 1.25;
    }

    .about-text p {
      margin-bottom: 16px;
      font-size: 1.03rem;
      color: #4f3827;
    }

    .about-text p strong {
      color: var(--chocolate);
    }

    .about-image {
      position: relative;
      display: grid;
      place-items: center;
      min-height: 320px;
      padding: 40px;
      font-size: clamp(4rem, 9vw, 7rem);
      line-height: 1;
      background:
        radial-gradient(circle at 30% 30%, #fffcf5, #f0dfc4 70%);
      border-radius: 60% 40% 55% 45% / 50% 55% 45% 50%;
      box-shadow: var(--shadow-md);
      transition: var(--transition);
      user-select: none;
    }

    .about-image:hover {
      border-radius: 45% 55% 40% 60% / 55% 45% 60% 40%;
      transform: scale(1.03) rotate(-1deg);
      box-shadow: var(--shadow-lg);
    }

    /* ---------- МЕНЮ ---------- */
    .menu-section {
      background: linear-gradient(180deg, #f7ede0 0%, #fdf8f0 100%);
    }

    .menu-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
      gap: 28px;
    }

    .menu-card {
      position: relative;
      display: flex;
      flex-direction: column;
      align-items: center;
      text-align: center;
      padding: 32px 22px 26px;
      background: var(--warm-white);
      border-radius: var(--radius-md);
      border: 1px solid rgba(212, 163, 115, 0.25);
      box-shadow: var(--shadow-sm);
      overflow: hidden;
      transition: var(--transition);
      will-change: transform;
    }

    .menu-card::before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 6px;
      background: linear-gradient(90deg, var(--gold), var(--wheat));
      opacity: 0.55;
      transition: var(--transition);
    }

    .menu-card::after {
      content: '';
      position: absolute;
      inset: 0;
      background: radial-gradient(circle at 50% -20%, rgba(212, 163, 115, 0.18), transparent 60%);
      opacity: 0;
      transition: var(--transition);
      pointer-events: none;
    }

    .menu-card:hover {
      transform: translateY(-12px);
      border-color: var(--gold);
      box-shadow: var(--shadow-lg);
    }

    .menu-card:hover::before {
      height: 10px;
      opacity: 1;
    }

    .menu-card:hover::after {
      opacity: 1;
    }

    .menu-emoji {
      font-size: 3.6rem;
      margin-bottom: 14px;
      transition: var(--transition);
      filter: drop-shadow(2px 6px 8px rgba(107, 79, 58, 0.18));
    }

    .menu-card:hover .menu-emoji {
      transform: scale(1.18) rotate(-4deg);
    }

    .menu-card h3 {
      font-size: 1.3rem;
      margin-bottom: 8px;
      color: var(--dark-choco);
    }

    .menu-card .description {
      font-size: 0.95rem;
      color: #856b55;
      line-height: 1.45;
      margin-bottom: 18px;
      flex-grow: 1;
    }

    .price {
      display: inline-block;
      padding: 8px 22px;
      font-size: 1.4rem;
      font-weight: 800;
      color: var(--chocolate);
      background: var(--cream);
      border-radius: 999px;
      border: 1px dashed var(--gold);
      transition: var(--transition);
    }

    .menu-card:hover .price {
      background: var(--gold);
      color: #fff;
      border-style: solid;
    }

    /* ---------- АКЦИИ ---------- */
    .promo-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
      gap: 28px;
    }

    .promo-card {
      position: relative;
      display: flex;
      flex-direction: column;
      gap: 14px;
      padding: 36px 30px;
      background: linear-gradient(145deg, #ffffff, #faf1e2);
      border-radius: var(--radius-lg);
      border-left: 8px solid var(--gold);
      box-shadow: var(--shadow-sm);
      transition: var(--transition);
      overflow: hidden;
    }

    .promo-card::after {
      content: '';
      position: absolute;
      right: -40px;
      bottom: -40px;
      width: 160px;
      height: 160px;
      background: radial-gradient(circle, rgba(212, 163, 115, 0.25), transparent 70%);
      opacity: 0;
      transition: var(--transition);
      pointer-events: none;
    }

    .promo-card:hover {
      transform: translateY(-8px) scale(1.015);
      box-shadow: var(--shadow-lg);
      border-left-color: var(--chocolate);
    }

    .promo-card:hover::after {
      opacity: 1;
    }

    .promo-badge {
      align-self: flex-start;
      background: var(--gold);
      color: var(--dark-choco);
      font-weight: 700;
      font-size: 0.85rem;
      letter-spacing: 0.4px;
      padding: 6px 16px;
      border-radius: 999px;
    }

    .promo-card h3 {
      font-size: 1.55rem;
      line-height: 1.25;
      color: var(--dark-choco);
    }

    .promo-card p {
      color: #5f4633;
      font-size: 1rem;
    }

    .promo-time {
      display: inline-block;
      align-self: flex-start;
      font-weight: 700;
      color: var(--chocolate);
      background: var(--wheat);
      padding: 5px 14px;
      border-radius: 999px;
      font-size: 0.92rem;
    }

    .promo-price {
      font-weight: 700;
      color: var(--chocolate);
      font-size: 1.05rem;
    }

    /* ---------- ЛОЯЛЬНОСТЬ ---------- */
    .loyalty {
      display: grid;
      grid-template-columns: 1fr 1.2fr;
      gap: 44px;
      align-items: center;
      padding: 60px 48px;
      background: linear-gradient(120deg, #f7e9d7, #f3e1c9);
      border-radius: 80px 24px 80px 24px;
      box-shadow: inset 0 0 0 2px rgba(212, 163, 115, 0.3), var(--shadow-sm);
    }

    .loyalty-stamps {
      display: flex;
      flex-wrap: wrap;
      gap: 14px;
      justify-content: center;
    }

    .stamp {
      width: 72px;
      height: 72px;
      display: grid;
      place-items: center;
      font-size: 2rem;
      background: var(--warm-white);
      border-radius: 50%;
      border: 2px solid var(--gold);
      box-shadow: 0 6px 0 var(--wheat), 0 12px 18px rgba(107, 79, 58, 0.1);
      transition: var(--transition);
      cursor: default;
    }

    .stamp:hover {
      transform: translateY(-8px);
      box-shadow: 0 14px 0 var(--gold), 0 20px 28px rgba(212, 163, 115, 0.4);
    }

    .loyalty-text h3 {
      font-size: clamp(1.6rem, 3.2vw, 2rem);
      color: var(--dark-choco);
      margin-bottom: 18px;
    }

    .loyalty-text p {
      font-size: 1.05rem;
      margin-bottom: 16px;
      color: #4f3827;
    }

    .loyalty-text .highlight {
      font-weight: 700;
      color: var(--chocolate);
      background: rgba(212, 163, 115, 0.35);
      padding: 2px 10px;
      border-radius: 999px;
    }

    .loyalty-note {
      font-style: italic;
      color: #6b4f3a;
      font-size: 0.95rem;
    }

    /* ---------- КОНТАКТЫ ---------- */
    .contacts-wrapper {
      display: grid;
      grid-template-columns: 0.9fr 1.1fr;
      gap: 32px;
    }

    .contact-info {
      padding: 38px 32px;
      background: var(--warm-white);
      border-radius: var(--radius-md);
      box-shadow: var(--shadow-sm);
      transition: var(--transition);
    }

    .contact-info:hover {
      box-shadow: var(--shadow-md);
      transform: translateY(-4px);
    }

    .contact-info h3 {
      font-size: 1.7rem;
      color: var(--dark-choco);
      margin-bottom: 26px;
    }

    .contact-item {
      display: flex;
      align-items: center;
      gap: 16px;
      margin-bottom: 22px;
      font-size: 1.05rem;
      color: #4f3827;
    }

    .contact-item:last-child {
      margin-bottom: 0;
    }

    .emoji-icon {
      flex-shrink: 0;
      width: 52px;
      height: 52px;
      display: grid;
      place-items: center;
      font-size: 1.7rem;
      background: var(--wheat);
      border-radius: 50%;
      transition: var(--transition);
    }

    .contact-info:hover .emoji-icon {
      background: var(--gold);
      transform: rotate(-6deg);
    }

    .contact-item a {
      transition: color var(--transition);
    }

    .contact-item a:hover {
      color: var(--gold-dark);
    }

    .map-container {
      position: relative;
      min-height: 340px;
      border-radius: var(--radius-md);
      overflow: hidden;
      border: 2px solid var(--wheat);
      box-shadow: var(--shadow-sm);
      transition: var(--transition);
      background:
        linear-gradient(135deg, #e8d9c0 0%, #d9c7ac 100%);
    }

    .map-container:hover {
      border-color: var(--gold);
      box-shadow: var(--shadow-md);
    }

    .map-placeholder {
      position: absolute;
      inset: 0;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      gap: 10px;
      padding: 30px;
      text-align: center;
      color: var(--chocolate);
      font-weight: 600;
    }

    .map-placeholder::before {
      content: '';
      position: absolute;
      inset: 0;
      background-image:
        linear-gradient(rgba(107, 79, 58, 0.08) 1px, transparent 1px),
        linear-gradient(90deg, rgba(107, 79, 58, 0.08) 1px, transparent 1px);
      background-size: 40px 40px;
      opacity: 0.7;
    }

    .map-placeholder > * {
      position: relative;
      z-index: 1;
    }

    .map-placeholder .map-emoji {
      font-size: 3.8rem;
      animation: float 3s ease-in-out infinite;
    }

    @keyframes float {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(-8px); }
    }

    /* ---------- ПОДВАЛ ---------- */
    footer {
      margin-top: 40px;
      padding: 40px 20px 32px;
      background: var(--chocolate);
      color: var(--cream);
      text-align: center;
    }

    footer p {
      font-size: 0.95rem;
      opacity: 0.9;
    }

    .footer-love {
      margin-top: 8px;
      font-size: 1.1rem;
      opacity: 0.85;
    }

    /* ---------- АНИМАЦИЯ ПОЯВЛЕНИЯ ---------- */
    .reveal {
      opacity: 0;
      transform: translateY(28px);
      transition: opacity 0.7s ease, transform 0.7s ease;
    }

    .reveal.is-visible {
      opacity: 1;
      transform: translateY(0);
    }

    /* ---------- ЯКОРЯ ---------- */
    section[id] {
      scroll-margin-top: 90px;
    }

    /* ---------- АДАПТИВ ---------- */
    @media (max-width: 992px) {
      .about-grid,
      .loyalty,
      .contacts-wrapper {
        grid-template-columns: 1fr;
      }

      .loyalty {
        border-radius: 48px 24px 48px 24px;
        padding: 48px 28px;
        text-align: center;
      }

      .loyalty-text .highlight {
        display: inline-block;
        margin: 2px 0;
      }

      .about-image {
        min-height: 260px;
      }
    }

    @media (max-width: 768px) {
      .nav-container {
        padding: 12px 20px;
      }

      .nav-toggle {
        display: flex;
      }

      .nav-links {
        position: absolute;
        top: 100%;
        left: 0;
        right: 0;
        flex-direction: column;
        align-items: stretch;
        gap: 0;
        background: rgba(250, 243, 224, 0.98);
        backdrop-filter: blur(12px);
        box-shadow: var(--shadow-md);
        max-height: 0;
        overflow: hidden;
        transition: max-height 0.4s ease;
      }

      .nav-links.is-open {
        max-height: 420px;
      }

      .nav-links li {
        border-bottom: 1px solid rgba(212, 163, 115, 0.25);
      }

      .nav-links a {
        display: block;
        padding: 16px 24px;
        font-size: 1rem;
      }

      .nav-links a::after {
        display: none;
      }

      .hero {
        padding: 60px 0 80px;
        text-align: center;
      }

      .hero__content {
        margin: 0 auto;
      }

      .hero p {
        margin-left: auto;
        margin-right: auto;
      }

      .hero__actions {
        justify-content: center;
      }

      .hero::after {
        font-size: 4.5rem;
        right: -20px;
        bottom: 0;
        opacity: 0.1;
      }

      section {
        padding: 64px 0;
      }

      .menu-grid,
      .promo-grid {
        gap: 22px;
      }

      .contact-item {
        font-size: 1rem;
      }

      .emoji-icon {
        width: 46px;
        height: 46px;
        font-size: 1.5rem;
      }
    }

    @media (max-width: 480px) {
      .container {
        padding: 0 18px;
      }

      .nav-container {
        padding: 10px 16px;
      }

      .logo {
        font-size: 1.35rem;
      }

      .logo__icon {
        font-size: 1.6rem;
      }

      .hero h1 {
        font-size: 2rem;
      }

      .btn {
        width: 100%;
        padding: 14px 24px;
        font-size: 1rem;
      }

      .hero__actions {
        flex-direction: column;
      }

      .section-title {
        font-size: 1.6rem;
      }

      .menu-card {
        padding: 26px 18px 22px;
      }

      .menu-emoji {
        font-size: 3rem;
      }

      .promo-card {
        padding: 28px 22px;
      }

      .promo-card h3 {
        font-size: 1.3rem;
      }

      .loyalty {
        padding: 36px 20px;
        border-radius: 32px 16px 32px 16px;
      }

      .stamp {
        width: 58px;
        height: 58px;
        font-size: 1.6rem;
      }

      .contact-info {
        padding: 28px 22px;
      }
    }

    /* ---------- ДОСТУПНОСТЬ / MOTION ---------- */
    @media (prefers-reduced-motion: reduce) {
      html {
        scroll-behavior: auto;
      }

      *,
      *::before,
      *::after {
        animation-duration: 0.001ms !important;
        animation-iteration-count: 1 !important;
        transition-duration: 0.001ms !important;
      }

      .reveal {
        opacity: 1;
        transform: none;
      }
    }

    /* Фокус для клавиатуры */
    a:focus-visible,
    button:focus-visible {
      outline: 3px solid var(--gold);
      outline-offset: 3px;
      border-radius: 8px;
    }
  </style>
</head>
<body>
  <!-- ШАПКА -->
  <header class="navbar">
    <div class="nav-container">
      <a href="#home" class="logo" aria-label="Пан Пышка — на главную">
        <span class="logo__icon" aria-hidden="true">🥖</span>
        Пан Пышка
      </a>

      <button class="nav-toggle" type="button" aria-label="Открыть меню" aria-expanded="false" aria-controls="nav-links">
        <span></span>
        <span></span>
        <span></span>
      </button>

      <nav>
        <ul class="nav-links" id="nav-links">
          <li><a href="#about">О нас</a></li>
          <li><a href="#menu">Меню</a></li>
          <li><a href="#hits">Хиты</a></li>
          <li><a href="#reviews">Отзывы</a></li>
          <li><a href="#contacts">Контакты</a></li>
        </ul>
      </nav>
    </div>
  </header>

  <main>
    <!-- ГЕРОЙ -->
    <section class="hero" id="home">
      <div class="container">
        <div class="hero__content">
          <span class="hero__badge">🌾 На закваске с 2014 года</span>
          <h1>Свежий хлеб и <span class="highlight">любовь</span> с раннего утра</h1>
          <p>Пекарня «Пан Пышка» — здесь тесто подходит на закваске, а сердце — на доброте. Заходите за ароматным настроением!</p>
          <div class="hero__actions">
            <a href="#menu" class="btn btn--primary">Заглянуть в меню →</a>
            <a href="#contacts" class="btn btn--ghost">Как добраться</a>
          </div>
        </div>
      </div>
    </section>

    <!-- О ПЕКАРНЕ -->
    <section id="about">
      <div class="container">
        <div class="section-head reveal">
          <h2 class="section-title">О пекарне</h2>
          <p class="section-subtitle">Наша история — это slow food, закваска и любовь к традициям</p>
        </div>

        <div class="about-grid">
          <div class="about-text reveal">
            <span class="accent">🌾 С 2014 года на закваске</span>
            <h3>Хлеб, который дышит историей</h3>
            <p>Мы начинали с маленькой печи и одной банки ржаной закваски, которую бережно храним и «кормим» каждый день. Наши бабушки пекли хлеб в русских печах — мы продолжаем эту традицию, добавляя лишь муку, воду, соль и время.</p>
            <p>В «Пан Пышке» нет места ускорителям и улучшителям. Только длительная ферментация, ручная формовка и печь на камне. Приходите попробовать настоящий крафт — от багета до чиабатты.</p>
            <p><strong>Каждое утро в 7:00</strong> мы открываем двери, чтобы вы уловили тёплый запах свежего хлеба.</p>
          </div>

          <div class="about-image reveal" aria-hidden="true">
            🥨🍞🥐
          </div>
        </div>
      </div>
    </section>

    <!-- МЕНЮ -->
    <section id="menu" class="menu-section">
      <div class="container">
        <div class="section-head reveal">
          <h2 class="section-title">Наше меню</h2>
          <p class="section-subtitle">6 фирменных изделий, которые пекутся с душой каждое утро</p>
        </div>

        <div class="menu-grid">
          <article class="menu-card reveal">
            <div class="menu-emoji" aria-hidden="true">🥐</div>
            <h3>Круассан с миндалем</h3>
            <p class="description">Слоёный, с нежной миндальной пастой и хрустящими лепестками</p>
            <div class="price">189 ₽</div>
          </article>

          <article class="menu-card reveal">
            <div class="menu-emoji" aria-hidden="true">🥖</div>
            <h3>Багет французский</h3>
