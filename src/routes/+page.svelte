<script>
import First from './FirstComp.svelte'
let active = true
let links = ['Home', 'Services', 'Account']
</script>
<h1>main page</h1>

<h2>first 3</h2>
<h2>I'm now on my main</h2>
<h1>This for my branch</h1>

<p>another one</p>
<First />

{#if active}
    <section>
        <h1>KJM</h1>
        <nav>
            <ul>
                {#each links as link}
                    <li>{link}</li>
                {/each}
            </ul>
        </nav>
    </section>
{/if}






