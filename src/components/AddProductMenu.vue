<template>
    <form @submit.prevent>
        <h4>Add a product</h4>
        <CustomInput
        v-model = "product.name"
        placeholder="Name"
        />
        
        <CustomButton 
        class="btn" 
        style="align-self: flex-end; margin-top: 15px;" 
        @click="createProduct"
        >
            Add
        </CustomButton>
    </form>
</template>

<script>
import CustomButton from "@/UI/CustomButton.vue"
import CustomInput from "@/UI/CustomInput.vue";

export default {
    components: {CustomButton, CustomInput},

    data() {
        return {
            product: {
                name: "",
                id: 0,
                isDeleted: false,
            }
        }
    },
    methods: {
        createProduct() {
            this.product.id = Date.now();
            this.$emit('create', this.product);
            this.product = {
                name: "",
                id: 0,
                isDeleted: false,
            }
        }
    }
}
</script>

<style scoped>
    form {
        display: flex;
        flex-direction: column;
    }

</style>