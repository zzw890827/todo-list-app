<template>
  <b-alert :variant="type==='done'?'success':'primary'"
           show
           :dismissible="type==='todo'"
           @dismissed="handleDismiss"
           :class="{done: type==='done'}"
           fade>{{item.content}}
  </b-alert>
</template>

<script>
  export default {
    name: "TodoItem",
    props: {
      item: {
        type: Object,
        default: () => {
        },
      },
      type: {
        type: String,
        default: 'todo'
      },
    },
    methods: {
      handleDismiss: function () {
        this.$emit('dismiss', this.item);
      }
    }
  }
</script>

<style scoped>
  .done {
    text-decoration: line-through;
  }
</style>
