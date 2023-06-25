<script>
  import '../app.css';
  import Header from "$lib/Header.svelte";
  import Footer from "$lib/Footer.svelte";
  
  
</script>

<Header />

<main>
  <slot />
</main>

<Footer />

<style>
  main {
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    background-color: #333;
    color: #f4f4f4;
    padding: 50px 0;
  }
</style>
