<template>
    <div class="item">
        <div v-if="!product.isDeleted">
            <div>Product: {{ product.name }}</div>
        </div>
        <div v-else>
            <div><strike>Product: {{ product.name }}</strike></div>
        </div>
        <CustomButton class="item__btn" @click="deleteItem">
            {{ product.isDeleted ? 'Bring back' : 'Delete' }}
        </CustomButton>
    </div>
</template>

<script>
import CustomButton from "@/UI/CustomButton.vue"
export default {
    components: {CustomButton},
    props: {
        product: {
            type: Object,
            required: true
        }
    },
    data() {
        return {
            
        }
    },
    methods: {
        deleteItem(){
            this.$emit("remove", this.product);
        },
    },
}
</script>

<style scoped>
    .item {
        padding: 15px;
        border: 3px solid purple;
        margin: 15px;
        display: flex;
        align-items: center;
        justify-content: space-between;
        border-radius: 12px;
    }

    .item__btn {
        margin-left: 5px;
        display: flex;
    }
</style>