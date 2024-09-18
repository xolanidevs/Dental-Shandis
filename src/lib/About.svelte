<script>

</script>

<section class="container">
  <div class="wrapper">
    <div class="about-content">
      <h1>
        About <span>DentalShandis</span>
      </h1>  
      <p>At Ceramident we know that quality, efficiency and reliability are what our clients deserve.</p>
      <p>That is why our goal is to develop superior products, manufactured to exacting specifications, made from quality materials, using state-of-the-art technology by skilled technicians.</p>
      <p>As the dental industry steps further into the digital design and development age, we endeavour to consistently be at the forefront as a premium dental laboratory in Africa.</p>
      <p>For expertly produced and timeously delivered custom dental products – including: crowns and bridges, aesthetic veneers, implant supported prostheses, clear aligners and biteplates – get in touch with us today.</p>
      </div>
      <div>

        <button>
          Our Team
        </button>
      </div>
      <div class="about-img">
        <img src="/images/aboutImg.jpg" alt="image">
      </div>
  </div>
</section>
<style>

  /* Mobile */
  section {
  padding: 2rem;
  background: var(--background-gray); 
  color: var(--background);
}

.wrapper {
  max-width: 1200px;
  margin: 0 auto;
}

.about-content {
  margin-bottom: 2rem;
}

.about-content h1 {
  font-size: 2rem;
  margin-bottom: 1rem;
}

.about-content h1 span {
  color: var(--primary);
}

.about-content p {
  font-size: 1rem;
  line-height: 1.6;
  margin-bottom: 1rem;
}

button {
  background: var(--primary);
  color: var(--background);
  padding: 0.75rem 1.5rem;
  font-weight: bold;
  text-transform: uppercase;
  margin-bottom: 2rem;
}

.about-img {
  width: 100%;
  max-width: 500px;
  margin: 0 auto;
}

.about-img img {
  width: 100%;
  height: auto;
  border-radius: 10px;
}

@media (min-width: 768px) {
  .wrapper {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .about-content {
    text-align: center;
    max-width: 80%;
  }

  .about-img {
    margin-top: 2rem;
  }
}

@media (min-width: 1024px) {
  .wrapper {
    flex-direction: row;
    align-items: flex-start;
    justify-content: space-between;
    position: relative;
    padding-top: 3rem;
  }

  .about-content {
    text-align: left;
    max-width: 55%;
    padding-right: 2rem;
  }

  .about-content h1 {
    font-size: 2.5rem;
  }

  .about-img {
    position: absolute;
    right: 0;
    top: 50%;
    transform: translateY(-50%);
    max-width: 45%;
    margin-top: 0;
  }

  button {
    position: absolute;
    bottom: -20%;
    left: 25%;

  }
}

</style>
