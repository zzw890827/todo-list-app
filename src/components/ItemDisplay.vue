<template>
  <b-card :title="title" :sub-title="subtitle" class="display">
    <b-card-body>
      <todo-item v-for="item in listArray"
                 :item="item"
                 :key="item.id"
                 :type="itemType"
                 @dismiss="handleDismiss">
      </todo-item>
    </b-card-body>
  </b-card>
</template>

<script>
  import TodoItem from "./TodoItem";

  export default {
    name: "ItemDisplay",
    components: {TodoItem},
    data() {
      return {}
    },
    props: {
      title: {
        type: String,
        default: '',
      },
      subtitle: {
        type: String,
        default: '',
      },
      listArray: {
        type: Array,
        default: () => [],
      },
      itemType: {
        type: String,
        default: 'todo'
      }
    },
    methods: {
      handleDismiss: function (item) {
        this.$emit('done', item);
      }
    }
  }
</script>

<style scoped>

</style>
