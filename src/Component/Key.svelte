<script>
    import {createEventDispatcher} from 'svelte';

    export let w = "57px";
    export let h = "57px";

    export let key_value
    let dispatch = createEventDispatcher()


</script>
<div>
    <button class="btn btn-custom m-2" on:click={() => dispatch('cal_value', key_value)}
            style=" width:{w}; height:{h}">{key_value}</button>
</div>
<style>
    .btn-custom {
        background: rgb(0, 0, 0, 0.4);
        font-weight: bold;
        font-size: 30px;
        padding: 5px 10px;


    }
</style>