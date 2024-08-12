<script lang="ts">
    let firstColumnLetters = "";
    let thirdColumnLetters = "";
    let fifthColumnLetters = "";
    const words = [
        "about", "after", "again", "below", "could",
        "every", "first", "found", "great", "house",
        "large", "learn", "never", "other", "place",
        "plant", "point", "right", "small", "sound",
        "spell", "still", "study", "their", "there",
        "these", "thing", "think", "three", "water",
        "where", "which", "world", "would", "write"
    ];
    $: passwordOutput = "";

    function findPasswordPossibilities() {
        const firstLetters = firstColumnLetters.split("");
        const thirdLetters = thirdColumnLetters.split("");
        const fifthLetters = fifthColumnLetters.split("");
        const possibilities = words.filter(word => {
            return firstLetters.includes(word[0]) &&
                thirdLetters.includes(word[2]) &&
                fifthLetters.includes(word[4]);
        });
        passwordOutput = possibilities.join(", ");
    }
</script>

<section>
    <h2>Password</h2>
    <div>
        <label for="first-letters">First Letter Column</label>
        <input type="text" placeholder="First letters" id="first-letters" bind:value={firstColumnLetters}/>
    </div>
    <div>
        <label for="third-letters">Third Letter Column</label>
        <input type="text" placeholder="Third letters" id="third-letters" bind:value={thirdColumnLetters}/>
    </div>
    <div>
        <label for="fifth-letters">Fifth Letter Column</label>
        <input type="text" placeholder="Fifth letters" id="fifth-letters" bind:value={fifthColumnLetters}/>
    </div>
    <input type="button" value="Find Password Possibilities" on:click={findPasswordPossibilities} />
    <p id="password-output">{passwordOutput}</p>
</section>