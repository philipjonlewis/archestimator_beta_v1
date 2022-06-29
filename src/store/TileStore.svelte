<script>
  // your script goes here
  import { writable } from "svelte/store";

  const tileValues = writable({
    unitOfMeasurement: "Metric",
    tileDimensions: {
      width: 0,
      height: 0,
      area: 0,
    },
    surfaceArea: 0,
    contingency: 0,
  });

  //   export const getTileArea = (obj) => {
  //     const tileArea = obj.tileDimensions.width * obj.tileDimensions.height;
  //     return {
  //       ...obj,
  //       tileDimensions: { ...obj.tileDimensions, area: tileArea },
  //     };
  //   };

  export { tileValues };

  //   count.subscribe((value) => {
  //     console.log(value);
  //   }); // logs '0'

  //   count.set(1); // logs '1'

  //   count.update((n) => n + 1); // logs '2'
</script>
