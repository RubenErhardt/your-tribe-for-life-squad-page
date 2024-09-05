<script>
    /** @type {import('./$types').PageData} */
    export let data;

    console.log("Received data in +page.svelte:", data);
</script>


<h1>Jaar 2 FDND Studenten</h1>

<div class="kaartjes-container">
    {#if data.people}
        {#each data.people as person}
        <div class="kaartje-container">
            <div class="kaartje">
                <div class="kaartje-front">
                </div>
                <div class="kaartje-back">
                    <h1>{person.name}</h1>
                    <p>{person.bio}</p>
                    <img src="{person.avatar}" alt="Person Avatar" width="100" height="100">
                </div>
            </div>
        </div>
        {/each}
    {:else}
        <p>No data available</p>
    {/if}
</div>

<style>
    h1{
        font-size: 3em;
        text-align: center;
    }
    .kaartjes-container {
        display: flex;
        flex-wrap: wrap;
        gap: 40px;
        justify-content: center;
        padding: 20px;
    }

    .kaartje-container {
        perspective: 1000px;
        width: 250px;
        height: 300px;
        box-sizing: border-box;
    }

    .kaartje {
        width: 100%;
        height: 100%;
        position: relative;
        transform-style: preserve-3d;
        transition: transform 0.6s;
        cursor: pointer;
    }

    .kaartje:hover {
        transform: rotateY(180deg);
    }

    .kaartje-front,
    .kaartje-back {
        position: absolute;
        width: 100%;
        height: 100%;
        backface-visibility: hidden;
        border-radius: 8px;
    }

    .kaartje-front {
        background-image: url('/images/61vOBvbsYJL._AC_UF1000,1000_QL80_.jpg');
        background-size: cover;
        background-position: center;
    }

    .kaartje-back {
        background: white;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        color: black;
        transform: rotateY(180deg);
        padding: 20px;
        text-align: center;
    }

    .kaartje-back h1 {
        font-size: 1.2em;
        margin-bottom: 8px;
    }

    .kaartje-back p {
        font-size: 0.9em;
    }
</style>
