<script>
    export let showModal = false;

</script>

{#if showModal}
    <div class="backDrop" on:click|self>
        <div class="myModal">
            <slot></slot>
        </div>
    </div>
{/if}

<style>
    .backDrop{
        width: 100%;
        height: 100%;
        position: fixed;
        background: rgba(0,0,0,1);
    }
    .myModal{
        padding: 10px;
        border-radius: 10px;
        max-width: 400px;
        margin: 10% auto;
        background: white;
        text-align: center;
        color:black;
    }
    
</style>