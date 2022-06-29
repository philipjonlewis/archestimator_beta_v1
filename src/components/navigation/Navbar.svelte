<script>
  import { Router, Link } from "svelte-navigator";

  import { useLocation } from "svelte-navigator";
  const location = useLocation();
</script>

<nav class="upper-container">
  <div class="upper-nav-container">
    <div>
      <Link to="/home"><p class="logo">archestimator.</p></Link>
    </div>
    <div class="flex items-center gap-4 text-gray-800">
      <Link to="/home">
        <div
          class={$location.pathname.includes("home")
            ? "active-link-item"
            : "link-item"}
        >
          <p>Home</p>
        </div>
      </Link>
      <Link to="about">
        <div
          class={$location.pathname.includes("about")
            ? "active-link-item"
            : "link-item"}
        >
          <p>About</p>
        </div>
      </Link>
      <Link to="contact">
        <div
          class={$location.pathname.includes("contact")
            ? "active-link-item"
            : "link-item"}
        >
          <p>Contact</p>
        </div>
      </Link>
      <Link to="estimates">
        <div
          class={$location.pathname.includes("estimates")
            ? "active-link-item"
            : "link-item"}
        >
          <p>Estimates</p>
        </div>
      </Link>
    </div>
  </div>
</nav>

<style lang="scss">
  .upper-container {
    @apply flex flex-col gap-0 justify-between items-center font-sans text-sm w-full;

    .upper-nav-container {
      @apply flex justify-between w-full py-4 border-b-[1px] border-gray-200;

      .logo {
        @apply flex justify-center items-center text-amber-600 text-xl font-semibold w-full h-full;
        // background-color: yellow;

        font-family: "Space Grotesk", sans-serif;
      }

      @mixin link-common {
        @apply flex flex-col text-sm justify-center items-center px-4 py-2  rounded-md text-stone-600;
      }

      .link-item {
        @include link-common();
        @apply hover:bg-amber-50 hover:text-amber-600;
        // background-color: red;
      }

      .active-link-item {
        @include link-common();
        @apply bg-amber-50 text-amber-600;
      }
    }
  }
</style>
