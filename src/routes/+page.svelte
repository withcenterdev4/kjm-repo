<script>
import First from './FirstComp.svelte'
import Second from './SecondComp.svelte'
import { scale, fade, fly } from 'svelte/transition'
let active = false
let act = true
let pop = false
let links = ['Home', 'Services', 'Account']
let accounts = []


function forLinks(i) {
    if(i === 2) {
        act = false
    }
}
function forQual() {
    const warning = confirm("Want to make quotes!")
    if(warning === true) {
        pop = false
    }else {
        pop = true
    }
}
</script>

{#if active}
    <First on:click={() => active = false}/>
{:else}
    <header style="display: flex; border-bottom: 1px solid #0004; justify-content: space-around;" in:fade={{duration: 2000}}>
        <h2>KJM</h2>
        <nav>
            <ul style="display: flex; justify-content: space-around; list-style: none;gap: 30px;">
                {#each links as link, i}
                    <li on:click={() => forLinks(i)} on:keydown>{link}</li>
                {/each}
            </ul>
        </nav>
    </header>
    {#if act}
        <section>
            <h1>Quotes</h1>
            <div>
                <textarea />
                <button on:click={forQual}><a href={pop ? '#' : 'Popup'}>Add quotes</a></button>
            </div>
        </section>
    {:else}
        <Second />
    {/if}

{/if}






