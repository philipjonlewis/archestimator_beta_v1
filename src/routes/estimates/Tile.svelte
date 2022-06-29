<script lang="ts">
  let unitOfMeasurement;
  // let surfaceArea = 0;
  let floorArea = 0;
  let contingency;
  let tileDimensions = {
    width: 0,
    height: 0,
  };

  $: convertedContingency =
    Math.ceil((floorArea / surfaceArea) * toDecimal(contingency)) || 0;

  $: surfaceArea = tileDimensions.width * tileDimensions.height;

  $: totalNumberOfTiles =
    Math.ceil(floorArea / surfaceArea) + convertedContingency || 0;

  // $: console.log(unitOfMeasurement);
  // $: console.log(surfaceArea);
  $: console.log(totalNumberOfTiles);

  function toDecimal(num: any) {
    return parseFloat(num) / 100;
  }
</script>

<!-- <ContentLayout >Tiles</ContentLayout> -->

<div>
  <div>
    <p>Tiles : {Math.ceil(floorArea / surfaceArea) || 0}</p>
    <p>Contingency : {convertedContingency}</p>

    <p>
      Total Number of tiles = {totalNumberOfTiles}
    </p>
  </div>
  <br />
  <hr />
  <div class="unit-of-measurement">
    <p>
      Unit of Measurement : {unitOfMeasurement} - {unitOfMeasurement ==
      "Imperial"
        ? "ft / In"
        : "mm / cm"}
    </p>
    <select bind:value={unitOfMeasurement}>
      <option value={"Metric"}>Metric</option>
      <option value={"Imperial"}>Imperial</option>
    </select>
  </div>
  <br />
  <hr />
  <div class="floor-area">
    <form>
      <label for="floorArea">Floor Area</label>
      <input type="number" id="floorArea" bind:value={floorArea} />
    </form>
  </div>
  <br />
  <hr />
  <div class="tile-details">
    <form class="flex flex-col w-64">
      <p>Tile Surface Area = {surfaceArea}</p>
      <label for="tileWidth">Tile Width</label>
      <input type="number" id="tileWidth" bind:value={tileDimensions.width} />
      <label for="tileHeight">Tile Height</label>
      <input type="number" id="tileHeight" bind:value={tileDimensions.height} />
      <label for="contingency">contingency in percentage</label>
      <input type="number" id="contingency" bind:value={contingency} />
    </form>
  </div>

  <!-- <h5>Output</h5>
  <p>Tile Adhesive</p>
  <p>Tile Grout</p> -->
</div>

<style lang="scss">
</style>
