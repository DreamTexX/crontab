<script lang="ts">
    import cronstrue from "cronstrue";
    
    let expression = "* * * * *";
    let description = cronstrue.toString(expression);

    $: {
        try {
            description = cronstrue.toString(expression);
        } catch (e) {
            description = "&nbsp;";
        }
    }
</script>

<main>
    <section>
        <form on:submit|preventDefault>
            <label>
                <input type="text" bind:value={expression} id="expression">
            </label>
            <div id="description">{@html description}</div>
        </form>
    </section>
</main>

<style>
    :global(:root) {
        --dark: #1a1a1a;
        --light: #f3f3f3;
    }

    :global(body) {
        margin: 0;
        padding: 0;
        font-family: sans-serif;
        background-color: var(--light);
    }

    :global(*) {
        box-sizing: border-box;
    }

    main {
        display: flex;
        justify-content: center;
        align-items: center;
        width: 100%;
        height: 100vh;
    }

    form {
        display: flex;
        flex-flow: column;
        justify-content: center;
        align-items: center;
        gap: 2rem;
        padding: 2rem;
    }

    input {
        color: var(--light);
        background-color: var(--dark);
        padding: 1rem 1.5rem;
        border-radius: 1rem;
        border: none;
        text-align: center;
        font-family: sans-serif;
        font-size: 2rem;
        outline: none;
        max-width: 300px;
        width: 100%;
    }

    #description {
        text-align: center;
        font-size: 1.5rem;
        color: var(--dark);
        max-width: 600px;
    }

    @media (prefers-color-scheme: dark) {
        :global(body) {
            background-color: var(--dark);
        }

        input {
            color: var(--dark);
            background-color: var(--light);
        }

        #description {
            color: var(--light);
        }
    }
</style>
