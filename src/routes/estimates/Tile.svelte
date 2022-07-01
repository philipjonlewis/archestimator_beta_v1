<script lang="ts">
  //@ts-nocheck
  import { onMount } from "svelte";

  let tileData = {
    floorArea: 0,
    contingency: 0,
    tileDimensions: {
      width: 0,
      height: 0,
    },
  };

  $: tileArea = tileData.tileDimensions.width * tileData.tileDimensions.height;

  $: tileCount = Math.ceil(tileData.floorArea / tileArea || 0);

  $: tileCountWithContingency =
    Math.ceil(tileData.floorArea / tileArea) + convertedContingency;

  $: convertedContingency =
    Math.ceil(
      (tileData.floorArea / tileArea) * toDecimal(tileData.contingency)
    ) || 0;

  $: contingencyDisplay =
    isNaN(tileData.contingency) || tileData.contingency == null
      ? 0
      : tileData.contingency;

  function toDecimal(num: any) {
    return parseFloat(num) / 100;
  }

  onMount(() => {
    tileData.tileDimensions.width = localStorage.getItem("tileWidth") || 0;
    tileData.tileDimensions.height = localStorage.getItem("tileHeight") || 0;
    tileData.contingency = localStorage.getItem("tileContingency") || 0;
    tileData.floorArea = localStorage.getItem("floorArea") || 0;
  });
</script>

<!-- <ContentLayout >Tiles</ContentLayout> -->

<div class="tile-container">
  <p class="text-2xl font-bold mb-2 text-gray-600 py-2">Tile Estimates</p>
  <div class="results-container">
    <div class="tile-count-container">
      <p>Tile Count</p>
      <p>w/o contingency</p>
      <p>{tileCount === Infinity ? 0 : tileCount}</p>
    </div>
    <div class="tile-count-container">
      <p>Total Tile Count</p>
      <p>
        {contingencyDisplay}% Contingency at {convertedContingency} tiles
      </p>
      <p>
        {isNaN(tileCountWithContingency) ||
        tileCountWithContingency == Infinity ||
        tileCountWithContingency == null
          ? 0
          : tileCountWithContingency}
      </p>
    </div>
  </div>

  <form class="floor-area">
    <label for="floorArea">Floor Area</label>
    <input
      type="number"
      id="floorArea"
      bind:value={tileData.floorArea}
      on:input={() => {
        localStorage.setItem("floorArea", tileData.floorArea);
      }}
    />
  </form>

  <form class="tile-details">
    <div class="input-label-container">
      <label for="tileWidth">Tile Width</label>
      <input
        type="number"
        id="tileWidth"
        bind:value={tileData.tileDimensions.width}
        on:input={() => {
          localStorage.setItem("tileWidth", tileData.tileDimensions.width);
        }}
      />
    </div>

    <div class="input-label-container">
      <label for="tileHeight">Tile Height</label>
      <input
        type="number"
        id="tileHeight"
        bind:value={tileData.tileDimensions.height}
        on:input={() => {
          localStorage.setItem("tileHeight", tileData.tileDimensions.height);
        }}
      />
    </div>
  </form>
  <!-- <p>Tile Surface Area = {tileArea}</p> -->

  <form class="contingency-container">
    <label for="contingency">Contingency in %</label>
    <input
      type="number"
      id="contingency"
      min="0"
      bind:value={tileData.contingency}
      on:input={() => {
        localStorage.setItem("tileContingency", tileData.contingency);
      }}
    />
  </form>
  <button
    on:click={() => {
      tileData = {
        floorArea: 0,
        contingency: 0,
        tileDimensions: {
          width: 0,
          height: 0,
        },
      };

      localStorage.setItem("tileWidth", 0);
      localStorage.setItem("tileHeight", 0);
      localStorage.setItem("tileContingency", 0);
      localStorage.setItem("floorArea", 0);
    }}
    class="clear-button">Clear Fields</button
  >
  <!-- <h5>Output</h5>
  <p>Tile Adhesive</p>
  <p>Tile Grout</p> -->
</div>

<style lang="scss">
  .tile-container {
    @apply flex flex-col justify-start h-full w-fit;

    .results-container {
      @apply flex gap-2 border-b-[1px] mb-2 pb-2;

      @mixin result-common {
        @apply flex flex-col w-64 justify-center bg-stone-50 p-4 rounded-md hover:shadow-md transition-shadow text-center;

        p:nth-of-type(1) {
          @apply text-xl font-bold;
        }
        p:nth-of-type(2) {
          @apply text-xs mb-4 pb-2 border-b-[1px];
        }
        p:nth-of-type(3) {
          @apply text-base w-fit px-4 py-2 rounded-full mx-auto font-semibold;
        }
      }

      .tile-count-container:nth-of-type(1) {
        @include result-common();

        p:nth-of-type(1) {
          @apply text-gray-500;
        }
        p:nth-of-type(2) {
          @apply text-gray-500;
        }
        p:nth-of-type(3) {
          @apply border border-sky-200  text-sky-700;
        }
      }

      .tile-count-container:nth-of-type(2) {
        @include result-common();

        p:nth-of-type(1) {
          @apply text-amber-600;
        }
        p:nth-of-type(2) {
          @apply text-gray-500;
        }
        p:nth-of-type(3) {
          @apply text-gray-700 bg-amber-100 text-amber-600;
        }
      }
    }

    .floor-area {
      @apply flex flex-col h-fit  border-b-[1px] mb-2 pb-2;

      label {
        @apply text-sm font-semibold text-gray-700 pb-2  text-center;
      }

      input {
        @apply h-10 p-2 rounded-sm text-gray-600  text-center;
      }
    }

    .tile-details {
      @apply flex gap-2 border-b-[1px] mb-2 pb-2;

      .input-label-container {
        @apply flex flex-col w-64 justify-center;

        label {
          @apply text-sm font-semibold text-gray-700 pb-2 text-center;
        }

        input {
          @apply h-10 p-2 rounded-sm text-gray-600 text-center;
        }
      }
    }

    .contingency-container {
      @apply flex flex-col h-fit  border-b-[1px] mb-2 pb-2;

      label {
        @apply text-sm font-semibold text-gray-700 pb-2  text-center;
      }

      input {
        @apply h-10 p-2 rounded-sm text-gray-600  text-center;
      }
    }

    .clear-button {
      @apply w-fit rounded-md mt-8 border p-2 h-10 border-sky-200  text-sky-700 hover:bg-sky-700 hover:text-white transition-all hover:shadow-lg text-sm;
    }
  }
</style>
