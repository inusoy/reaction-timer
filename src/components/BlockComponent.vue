<template>
    <div class="button" v-if="isVisible" @click="toggleVisibility">
        <span>PRESS THE BUTTON</span>
    </div>
    <h2 v-if="result !== 0">Your result is: {{ result }}ms</h2>
    <div class="button" v-if="result !== 0" @click="reset">
        <span>Try again?</span>
    </div>
</template>

<script>
export default {
    data() {
        return {
            isVisible: true,
            timer: 0,
            result: 0,
        }
    },
    methods: {
        toggleVisibility() {
            if (this.timer) {
                this.timer = performance.now() - this.timer
                this.result = this.timer
                this.isVisible = !this.isVisible
            } else {
                this.isVisible = !this.isVisible
                const timeout = this.getRandomArbitrary(2000, 5000)
                console.log(timeout)
                setTimeout(() => {
                    this.isVisible = true;
                    this.timer = performance.now()
                }, timeout);
            }
        },
        getRandomArbitrary(min, max) {
            return Math.random() * (max - min) + min;
        },
        reset() {
            this.isVisible = true
            this.timer = 0
            this.result = 0
        },
    }
}
</script>


<style>
.button {
    display: inline-flex;
    width: 100px;
    /* height: 100px; */
    background-color: #41b883;
    justify-content: center;
    align-items: center;
    padding: 1%;
    border-radius: 10px;
}
</style>