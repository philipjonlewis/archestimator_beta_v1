<script>
  import EstimationNavbar from "../components/navigation/EstimationNavbar.svelte";
</script>

<div class="h-full">
  <EstimationNavbar />
  <div class="slot-container">
    <slot />
  </div>
</div>

<style>
  .slot-container {
    height: calc(100% - 67px);
    /* background-color: red;
    display: flex;
    justify-content: flex-start;
    align-items: flex-start; */
  }
</style>
