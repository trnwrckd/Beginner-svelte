<script>
    export let showModal = false;
    export let isPromo = false;
    const disableModal = ()=> {
            isPromo=!isPromo;
        };
</script>

{#if showModal}
<div class="backdrop" class:promo={isPromo} on:click|self>
    <div class="myModal" on:click={disableModal} >
        <slot></slot>
        
    </div>
</div>{/if}

<style>
    .backdrop{
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
    .promo .myModal{
        background-color: crimson;
        color:white;
    }
</style>