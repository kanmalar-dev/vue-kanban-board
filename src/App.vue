
<template>
<div class="body">
  <br>
  <div class="cen"> <h3> KANBAN BOARD </h3> </div>
  <br>
  <div class="container mt-5">
    <div class="row">
      <div class="col form-inline">
        <!-- Enter task list want to have -->
        <b-form-input
          id="input-2"
          v-model="newTask"
          required
          placeholder="Enter New Task"
          @keyup.enter="add">
        </b-form-input>
        <b-button @click="add" variant="primary" class="ml-2">Add</b-button>
      </div>
    </div>
     
     <br>
    <div class="row mt-5">
      <div class="col-3">
        <div class="p-2 alert alert-secondary">
          <h3>Draft</h3>
          <!-- Backlog draggable component. Pass arrBackLog to list prop -->
          <draggable
            class="list-group kanban-column"
            :list="arrBackLog"
            group="tasks"
          >
            <div
              class="list-group-item"
              v-for="element in arrBackLog"
              :key="element.name"
            >
              {{ element.name }}
            </div>
          </draggable>
        </div>
      </div>

      <div class="col-3">
        <div class="p-2 alert alert-primary">
          <h3>To do  </h3>
          <!-- In Progress draggable component. Pass arrInProgress to list prop -->
          <draggable
            class="list-group kanban-column"
            :list="arrInProgress"
            group="tasks"
          >
            <div
              class="list-group-item"
              v-for="element in arrInProgress"
              :key="element.name"
            >
              {{ element.name }}
            </div>
          </draggable>
        </div>
      </div>

      <div class="col-3">
        <div class="p-2 alert alert-warning">
          <h3>In Progress</h3>
          <!-- Testing draggable component. Pass arrTested to list prop -->
          <draggable
            class="list-group kanban-column"
            :list="arrTested"
            group="tasks"
          >
            <div
              class="list-group-item"
              v-for="element in arrTested"
              :key="element.name"
            >
              {{ element.name }}
            </div>
          </draggable>
        </div>
      </div>

      <div class="col-3">
        <div class="p-2 alert alert-success">
          <h3>Complete</h3>
          <!-- Done draggable component. Pass arrDone to list prop -->
          <draggable
            class="list-group kanban-column"
            :list="arrDone"
            group="tasks"
          >
            <div
              class="list-group-item"
              v-for="element in arrDone"
              :key="element.name"
            >
              {{ element.name }}
            </div>
          </draggable>
        </div>
      </div>
    </div>
  </div>
  <br>
  <br>
  <br>
  <br>
  <br>
  <br>
  <br>
  <br>
  <br>
</div>

</template>


<script>
//import draggable
import draggable from "vuedraggable";
export default {
  name: "kanban-board",
  components: {
    //import draggable as a component
    draggable
  },

  data() {
    return {
      // for new tasks
      newTask: "",
      // 4 arrays to keep track of our 4 statuses
      arrBackLog: [
        { name: "Code Sign In Page" },
        { name: "Test Dashboard" },
        { name: "User Interface Style " },
        { name: "Help with Designs" }
      ],
      arrInProgress: [],
      arrTested: [],
      arrDone: []
    };
  },
  methods: {
    //add new tasks method
    add: function() {
      if (this.newTask) {
        this.arrBackLog.push({ name: this.newTask });
        this.newTask = "";
      }
    }
  }
};
</script>

<style>
/* light stylings for the kanban columns */
.kanban-column {
  min-height: 300px;
}

.body {

  background-image:url('~@/assets/pic1.jpg');
  
}

.cen {
  text-align: center;
  color: cornsilk;
  font-family: Georgia, 'Times New Roman', Times, serif;
  font-size:xx-large;
}
</style>


