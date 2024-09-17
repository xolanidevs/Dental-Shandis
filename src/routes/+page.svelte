<script>
  import '../style/app.css';
  import '../style/morden-normalize.css';
  import '../style/utils.css';
  import { onMount } from 'svelte';
  import { fade } from 'svelte/transition';

  // State variables for the typing effect
  let typedWord = '';
  const words = ["LEADING", "BEST", "ADVANCED"];
  let currentWordIndex = 0;
  let cursorVisible = true;
  let typingIndex = 0;
  let isDeleting = false;

  onMount(() => {
    // Set up the typing effect interval
    const typingInterval = setInterval(typeEffect, 100);
    
    // Set up the cursor blinking interval
    setInterval(() => {
      cursorVisible = !cursorVisible;
    }, 500);

    // Clean up intervals on component unmount
    return () => clearInterval(typingInterval);
  });

  // Function to handle the typing effect
  function typeEffect() {
    const currentWord = words[currentWordIndex];

    if (!isDeleting && typingIndex < currentWord.length) {
      // Typing forward
      typedWord += currentWord[typingIndex];
      typingIndex++;
    } else if (!isDeleting && typingIndex === currentWord.length) {
      // Finished typing the word, prepare to delete
      isDeleting = true;
      setTimeout(() => {
        typingIndex--;
      }, 1000); // Pause before deleting
    } else if (isDeleting && typingIndex > 0) {
      // Deleting the word
      typedWord = currentWord.substring(0, typingIndex - 1);
      typingIndex--;
    } else if (isDeleting && typingIndex === 0) {
      // Finished deleting, move to the next word
      isDeleting = false;
      currentWordIndex = (currentWordIndex + 1) % words.length;
    }
  }
</script>

<section class="hero">
  <div class="bg">
    <div class="hero-content container">
      <h1>
        AFRICA'S <span class="typed-word">{typedWord}<span class:blink={cursorVisible}>|</span></span><br> DENTAL LABORATORY
      </h1>
      <!-- Paragraph with fade-in effect -->
      <p transition:fade={{ delay: 1000, duration: 1000 }}>
        With 40 years as industry leader in the dental profession, Dental Shandis
        stands at the cutting edge of Dental Technology. Using only the best
        systems available we pride ourselves on innovative and highly precise
        manufacturing in order to provide our clients with top-tier products,
        consistently reliable service, and efficient process.
      </p>
      <!-- Buttons with fade-in effect -->
      <div class="cta-buttons" transition:fade={{ delay: 2000, duration: 1000 }}>
        <button class="primary">REQUEST A QUOTE</button>
        <button class="secondary">BOOK A COLLECTION</button>
      </div>
    </div>
  </div>
</section>

<style>
  .hero {
    min-height: 100vh;
    display: flex;
    align-items: center;
    background-image: url('/images/2.jpg');
    background-size: cover;
    background-position: center;
    color: var(--background);
    overflow: hidden;
    margin-top: 0;
  }

  .bg {
    background: rgba(0, 0, 0, .5);
    width: 100%;
    min-height: 100vh;
    padding: 2rem 0;
    display: flex;
    align-items: center;
  }

  .hero-content {
    padding: 1rem;
  }

  h1 {
    font-size: 2rem;
    font-weight:bolder;
    margin-bottom: 1rem;
    white-space: normal;
    line-height: 1.2;
  }

  .typed-word {
    color: var(--primary); 
    display: inline-block;
    min-width: 150px; 
    text-align: left;
  }

  .blink {
    opacity: 0;
    width: 5px;
  }

  p {
    font-size: 1rem;
    margin-bottom: 2rem;
    max-width: 100%;
    color: var(--slate-100);
  }

  .cta-buttons {
    display: flex;
    /* flex-direction: column; */
    gap: 1rem;
    align-items: center;
  }

  button {
    width: 100%;
    max-width: 250px;
    padding: 0.8rem 1rem;
    font-size: 0.7rem;
    cursor: pointer;
    transition: background-color 0.3s, border .3s, color .3s;
    border: 1px solid var(--primary);
  }

  .primary {
    background-color: var(--primary);
    color: var(--background);
  }

  .secondary {
    background-color: transparent;
    color: var(--primary);
  }
  
  button:hover {
    background: transparent;
    border: 1px solid var(--primary);
    color: var(--primary);
  }

  @media (min-width: 768px) {
    h1 {
      font-size: 2.5rem;
    }

    p {
      font-size: 1.1rem;
      max-width: 60ch;
      margin-left: auto;
      margin-right: auto;
    }

    .cta-buttons {
      flex-direction: row;
      justify-content: center;
    }

    button {
      width: auto;
    }
  }

  @media (min-width: 1024px) {
    .hero-content {
      text-align: left;
      padding: 2rem;
    }

    h1 {
      font-size: 3rem;
      white-space: nowrap;
    }

    .typed-word {
      min-width: 200px;
    }

    p {
      margin-left: 0;
      margin-right: 0;
    }

    .cta-buttons {
      justify-content: flex-start;
    }
  }
</style>



