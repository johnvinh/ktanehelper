<script lang="ts">
    let parallelPort = false;
    let twoOrMoreBatteries = false;
    let serialNumberIsEven = false;
    let red = false;
    let blue = false;
    let light = false;
    let star = false;

    $: result = calculateResult(parallelPort, twoOrMoreBatteries, serialNumberIsEven, red, blue, light, star);

    function calculateResult(parallelPort: boolean, twoOrMoreBatteries: boolean, serialNumberIsEven: boolean, red: boolean, blue: boolean, light: boolean, star: boolean) {
        if (red && blue && star && light) {
            return "DO NOT CUT";
        } else if (red && blue && star && !light && parallelPort) {
            return "CUT";
        } else if (red && blue && !star && light && serialNumberIsEven) {
            return "CUT";
        } else if (red && blue && !star && !light && serialNumberIsEven) {
            return "CUT";
        } else if (red && !blue && star && light && twoOrMoreBatteries) {
            return "CUT";
        } else if (red && !blue && star && !light) {
            return "CUT";
        } else if (red && !blue && !star && light && twoOrMoreBatteries) {
            return "CUT";
        } else if (red && !blue && !star && !light && serialNumberIsEven) {
            return "CUT";
        } else if (!red && blue && star && light && parallelPort) {
            return "CUT";
        } else if (!red && blue && star && !light) {
            return "DO NOT CUT";
        } else if (!red && blue && !star && light && parallelPort) {
            return "CUT";
        } else if (!red && blue && !star && !light && serialNumberIsEven) {
            return "CUT";
        } else if (!red && !blue && star && light && twoOrMoreBatteries) {
            return "CUT";
        } else if (!red && !blue && star && !light) {
            return "CUT";
        } else if (!red && !blue && !star && light) {
            return "DO NOT CUT";
        } else if (!red && !blue && !star && !light) {
            return "CUT";
        }
    }
</script>

<main>
    <h1>Complicated Wires</h1>
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
    <div>
        <label for="red">Red</label>
        <input type="checkbox" bind:checked={red} id="red">
    </div>
    <div>
        <label for="blue">Blue</label>
        <input type="checkbox" bind:checked={blue} id="blue">
    </div>
    <div>
        <label for="light">Light</label>
        <input type="checkbox" bind:checked={light} id="light">
    </div>
    <div>
        <label for="star">Star</label>
        <input type="checkbox" bind:checked={star} id="star">
    </div>
    <strong id="result">
        {result}
    </strong>
</main>