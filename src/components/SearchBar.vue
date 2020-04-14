<template>
    <div class="row">
        <input class="col-md-8" @input="onInput"/>
        <input type="submit" class="col-md-4 btn btn-primary" @click="onSubmit"/>
    </div>
</template>>

<script>
export default {
    name: "SearchBar",
    data () {
        return {
            inputText: "",
        };
    },
    methods: {
        onInput(event) {
            this.inputText = event.target.value;
        },
        onSubmit() {
            this.$emit("valueSubmit", this.inputText);
        }
    },
}
</script>>

<style scoped>
    div{
        text-align: center;
        margin: 20px;
    }
</style>>