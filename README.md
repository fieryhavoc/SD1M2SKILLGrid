# SD1M2SKILLGrid
STYLE.CSS Opdracht 1
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

/* body kan flexbox gebruiken */
body {
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    font-family: Arial, sans-serif;
    background-color: #000;
}

.header {
    background-color: #000;
    color: #fff;
    text-align: center;
    padding: 2rem;
}

.dashboard {
    display: grid;
    grid-template-columns: repeat(6, 1fr);
    grid-template-rows: repeat(3, 1fr);
    gap: 1.5rem;
    padding: 2rem;
    background-color: #000;
    flex: 1;
}

.block {
    background-color: #e6e6e6;
    padding: 1.5rem;
    border-radius: 0.5rem;
    font-weight: bold;
}

.fetch {
    background-color: #4b8b3b;
    grid-column: 1 / 4;
    grid-row: 1 / 2;
}

.stopwatch {
    background-color: #a8433a;
    grid-column: 2 / 4;
    grid-row: 2 / 3;
}

.formulier {
    background-color: #3a3fa8;
    grid-column: 4 / 7;
    grid-row: 1 / 4;
}

.footer {
    background-color: #000;
    color: #fff;
    text-align: center;
    padding: 1.5rem;
}

GRID.HTML Opdracht 1
<!DOCTYPE html>
<html lang="nl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Grid Dashboard</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>

<header class="header">
    <h1>GRID compositie</h1>
</header>

<main class="dashboard">

    <section class="block fetch">
        Fetch
    </section>

    <section class="block stopwatch">
        Stopwatch
    </section>

    <section class="block formulier">
        Formulier
    </section>

</main>

<footer class="footer">
    <p>&copy; 2026 Grid opdracht</p>

</footer>

</body>
</html>


FORMULIER.HTML - Opdracht Fetch formulier
<!DOCTYPE html>
<html lang="nl">
<head>
    <meta charset="UTF-8">
    <title>Pokémon Fetch</title>
</head>
<body>

    <h2>Zoek een Pokémon</h2>

    <input
        type="text"
        id="pokemonName"
        placeholder="Bijv. pikachu"
    >

    <button onclick="fetchData()">Zoek Pokémon</button>

    <br><br>

    <img
        id="pokemonSprite"
        alt="Pokemon sprite"
        style="display: none;"
    >

    <script src="poke.js"></script>
</body>
</html>

POKE.JS - Opdracht Fetch Formulier
async function fetchData() {
    try {
        const pokemonName = document
            .getElementById("pokemonName")
            .value
            .toLowerCase();

        const response = await fetch(
            `https://pokeapi.co/api/v2/pokemon/${pokemonName}`
        );

        if (!response.ok) {
            throw new Error("Could not fetch resource");
        }

        const data = await response.json();

        const pokemonSprite = data.sprites.front_default;
        const imgElement = document.getElementById("pokemonSprite");

        imgElement.src = pokemonSprite;
        imgElement.style.display = "block";

    } catch (error) {
        console.error(error);
        alert("Pokémon niet gevonden");
    }
}
