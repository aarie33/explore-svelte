<script>
    export let currentEmoji;
    let current = 'button1'
</script>

<style>
    div{
        font-size: 5rem;
    }
</style>

<div>{currentEmoji}</div>

<button 
    class="btn"
    class:btn-primary="{current == 'button1'}" 
    on:click="{() => current = 'button1'}">
    Click me
</button>
<button 
    class="btn"
    class:btn-primary="{current == 'button2'}" 
    on:click="{() => current = 'button2'}">
    Click me again
</button>
<button 
    class="btn"
    class:btn-primary="{current == 'button3'}" 
    on:click="{() => current = 'button3'}">
    Click me 1 more time
</button>