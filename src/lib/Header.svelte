<script>
  import { fade, fly } from 'svelte/transition';
  import { spring } from 'svelte/motion';
  
  let isMenuOpen = false;
  
  const toggleMenu = () => {
    isMenuOpen = !isMenuOpen;
  };
  
  const burgerSpring = spring({ x: 0, y: 0 }, {
    stiffness: 0.1,
    damping: 0.3
  });
  
  $: if (isMenuOpen) {
    burgerSpring.set({ x: 1, y: 1 });
  } else {
    burgerSpring.set({ x: 0, y: 0 });
  }
</script>

<header>
  <div class="logo">Dental<span>Shandis</span></div>
  
  <!-- Mobile -->
  <nav class="mobile-nav">
    <button class="burger" on:click={toggleMenu}>
      <div class="burger-icon" style="transform: rotate({$burgerSpring.x * 45}deg) translate({$burgerSpring.y * 5}px, {$burgerSpring.y * 5}px)"></div>
      <div class="burger-icon" style="transform: rotate({-$burgerSpring.x * 45}deg) translate({$burgerSpring.y * 5}px, {-$burgerSpring.y * 5}px)"></div>
    </button>
    
    {#if isMenuOpen}
      <div class="mobile-menu" transition:fly={{ y: -200, duration: 300 }}>
        <ul>
          <li><a href="/">Home</a></li>
          <li><a href="#about">About</a></li>
          <li><a href="#services">Services</a></li>
          <li><a href="#contact">Contact</a></li>
        </ul>
      </div>
    {/if}
  </nav>
  
  <!-- Desktop -->
  <nav class="desktop-nav">
    <ul>
      <li><a href="/">Home</a></li>
      <li><a href="#about">About</a></li>
      <li><a href="#services">Services</a></li>
    </ul>
    <!-- <div class="cta">
      <button class="primary"><a href="#contact">Get A Quote</a></button>
    </div> -->
  </nav>
</header>

<style>
  header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding:0 2rem;
    height: 10vh;
    z-index: 10000;
    background-color: transparent;
    width: 90%;
    position: fixed;
    top: 0;
    left: 50%;
    transform: translateX(-50%);
  }
  
  .logo {
    font-size: 1.5rem;
    font-weight: bold;
    color: var(--background);
  }

  .logo span{
    color: var(--primary);
  }
  
  .mobile-nav {
    display: block;
  }
  
  .desktop-nav {
    display: none;
  }
  
  .burger {
    background: none;
    border: none;
    cursor: pointer;
    padding: 0;
    width: 30px;
    height: 20px;
    position: relative;
  }
  
  .burger-icon {
    width: 100%;
    height: 2px;
    background-color: var(--primary);
    position: absolute;
    left: 0;
    transition: all 0.3s ease;
    z-index: 1;
  }
  
  .burger-icon:nth-child(1) { 
    top: 0;
   }

  .burger-icon:nth-child(2) {
    top: 50%;
    transform: translateY(-50%);
  }

  .burger-icon:nth-child(3) {
    bottom: 0;
    }
  
  .mobile-menu {
    position: absolute;
    background: rgba(0, 0, 0, .8);
    backdrop-filter: blur(3px);
    top: 0;
    left: 0;
    right: 0;
    padding: 1rem;
    width: 100%;
    height: 100vh;
  }

  .mobile-menu ul{
    position: absolute;
    left: 50%;
    /* right: 50%; */
    top: 10%;
    transform: translateX(-50%);
    font-size: 1.5rem;
  }

  .mobile-menu a{
    font-size: 1.5rem;
    text-transform: uppercase;
    font-weight: 600;
    letter-spacing: -0.05em;
  }


  ul {
    padding: 0;
    margin: 0; 
  }
  
  li {
    margin-bottom: 1rem;
  }

  
  
  a {
    text-decoration: none;
    color: var(--background);
    font-size: 1rem;
  }

  button {
    width: 100%;
    max-width: 250px;
    padding: 0.4rem 1rem;
   
    cursor: pointer;
    transition: background-color 0.3s, border .3s, color .3s;
    border: 1px solid var(--primary);
  }

  button a{
    font-size: .9rem;
    color: var(--primary);
  }

  .primary {
    background-color: transparent;
    color: var(--background);
  }
  
  button:hover {
    background: transparent;
    border: 1px solid var(--primary);
    color: var(--primary);
  }
  
  @media (min-width: 850px) {
    .mobile-nav {
      display: none;
    }
    
    .desktop-nav {
      display: block;
    }
    
    .desktop-nav ul {
      display: flex;
    }
    
    .desktop-nav li {
      margin-left: 1rem;
      margin-bottom: 0;
    }
  }

</style>