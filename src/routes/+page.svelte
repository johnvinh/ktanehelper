<script lang="ts">
    import ComplicatedWires from "./ComplicatedWires.svelte";

    let parallelPort = false;
    let twoOrMoreBatteries = false;
    let serialNumberIsEven = false;
</script>

<ComplicatedWires parallelPort={parallelPort} twoOrMoreBatteries={twoOrMoreBatteries}
                  serialNumberIsEven={serialNumberIsEven}/>