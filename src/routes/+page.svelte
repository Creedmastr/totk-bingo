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
        ""
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
            buttonColor[buttonId] = "red";
        }, 500); // Adjust the duration of long-press as needed
    }

    function handlePressEnd() {
        clearTimeout(timer);
    }

    function handleClick(buttonId: any) {
        console.log("Button ID:", buttonId);
        buttonColor[buttonId] = "blue";
    }
</script>

<body>
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
</body>

<style>
    button {
        display: subgrid;
        font-size: 2rem;
        background-color: lightgray;
        filter: drop-shadow(0 0 0.15rem black);
        border-radius: .1rem;
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
</style>
