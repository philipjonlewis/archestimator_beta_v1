<script>
  import { Router, Link } from "svelte-navigator";
  import Navbar from "../components/navigation/Navbar.svelte";
  import Footer from "../components/navigation/Footer.svelte";
</script>

<Router>
  <div class="container h-screen mx-auto flex flex-col justify-between">
    <Navbar />
    <div class="main-container">
      <slot />
    </div>
    <Footer />
  </div>
</Router>

<style lang="scss">
  .main-container {
    @apply container h-full;
  }
</style>
