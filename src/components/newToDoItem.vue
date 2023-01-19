<template>
  <form @submit.prevent="onSubmit">
    <h2 class="label-wrapper">
      <label for="new-todo-item" class="label__lg">co mam udelat?</label>
    </h2>
    <input type="text" id="new-todo-item" name="new-todo" autocomplete="off" v-model.trim="label" class="input__lg"/>
    <input type="text" id="new-todo-item2" name="new-todo2" autocomplete="off" v-model.trim="label2" class="input__lg"/>
    <button type="submit" @click.right="onRightButton" class="btn btn__primary btn__lg">pridej</button>
  </form>
</template>
<script>
export default {
  methods: {
    onSubmit() {
      if (this.label === "") {
        return;
      }
      if (this.label2 === "") {
        return;
      }
      this.$emit("todo-added", this.label, this.label2);
      this.label = "";
      this.label2 = "";
    },
    onRightButton() {
      console.log('prave');
    }
  },
  data() {
    return {
      label: "",
      label2: "",
    }
  }
};
</script>

<style>

</style>