<script>
    const {pokemon, onSelect} = $props();
</script>

<button class="card-button" onclick={onSelect}>
    <article>
        <img src={pokemon.sprites.other['official-artwork'].front_default
        || pokemon.sprites.front_default
        } alt = {pokemon.name}>
        <div class="info">
            <span class="pokemon-id">#{String(pokemon.id).padStart(3,'0')}</span>
            <h3 class="pokemon-name">{pokemon.name}</h3>
        </div>
    </article>
</button>

<style>
.card-button {
        background: none;
        border: none;
        padding: 0;
        cursor: pointer;
        text-align: left;
        transition: transform 0.2s ease-in-out, box-shadow 0.2s ease-in-out;
    }
    .card-button:hover, .card-button:focus {
        transform: scale(1.05);
        box-shadow: 0 4px 12px rgba(0,0,0,0.15);
        border-radius: 16px; 
        z-index: 0;
    }
    
    article{
        width: 180px;
        height: 240px;
        border: 2px solid grey;
        border-radius: 16px;
        padding: 16px;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
    }

    .info{
        width: 100%;
        display: flex;
        flex-direction: column;
        gap: 8px;
    }

    h3{
        margin: 0;
        text-transform: capitalize;
    }

    img{
        max-height: 150px;
        object-fit: contain;
    }
</style>