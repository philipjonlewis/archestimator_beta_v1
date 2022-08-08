<script>
  import { Router, Link } from "svelte-navigator";
  import Icon from "@iconify/svelte";
  import { identity } from "svelte/internal";
  import { useLocation } from "svelte-navigator";
  const location = useLocation();

  let navLinks = [
    // {
    //   path: "/estimates/tile",
    //   name: "Tiles",
    //   icon: "icon-park-outline:floor-tile",
    // },
    // {
    //   path: "/estimates/paint",
    //   name: "Paint",
    //   icon: "clarity:paint-roller-solid",
    // },
    // {
    //   path: "/estimates/chb",
    //   name: "CHB",
    //   icon: "tabler:wall",
    // },
    // {
    //   path: "/estimates/wood",
    //   name: "Wood",
    //   icon: "mdi:hand-saw",
    // },
    // {
    //   path: "/estimates/hardware",
    //   name: "Hardware",
    //   icon: "uil:screw",
    // },
  ];
</script>

<nav class="lower-nav-container">
  <div class="links-container">
    {#each navLinks as { path, name, icon }}
      <Link to={path}>
        <div
          class={$location.pathname.includes(path)
            ? "active-link-item"
            : "link-item"}
        >
          <Icon {icon} height={24} />
          <p>{name}</p>
        </div>
      </Link>
    {/each}
  </div>
</nav>

<style lang="scss">
  .lower-nav-container {
    @apply flex flex-col gap-0 justify-between items-center mb-2  font-sans text-sm w-full;

    .links-container {
      @apply flex justify-start gap-0 w-full text-zinc-500 border-b-[1px] border-gray-200;

      @mixin link-common {
        @apply flex flex-col gap-2 text-sm justify-center items-center  pb-1 pt-2 rounded-t-sm border-b-2 border-transparent min-w-[6rem];
      }

      .link-item {
        @include link-common();
        @apply hover:bg-amber-50 hover:text-amber-600;
        // background-color: red;
      }

      .active-link-item {
        @include link-common();
        @apply bg-amber-50 text-amber-600 border-b-2 border-b-amber-600;
      }
    }
  }
</style>
