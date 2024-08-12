<script>
    import '../sakura-dark.css';
</script>

<div class="app">
    <main>
        <slot />
    </main>
</div>

<style>
    main {
        display: flex;
        flex-direction: row;
        gap: 2em;
    }
</style>
