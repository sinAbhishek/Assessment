<script>
  export let addcard;
  export let close;
  let name = "";
  $: console.log(name);

  let image = "";
  let city = "";
  let desc = "";

  function details() {
    const x = {
      name: name,
      touristplaces: [
        {
          name: city,
          image: image,
          desc: desc,
        },
      ],
    };
    addcard(x);
  }
</script>

<div
  class="modal w-screen h-screen fixed flex justify-center items-center z-40"
>
  <div
    class=" flex flex-col justify-center items-center bg-white w-1/2 h-1/2 relative"
  >
    <button
      on:click={close}
      class=" absolute right-0 top-0 m-4 bg-slate-800 text-white px-4"
    >
      Close</button
    >
    <input
      class=" my-2 border bottom-4 border-black bg-black text-white px-4 py-2"
      type="text"
      bind:value={name}
      placeholder="Country"
    />
    <input
      class=" my-2 border bottom-4 border-black bg-black text-white px-4 py-2"
      type="text"
      bind:value={city}
      placeholder="City"
    />
    <input
      class=" my-2 border bottom-4 border-black bg-black text-white px-4 py-2"
      type="text"
      bind:value={image}
      placeholder="image url"
    />
    <textarea
      class=" my-2 border bottom-4 border-black w-1/2 h-14 bg-black text-white px-4 py-2"
      type="text"
      bind:value={desc}
      placeholder="Description"
    />
    <button class=" w-max bg-slate-950 text-white px-4" on:click={details}>
      Submit</button
    >
  </div>
</div>

<style>
  .modal {
    background-color: rgba(0, 0, 0, 0.652);
  }
</style>
