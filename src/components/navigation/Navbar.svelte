<script>
  import { Router, Link } from "svelte-navigator";
  import Icon from "@iconify/svelte";

  let activeLink;

  const activeLinkHandler = (name) => {
    activeLink = name;
    console.log(activeLink);
  };
</script>

<nav
  class="flex justify-between items-center mb-2 py-4 font-sans text-sm border-b-[1px] border-gray-300 "
>
  <div>
    <Link to="/"><p class="logo">archestimator.</p></Link>
  </div>

  <div class="links-container">
    <Link to="/estimates/tile" on:click={() => activeLinkHandler("tile")}>
      <div class={activeLink == "tile" ? "active-link-item" : "link-item"}>
        <span>
          <Icon icon="icon-park-outline:floor-tile" height={24} />
        </span>
        <p>Tile</p>
      </div>
    </Link>

    <Link to="/estimates/paint" on:click={() => activeLinkHandler("paint")}>
      <div class={activeLink == "paint" ? "active-link-item" : "link-item"}>
        <Icon icon="clarity:paint-roller-solid" height={24} />
        <p>Paint</p>
      </div>
    </Link>
  </div>
</nav>

<style lang="scss">
  .logo {
    @apply text-orange-600 text-xl font-semibold;
    // background-color: yellow;

    font-family: "Space Grotesk", sans-serif;
  }

  .links-container {
    @apply flex gap-2 text-slate-700;

    @mixin link-common {
      @apply flex flex-col gap-2 text-sm justify-center items-center py-2 px-4 rounded-md border border-transparent;
    }

    .link-item {
      @include link-common();
      @apply hover:border-orange-600 hover:text-orange-600;
      // background-color: red;
    }

    .active-link-item {
      @include link-common();
      @apply bg-stone-100 text-orange-600;
    }
  }
</style>
