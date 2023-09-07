<template>
    <input :value="modelValue" @input="updateValue" class="input" type="text">
</template>

<script>

export default {
    name: "MyInput",
    props: {
        modelValue: String,
    },
    methods: {
        updateValue(event){
            this.$emit('update:modelValue', event.target.value);
        }
    }
}
</script>

<style scoped>
    .input {
        width: 100%;
        border: 3px solid purple;
        padding: 10px 15px;
        margin-top: 15px;
        border-radius: 12px;
    }
</style>