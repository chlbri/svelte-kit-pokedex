<script
  context="module"
  lang="ts">
  import { getPokemonById } from '../../pokestore';
  export async function load(ctx: {
    page: {
      params: {
        id: any;
      };
    };
  }) {
    let id =
      ctx.page
        .params
        .id;
    const pokeman = await getPokemonById(
      id
    );
    return {
      props: {
        pokeman
      }
    };
  }
</script>

<script lang="ts">
  export let pokeman: {
    types: {
      type: {
        name: any;
      };
    }[];
    name: string;
    height: any;
    weight: any;
    sprites: {
      [
        x: string
      ]: string;
    };
  };
  const type =
    pokeman
      .types[0]
      .type.name;
</script>

<svelte:head>
  <title
    >Pokedex - {pokeman.name}</title
  >
</svelte:head>

<div
  class="flex flex-col items-center"
>
  <h1
    class="text-4xl text-center my-8 uppercase"
  >
    {pokeman.name}
  </h1>
  <p>
    Type: <strong
      >{type}</strong
    >
    | Height:
    <strong
      >{pokeman.height}</strong
    >
    | Weight:
    <strong
      >{pokeman.weight}</strong
    >
  </p>
  <img
    class="card-image"
    src={pokeman
      .sprites[
      'front_default'
    ]}
    alt={pokeman.name}
  />
</div>
