<script>
  import Card from "../components/Card.svelte";
  import data from "../data/data.js";
  import Modal from "../components/Modal.svelte";
  let updated = data;
  let name = "";
  let newdata = "";

  let open = true;
  let modalopen = false;

  function filterresults(name, updated) {
    if (name) {
      const result = updated.filter(
        (c) =>
          name.toLowerCase() ===
          c.name.slice(0, name.length).toLocaleLowerCase()
      );
      return result;
    } else if (updated) {
      return updated;
    } else {
      return updated;
    }
  }
  console.log(data);
  function content(axe) {
    newdata = axe;
  }
  function close() {
    modalopen = !modalopen;
  }
  function addcard(x) {
    updated = [...updated, x];
  }
</script>

{#if open}
  <div class=" fixed w-screen h-screen flex justify-center items-center">
    <button
      class=" w-max px-4 py-2 bg-red-500 rounded-md text-lg font-semibold hover:scale-105 transition duration-300"
      on:click={() => (open = !open)}
    >
      Open</button
    >
  </div>
{/if}

{#if modalopen}
  <Modal {addcard} {close} />
{/if}
{#if newdata}
  <div class="absolute left-0 w-1/2 h-screen flex flex-col items-center">
    <h2 class=" text-white md:text-3xl font-semibold mb-3 text-lg">
      Top Tourist places to visit in {newdata.name}
    </h2>

    {#each newdata.touristplaces as place}
      <div class=" w-full flex flex-col items-center my-4">
        <img class="image w-2/3 h-2/3" src={place.image} alt="" />
        <h1 class=" text-slate-50 font-bold text-xl">{place.name}</h1>
        <a
          class=" bg-red-300 w-max px-4 py-2 hover:scale-105 transition duration-300"
          href={`/place/${newdata.name}`}>See more</a
        >
      </div>
    {/each}
  </div>
{/if}
{#key updated}
  <div
    class={open
      ? "drawer bg-white w-1/2 absolute right-0 top-0 h-max flex justify-center flex-col items-center"
      : " def bg-gray-200  w-1/2 absolute right-0 top-0 h-max  transition duration-500 flex flex-col items-center"}
  >
    <button
      class=" absolute top-0 left-0 bg-red-700 text-xl rounded-md px-4 py-1 m-4"
      on:click={() => {
        open = !open;
        newdata = "";
      }}>X</button
    >
    <button
      class=" absolute top-0 right-0 bg-green-400 text-xl rounded-md px-4 py-1 m-4"
      on:click={() => {
        modalopen = !modalopen;
        newdata = "";
      }}>Add</button
    >
    <input
      class=" h-10 w-2/3 mt-4 bg-black text-white rounded-full px-4 mb-2"
      type="text"
      placeholder="Search country"
      bind:value={name}
    />
    {#each filterresults(name, updated) as item}
      <Card {item} {content} />
    {/each}
  </div>
{/key}

<style>
  .drawer {
    transform: translateX(100vw);
    transition: 1s ease-in-out;
  }
  .def {
    min-height: 100vh;
  }
  .image {
    min-width: 220px;
  }
</style>
