<script lang="ts">
	import { listen } from "svelte/internal";
    import { setContext } from 'svelte'
    let vals = ''

    //for context
    let myName = 'kjm'
    setContext("myKey", myName)
let value = ''
//typescript
interface data  {number: Number, operation: String}
const list: data =  {number: 1, operation: '+'}


function numVal(num:Number) {
     value += num
}
function opeVal(ope:String) {
    value += ope
}
function equals() {
     value = eval(value)
     value = value
}


</script>

<p class="text-3xl font-bold underline">This is second comp</p>

<input bind:value readonly>
<button on:click={() => numVal(2)}>2</button>
<button on:click={() => numVal(3)}>3</button>
<button on:click={() => opeVal('-')}>-</button>
<button on:click={() => opeVal('+')}>+</button>
<button on:click={equals} style:color = "blue">=</button>
<button on:click={() => value = ''} style:color|important={value ? 'red' : 'lightgray'}>clear</button>

<!-- typescript -->
<h1>{list.operation} - </h1>


<input bind:value={vals}>
<button on:click={() => vals++}>incre</button>






