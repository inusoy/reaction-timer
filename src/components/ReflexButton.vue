<template>
    <div class="button" v-if="isButtonVisible" @click="buttonPressed">
        <span>PRESS THE REFLEX BUTTON</span>
    </div>
</template>

<script>
export default {
    props: {
        isButtonVisible: {
            type: Boolean,
        }
    }
    ,
    methods: {
        buttonPressed() {
            this.$emit('reflexButtonClicked')
        }
    }
}
</script>

<style>
.button {
    display: inline-flex;
    width: 100px;
    background-color: #41b883;
    justify-content: center;
    align-items: center;
    padding: 1%;
    border-radius: 10px;
}
</style>