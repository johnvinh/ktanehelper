<script lang="ts">
    let parallelPort = false;
    let twoOrMoreBatteries = false;
    let serialNumberIsEven = false;
    let red = false;
    let blue = false;
    let light = false;
    let star = false;

    $: result = calculateResult(red, blue, {light, star, twoOrMoreBatteries, parallelPort, serialNumberIsEven});

    type WireCondition = {
        light: boolean;
        star: boolean;
        twoOrMoreBatteries?: boolean;
        parallelPort?: boolean;
        serialNumberIsEven?: boolean;
    };

    const wireLogic = {
        white: ({light, star, twoOrMoreBatteries}: WireCondition) => {
            if (star && light) return !!twoOrMoreBatteries;
            return !light;
        },

        red: ({light, star, twoOrMoreBatteries, serialNumberIsEven}: WireCondition) => {
            if (star && light) return !!twoOrMoreBatteries;
            if (light) return !!twoOrMoreBatteries;
            if (star) return true;
            return !!serialNumberIsEven;
        },

        blue: ({light, star, parallelPort, serialNumberIsEven}: WireCondition) => {
            if ((star && light) || light) return !!parallelPort;
            if (star) return false;
            return !!serialNumberIsEven;
        },

        redBlue: ({light, star, parallelPort, serialNumberIsEven}: WireCondition) => {
            if (star && light) return false;
            if (light) return !!serialNumberIsEven;
            if (star) return !!parallelPort;
            return !!serialNumberIsEven;
        }
    };

    function calculateResult(
        red: boolean,
        blue: boolean,
        condition: WireCondition
    ): boolean {
        if (red && blue) return wireLogic.redBlue(condition);
        if (!red && !blue) return wireLogic.white(condition);
        if (red) return wireLogic.red(condition);
        if (blue) return wireLogic.blue(condition);
        return false;
    }
</script>

<main>
    <h1>Complicated Wires</h1>
    <section>
        <form>
            <fieldset>
                <legend>Bomb Attributes</legend>
                <div>
                    <label for="parallelPort">Parallel Port</label>
                    <input type="checkbox" bind:checked={parallelPort} id="parallelPort">
                </div>
                <div>
                    <label for="twoOrMoreBatteries">Two or More Batteries</label>
                    <input type="checkbox" bind:checked={twoOrMoreBatteries} id="twoOrMoreBatteries">
                </div>
                <div>
                    <label for="serialNumberIsEven">Serial Number is Even</label>
                    <input type="checkbox" bind:checked={serialNumberIsEven} id="serialNumberIsEven">
                </div>
            </fieldset>
            <fieldset>
                <legend>Wire Colors</legend>
                <div>
                    <label for="red">Red</label>
                    <input type="checkbox" bind:checked={red} id="red">
                </div>
                <div>
                    <label for="blue">Blue</label>
                    <input type="checkbox" bind:checked={blue} id="blue">
                </div>
            </fieldset>
            <fieldset>
                <legend>Wire Attributes</legend>

                <div>
                    <label for="light">Light</label>
                    <input type="checkbox" bind:checked={light} id="light">
                </div>

                <div>
                    <label for="star">Star</label>
                    <input type="checkbox" bind:checked={star} id="star">
                </div>
            </fieldset>
            <strong id="result">
                {result ? 'Cut' : 'Do Not Cut'}
            </strong>
        </form>
    </section>
</main>