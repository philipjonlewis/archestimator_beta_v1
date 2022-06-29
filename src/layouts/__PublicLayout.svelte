<script>
  import { Router, Link } from "svelte-navigator";
  import Navbar from "../components/navigation/Navbar.svelte";
  import Footer from "../components/navigation/Footer.svelte";
</script>

<Router>
  <div class="page-container">
    <Navbar />
    <div class="content-container">
      <slot />
    </div>
    <Footer />
  </div>
</Router>

<style lang="scss">
  .page-container {
    @apply container h-screen mx-auto flex flex-col justify-between;

    .content-container {
      @apply container h-full;
    }
  }
</style>
