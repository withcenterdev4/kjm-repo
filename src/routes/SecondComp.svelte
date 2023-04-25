<script lang="ts">
	import { listen } from "svelte/internal";

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

<h1>This is second comp</h1>

<input bind:value readonly>
<button on:click={() => numVal(2)}>2</button>
<button on:click={() => numVal(3)}>3</button>
<button on:click={() => opeVal('-')}>-</button>
<button on:click={() => opeVal('+')}>+</button>
<button on:click={equals} style:color = "blue">=</button>
<button on:click={() => value = ''} style:color|important={value ? 'red' : 'lightgray'}>clear</button>

<!-- typescript -->
<h1>{list.operation} - </h1>






<!-- <script lang="ts">
    interface User {
        name: string;
        id: number;
    }
    
    class UserAccount {
        name: string;
        id: number;
    
        constructor(name: string, id: number) {
        this.name = name;
        this.id = id;
        }
    }
    
    const user: User = new UserAccount("Murphy", 1)
</script>
<h1>{user.name}</h1> -->

