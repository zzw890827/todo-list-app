<template>
  <div id="app">
    <b-navbar type="light" variant="light" class="nav justify-content-center">
      <b-nav-form class="flex-nowrap">
        <b-form-input class="mr-sm-2" :placeholder="placeholder" v-model="inputItem"
                      style="width: 900px"></b-form-input>
        <b-button id="add_btn" variant="outline-primary" class="my-2 my-sm-0" @click="addTodoList">Add</b-button>
      </b-nav-form>
    </b-navbar>
    <div class="content">
      <item-display v-if="todoList.length!==0"
                    title="Todo"
                    subtitle="Todo items are showing below:"
                    :listArray=todoList
                    @done="addDoneList"
                    class="display">
      </item-display>
      <item-display v-if="doneList.length!==0"
                    title="Done"
                    subtitle="Done items are showing below:"
                    itemType="done"
                    :listArray=doneList>
      </item-display>
    </div>
    <b-tooltip v-if="inputItem===''" target="add_btn" placement="bottom">Input is <strong>empty!</strong></b-tooltip>
  </div>
</template>

<script>
  import ItemDisplay from "./components/ItemDisplay";

  class Item {
    constructor(id, content) {
      this.id = id;
      this.content = content;
    }
  }

  let todoCount = 1;

  export default {
    name: 'app',
    components: {
      ItemDisplay
    },
    data() {
      return {
        inputItem: '',
        todoList: [],
        doneList: [],
        placeholder: 'Todo...'
      }
    },
    methods: {
      addTodoList: function () {
        if (this.inputItem !== '') {
          this.todoList.push(new Item(todoCount++, this.inputItem));
          this.inputItem = '';
        }
      },
      addDoneList: function (doneItem) {
        this.doneList.push(doneItem);
      }
    }
  }
</script>

<style>
  .nav {
    margin-bottom: 20px;
  }

  .content {
    margin: 0 auto;
    max-width: 980px;
  }

  .display {
    margin-bottom: 20px;
  }

</style>

