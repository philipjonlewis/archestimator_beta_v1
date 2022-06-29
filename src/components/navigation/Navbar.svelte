<script>
  import { Router, Link } from "svelte-navigator";
  import Icon from "@iconify/svelte";
  import { identity } from "svelte/internal";

  let activeLink;

  let navLinks = [
    {
      path: "/estimates/tile",
      name: "Tiles",
      icon: "icon-park-outline:floor-tile",
    },
    {
      path: "/estimates/paint",
      name: "Paint",
      icon: "clarity:paint-roller-solid",
    },
    {
      path: "/estimates/chb",
      name: "CHB",
      icon: "tabler:wall",
    },
    {
      path: "/estimates/wall",
      name: "Wood",
      icon: "mdi:hand-saw",
    },
    {
      path: "/estimates/hardware",
      name: "Hardware",
      icon: "uil:screw",
    },
  ];

  const activeLinkHandler = (name) => {
    activeLink = name;
    console.log(activeLink);
  };
</script>

<nav class="nav-container">
  <div>
    <Link to="/"><p class="logo">archestimator.</p></Link>
  </div>

  <div class="links-container">
    {#each navLinks as { path, name, icon }}
      <Link to={path} on:click={() => activeLinkHandler(name)}>
        <div class={activeLink == name ? "active-link-item" : "link-item"}>
          <Icon {icon} height={24} />
          <p>{name}</p>
        </div>
      </Link>
    {/each}
  </div>
</nav>

<style lang="scss">
  .nav-container {
    @apply flex justify-between items-center mb-2 py-4 font-sans text-sm;

    .logo {
      @apply text-orange-600 text-xl font-semibold;
      // background-color: yellow;

      font-family: "Space Grotesk", sans-serif;
    }

    .links-container {
      @apply flex gap-1 text-slate-600;

      @mixin link-common {
        @apply flex flex-col gap-2 text-sm justify-center items-center py-1 rounded-t-sm border-b-2 border-transparent min-w-[6rem];
      }

      .link-item {
        @include link-common();
        @apply hover:bg-stone-100 hover:text-orange-600;
        // background-color: red;
      }

      .active-link-item {
        @include link-common();
        @apply bg-orange-50 text-orange-600 border-b-2 border-b-orange-600;
      }
    }
  }
</style>
