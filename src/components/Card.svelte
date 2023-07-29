<script>
  export let item;
  export let content;
</script>

<div
  on:click={() => content(item)}
  style={`background-image:url(${item.touristplaces[0].image})`}
  class=" relative card w-4/5 h-52 my-2 hover:scale-105 transition duration-500 hover:cursor-pointer"
>
  <div class=" absolute bottom-0">
    <h2
      class="font-bold text-2xl text-green-200 border border-red-600 bg-slate-900 px-4"
    >
      {item.name}
    </h2>
  </div>
</div>

<style>
  .card {
    background-size: cover;
  }
</style>
