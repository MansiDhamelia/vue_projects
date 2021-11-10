<template>
  <div class="header">
    <div class="sub_container">
      <div class="box">
        <input
          type="text"
          id="txtId"
          v-model="text"
          placeholder="Add text..."
        />

        <Button @click="onClick" text="Add item" color="grey" />
      </div>
      <div class="li_container">
        <Tasks @toggle="toggleTask" @delete-task="deleteTask" :tasks="tasks" />
      </div>
    </div>
  </div>
</template>


<script>
import Button from "./Button.vue";
import Tasks from "./Data.vue";

export default {
  name: "Additem",
  components: {
    Button,
    Tasks,
  },
  data() {
    return {
      text: "",
      reminder: false,
      tasks: [],
    };
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: "item1",
        reminder: true,
      },
      {
        id: 2,
        text: "item2",
        reminder: true,
      },
      {
        id: 3,
        text: "item3",
        reminder: false,
      },
    ];
  },

  methods: {
    deleteTask(id) {
      this.tasks = this.tasks.filter((task) => task.id !== id);
    },
    onClick() {
      if (!this.text) {
        alert("Please add a value");
        return;
      } else {
        // this.tasks.push(this.text);
        //  this.text='';

        const newItem = {
          id: Math.floor(Math.random() * 100),
          text: this.text,
        };

        this.tasks = [...this.tasks, newItem];
        this.$emit("add-task", newItem);
        this.id = "";
        this.text = "";
      }
    },
    toggleTask(id) {
      this.tasks = this.tasks.map((task) =>
        task.id === id ? { ...task, reminder: !task.reminder } : task
      );
    },
  },
};
</script>

<style scoped>
.header {
  min-height: 100vh;
  display: flex;
  margin-top: 30px;
  align-items: center;
  flex-direction: column;
}
.sub_container {
  width: 400px;
  height: 200px;
}

ul li:hover {
  background: darkgray;
}
ul li.checked {
  text-decoration: line-through;
}
.box {
  text-align: center;
  background-color: #202020;
  color: white;
  padding: 10px;
}
.box:after {
  content: "";
  clear: both;
  display: table;
}
#txtId {
  margin: 0px;
  padding: 8px;
  width: 75%;
  float: left;
  font-size: 15px;
  border: none;
}
.close {
  position: absolute;
  right: 0px;
  top: 0px;
  padding: 10px;
}
.close:hover {
  background-color: #202020;
  color: white;
}
</style>