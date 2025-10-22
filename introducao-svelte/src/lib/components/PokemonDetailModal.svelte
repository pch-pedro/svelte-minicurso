<script>
 const {onClose, pokemon} = $props();

</script>

<div class="modal-backdrop">
    <article class="modal-content">
        <button class="close-button" onclick={onClose}>&times;</button>
        <img src={pokemon.sprites.other['official-artwork'].front_default
        || pokemon.sprites.front_default
        } alt = {pokemon.name}>
        <div class="info">
            <span class="pokemon-id">#{String(pokemon.id).padStart(3,'0')}</span>
            <h2 class="pokemon-name">{pokemon.name}</h2>

            <div class="types">
                {#each pokemon.types as typeInfo}
                    <span class="type {typeInfo.type.name}">{typeInfo.type.name}</span>
                {/each}
            </div>

            <div class="stats">
                <h3>
                    {#each pokemon.stats as stat}
                        <div class="stat-item">
                            <span class="stat-name">{stat.stat.name}</span>
                            <span class="stat-value">{stat.base_stat}</span>
                            <progress value={stat.base_stat} max="150"></progress>
                        </div>
                    {/each}
                </h3>
            </div>
        </div>
    </article>
</div>


<style>
.modal-backdrop {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background-color: rgba(0, 0, 0, 0.7);
        display: flex;
        justify-content: center;
        align-items: center;
        z-index: 1000;
    }

    .modal-content {
        position: relative;
        background: #242424;
        padding: 2rem;
        border-radius: 16px;
        width: 90%;
        max-width: 450px;
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 1rem;
        box-shadow: 0 5px 15px rgba(0,0,0,0.3);
    }

    .close-button {
        position: absolute;
        top: 10px;
        right: 15px;
        background: none;
        border: none;
        font-size: 2rem;
        cursor: pointer;
        color: #eee;
    }

    img {
        max-width: 200px;
        margin-top: -60px;
    }

    .info { text-align: center; width: 100%; }
    .pokemon-id { color: #888; }
    .pokemon-name { text-transform: capitalize; margin: 0.5rem 0; }
    
    .types {
        display: flex;
        gap: 0.5rem;
        justify-content: center;
        margin-bottom: 1rem;
    }
    .type {
        padding: 0.3rem 0.8rem;
        border-radius: 12px;
        color: white;
        font-weight: bold;
        text-transform: capitalize;
    }
    
    .fire { background-color: #F08030; }
    .water { background-color: #6890F0; }
    .grass { background-color: #78C850; }
    .electric { background-color: #F8D030; }
    .psychic { background-color: #F85888; }
    .ice { background-color: #98D8D8; }
    .dragon { background-color: #7038F8; }
    .dark { background-color: #705848; }
    .fairy { background-color: #EE99AC; }
    .normal { background-color: #A8A878; }
    .fighting { background-color: #C03028; }
    .flying { background-color: #A890F0; }
    .poison { background-color: #A040A0; }
    .ground { background-color: #E0C068; }
    .rock { background-color: #B8A038; }
    .bug { background-color: #A8B820; }
    .ghost { background-color: #705898; }
    .steel { background-color: #B8B8D0; }

    .stats { width: 100%; }
    .stat-item {
        display: grid;
        grid-template-columns: 120px 40px 1fr;
        align-items: center;
        gap: 0.5rem;
        margin-bottom: 0.5rem;
        text-align: left;
    }
    .stat-name { text-transform: capitalize; }
    .stat-value { font-weight: bold; }
    progress { width: 100%; }

    @media (prefers-color-scheme: light) {
        .modal-content {
            color: #213547;
            background: #ffffff;
        }
        .close-button {
            color: #242424;
        }
        button {
            background-color: #f9f9f9;
        }
    }
</style>