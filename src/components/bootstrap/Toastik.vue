<template>
  <div>
    <b-button @click="makeToast()">Show Toast</b-button>
    <b-button @click="makeToast(true)">Show Toast (appended)</b-button>
    <div class="p-3 bg-secondary progress-bar-striped" style="min-height: 170px;">
    <div class="box">
      <b-button class="mb-2" variant="primary" @click="$bvToast.show('example-toast')">
        Show toast
      </b-button>
      <b-button class="mb-2" variant="primary" @click="$bvToast.hide('example-toast')">
        Hide toast
      </b-button>
      <b-toast id="example-toast" title="BootstrapVue" static no-auto-hide>
        Hello, world! This is a toast message.
      </b-toast>
    </div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'ToastComponent',
  data() {
    return {
      toastCount: 0
    }
  },
  methods: {
    makeToast(append = false) {
      this.toastCount++
      this.$bvToast.toast(`This is toast number ${this.toastCount}`, {
        title: 'BootstrapVue Toast',
        autoHideDelay: 5000,
        appendToast: append
      })
    }
  }
}
</script>