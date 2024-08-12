<script lang="ts">
    import ComplicatedWires from "./ComplicatedWires.svelte";
    import Password from "./Password.svelte";

    let parallelPort = false;
    let twoOrMoreBatteries = false;
    let serialNumberIsEven = false;
</script>

<ComplicatedWires parallelPort={parallelPort} twoOrMoreBatteries={twoOrMoreBatteries}
                  serialNumberIsEven={serialNumberIsEven}/>

<Password/>