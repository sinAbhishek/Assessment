<script>
  import main from "../../../data/data.js";
  export let data;

  const filter = main.filter(
    (c) => c.name.toLowerCase() === data.params.id.toLowerCase()
  );
</script>

<div class=" w-screen h-max flex flex-col justify-center items-center">
  {#each filter[0].touristplaces as place}
    <div class=" w-4/5 h-max flex flex-col mt-4">
      <img class=" w-full h-96" src={place.image} alt="" />
      <h3 class=" text-white text-xl font-semibold mx-auto mb-8 mt-2">
        {place.name}
      </h3>
      <p class=" text-white">{place.desc}</p>
    </div>
  {/each}
</div>
