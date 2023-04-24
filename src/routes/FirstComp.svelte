<script>
import { scale, fade } from 'svelte/transition'

</script>

<div style="width: 50%; margin: 30% auto 0; display: flex; align-items: center;justify-content: center;flex-direction: column;border: 1px solid #000; padding: 20px;" out:scale={{duration: 700}}>
    <h1>Welcome to KJM's website</h1>
    <button on:click>Get Started</button>
</div>


