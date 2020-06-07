<template>
    <div class="component">
        <h3>You may view the User Details here</h3>
        <p>Many Details</p>
        <p>User Name: {{ name }}</p>
        <p>User age: {{ userAge }}</p>
        <button @click="resetFn()"> Reset Name </button>
        <button @click="resetName"> Reset Name </button>
    </div>
</template>

<script>
    import { eventBus } from "../main.js"

    export default {
        //prop validation
        props: {
            name: {
                type: String
            },
            resetFn: Function,
            userAge: Number
        },
        methods: {
            resetName(){
                this.name = "Miguel"
                this.$emit('nameWasReset', this.name)
            }
        },
        created(){
            eventBus.$on("ageWasEdited", (age) => {
                this.userAge = age
            })
        }
    }
</script>

<style scoped>
    div {
        background-color: lightcoral;
    }
</style>
