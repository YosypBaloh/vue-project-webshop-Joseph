<template>
    <h1 v-on:click="changeText()">{{ title.toLowerCase() }}!</h1>
    <p @mouseover="changeText('Some new')">{{ !isHasCar }}</p>
    <p v-bind:style="style">{{ info }}</p>
    <input @input="changeTextDynamic($event.target.value)" /> <br />
    <input @input="changeStyle($event.target.value)" />
    </template>

<script>
export default {
data() {
    return {
        title: "Hello World",
        isHasCar: true,
        userInput: "",
        style: "",
    };
    },
    methods: {
        changeText(word = "New") {
        this.title = word;
    },
    changeTextDynamic(value) {
        this.userInput = value;
    },
    changeStyle(value) {
        this.style = value;
    },
  },
  computed: {
    info() {
        if (this.userInput === "");
        else return "User text: " + this.userInput + "!";
    }
  }
};
</script>

<style scoped>
    
</style>