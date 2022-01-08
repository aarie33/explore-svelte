<script>
    import { onMount, onDestroy, beforeUpdate, afterUpdate } from 'svelte';

    let description = '';
    $: characters = description.length;
    $: words = description ? description.split(' ').length : 0;

    $: if (characters > 10) {
        console.log(description);
    }

    function handleSubmit(event){
        // event.preventDefault();
        console.log('Form submitted');
        description = '';
    }

    // lifecycle
    onMount(function() {
        console.log('onMount');
    });
    
    onDestroy(function() {
        console.log('onDestroy');
    });
    
    beforeUpdate(function() {
        console.log('beforeUpdate');
    });

    afterUpdate(function() {
        console.log('afterUpdate');
    });
</script>

<div class="form-group">
    <p>{description}</p>
    <form on:submit|preventDefault="{handleSubmit}">
        <textarea bind:value={description} rows="7" />

        <button class="btn btn-primary" type="submite">Submit</button>
    </form>
    <p>Characters bound : {characters}</p>
    <p>Words bound : {words}</p>
</div>