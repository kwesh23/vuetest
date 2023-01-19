<template>
  <form class="stack-small" @submit.prevent="onSubmit">
    <div>
      <label class="edit-label">Edit Name for &quot;{{label}}&quot;</label>
      <input
          :id="id"
          type="text"
          autocomplete="off"
          v-model.lazy.trim="newLabel" />
      <input
          :id="id2"
          type="text"
          autocomplete="off"
          v-model.lazy.trim="newLabel2" />
    </div>
    <div class="btn-group">
      <button type="button" class="btn" @click="onCancel">
        Cancel
        <span class="visually-hidden">editing {{label}} a {{label2}}</span>
      </button>
      <button type="submit" class="btn btn__primary btn__lg">
        Save
        <span class="visually-hidden">edit for {{label}} a {{label2}}</span>
      </button>
    </div>
  </form>
</template>
<script>
export default {
  props: {
    label: {
      type: String,
      required: true,
    },
    label2: {
      type: String,
      required: true,
    },
    id: {
      type: String,
      required: true,
    },
    id2: {
      type: String,
      required: true,
    },
  },
  data() {
    return {
      newLabel: this.label,
      newLabel2: this.label2,
    };
  },
  methods: {
    onSubmit() {
      if (this.newLabel && this.newLabel !== this.label && this.newLabel2 && this.newLabel2 !== this.label2) {
        this.$emit("item-edited", this.newLabel, this.newLabel2);
      }
    },
    onCancel() {
      this.$emit("edit-cancelled");
    },
  },
};
</script>
<style scoped>
.edit-label {
  font-family: Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #0b0c0c;
  display: block;
  margin-bottom: 5px;
}
input {
  display: inline-block;
  margin-top: 0.4rem;
  width: 100%;
  min-height: 4.4rem;
  padding: 0.4rem 0.8rem;
  border: 2px solid #565656;
}
form {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
}
form > * {
  flex: 0 0 100%;
}
</style>