<script lang="ts">
    let goals: Array<String> = [
        "",
        "",
        "",
        "",
        "",
        "",
        "",
        "",
        "",
        "",
        "",
        "",
        "",
        "",
        "",
        "",
        "",
        "",
        "",
        "",
        "",
        "",
        "",
        "",
        "",
    ];

    let possibleGoals = [
        "5 Koroks",
        "5 hearts",
        "5 shrine",
        "Gerudo's main quest",
        "Zora's main quest",
        "Goron's main quest",
        "Rito's main quest",
        "An abyss",
        "A piece of Yiga armor",
        "Go to the Lost Woods",
        "Go to Kakariko village",
        "Go to Atheno village",
        "Go to a mine",
        "Champion's tunic",
        "5 towers",
        "Beat a flux construct",
        "Weapon with 20+ damage",
        "Kill a golem",
        "Kill an abyss' boss",
        "Kill an hynox",
        "Go to Tarrey Town",
        "Build a flying machine (controllable)",
        "Build a car",
        "Upgrade the battery",
        "Finish the tutorial",
        "Perfect pary an attack",
        "Do a flurry jump",
        "Get 5 Elusis cristals",
        "See Satori",
        "Unlock duplicata",
        "Get one duplicata plate",
        "Go the the Great Plateau",
    ];

    let i = 0;
    while (i < goals.length) {
        let index = Math.floor(Math.random() * possibleGoals.length);
        goals[i] = possibleGoals[index];
        possibleGoals.splice(index, 1);

        i++;
    }

    let buttonColor: Array<string> = [
        "",
        "",
        "",
        "",
        "",
        "",
        "",
        "",
        "",
        "",
        "",
        "",
        "",
        "",
        "",
        "",
        "",
        "",
        "",
        "",
        "",
        "",
        "",
        "",
        "",
    ]; // Initial button color

    let timer: any;

    function handleLongPress(buttonId: any) {
        timer = setTimeout(() => {
            buttonColor[buttonId] = "#ff8a8a";
        }, 500); // Adjust the duration of long-press as needed
    }

    function handlePressEnd() {
        clearTimeout(timer);
    }

    function handleClick(buttonId: any) {
        console.log("Button ID:", buttonId);
        buttonColor[buttonId] = "#8ab7ff";
    }
</script>

<body>
    <h3>TOTK Bingo</h3>
    <div id="grid">
        <div id="subgrid">
            {#each goals as goal, index}
                <button
                    on:mousedown|preventDefault={() => handleLongPress(index)}
                    on:mouseup|preventDefault={handlePressEnd}
                    on:mouseleave|preventDefault={handlePressEnd}
                    on:click|preventDefault={() => handleClick(index)}
                    style="background-color: {buttonColor[index]}"
                    id={`btn${index}`}
                >
                    {goal}
                </button>
            {/each}
        </div>
    </div>

    <footer>
        Hosted mercifully by the <a href="https://discord.gg/mRkShwjdA5">Bazar ambulant</a>, go check them out.
    </footer>
</body>

<style>
    h3 {
        display: flex;
        justify-content: center;
        font-size: 4rem;
        font-family: Arial, Helvetica, sans-serif;
        margin: .9rem;
    }
    button {
        display: subgrid;
        font-size: 2rem;
        background-color: lightgray;
        filter: drop-shadow(0 0 0.25rem black);
        border-radius: 0.3rem;
        border: 0;
        width: 10rem;
        height: 10rem;
        margin: 0;
        padding: 0;
    }

    #subgrid {
        display: grid;
        grid-template-columns: repeat(5, 1fr);
        gap: 10px;
    }

    footer {
        font-family: Arial, Helvetica, sans-serif;
        display: flex;
        justify-content: center;
        margin: 0.9rem;
        padding: 0;
    }
</style>
