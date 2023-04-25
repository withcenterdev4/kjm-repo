<script>
import First from './FirstComp.svelte'
import Second from './SecondComp.svelte'
import Third from './ThirdComp.svelte'
import { scale, fade, fly } from 'svelte/transition'
import { getContext } from 'svelte'
import { get } from 'svelte/store'
import { createEventDispatcher } from 'svelte'
const dispatch = createEventDispatcher()

let active = true
let act = true
let pop = false
let textar = false
let test = false
let links = ['Home', 'Services', 'Account']
let myQoutes = []
let newQoutes = ''
let textarea = ''
let forttl = ''
//for login and signup
let bol = true
let act1 = false
let vals = ''
let popMess = false


let firstVal = [
    {username: 'keannu', password: '123pass'}
]


//for login and signup
function logFuncs() { 
    if(vals === '123pass') {
        alert('Succesfully login')
        active = false
    }else {
        alert('Invalid code')
    }
}
function forFirstComp() {
    bol = false
}


function forLinks(i) {
    if(i === 2) {
        act = false
    }else if(i === 0) {
        act = true
    }
}
function forQual() {
    const warning = confirm("Want to make quotes!")
    if(warning === true) {
        textar = true
    }else {
        pop = true
    }
}
function forCancel() {
    textar = false
    textarea = ''
}
function forAdd() {
    myQoutes = [...myQoutes, {title: forttl, text: textarea}]
    forttl = ''
    textarea = ''
    textar = false
}
function forCopy(i) {
    console.log(i)
    popMess = true
}
</script>

{#if active}
    {#if bol}
        <First on:click={forFirstComp}/>
    {:else}
        <!-- <Third on:forkey={forThirdComp}/> -->
        <form on:submit|preventDefault={logFuncs} in:fly={{ y:500, duration:800}} out:fade={{duration:300}}>
            <input bind:value={vals} placeholder="Enter Code" type=password>
            <button type=submit disabled={vals ? false : true}>login</button>
        </form>
    {/if}
{:else}
    <header style="display: flex; border-bottom: 1px solid #0004; justify-content: space-around;" in:scale={{duration: 1000}}>
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
                {#if textar}
                    <div style="margin-bottom: 30%;">
                        <input placeholder=title bind:value={forttl}>
                        <textarea bind:value={textarea}/>
                        <button disabled={textarea ? false : true} on:click={forAdd}>add</button>
                        <button on:click={forCancel}>cancel</button>
                    </div>
                {:else}
                <button on:click={forQual}  style="margin-bottom: 30%;">Make quotes</button>
                {/if}
                <div style="display:grid; grid-template-columns:repeat(2, 1fr); width: 900px;">
                    {#each myQoutes as qoute, i}
                        <div style="border: 1px solid #000; width: 450px; margin: 10px;padding: 20px;" in:scale={{duration:600}}>
                            <h2>{qoute.title}</h2>
                            <p>{qoute.text}</p>
                            <button on:click={() => forCopy(i)}>copy</button>
                        </div>
                        {#if popMess}
                            <div class="popupmess" class:pops={popMess}>
                                <h2><i>Qoutes copied!</i></h2>
                                <p>{qoute.forttl}</p>
                                <p><i>{qoute.textarea}</i></p>
                            </div>
                        {/if}
                    {/each}
                </div>
            </div>
        </section>
    {:else}
        <Second />
    {/if}

{/if}

<style>
    .popupmess {
        right: -1000px;
        position: absolute;
        bottom: 5%;
        background:aliceblue;
        padding: 10px;
        width: 200px;
    }
    .pops {
        position: absolute;
        bottom: 5%;
        right: 5%;
        background:aliceblue;
        padding: 10px;
        width: 200px;
    }
</style>


