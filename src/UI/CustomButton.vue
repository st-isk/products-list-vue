<template>
    <button class="btn">
        <slot></slot>
    </button>
</template>

<script>
    export default{
        
    }
</script>

<style scoped>
    .btn {
        padding: 10px 15px;
        background-color: white;
        color: purple;
        border: 1px solid purple;
        border-radius: 12px;
    }

    .btn:hover {
	    box-shadow: inset 0 0 0 3px purple;
    }
</style>