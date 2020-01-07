
<template>
  <div class="container" >
    <h1 clas="ti">Lista de tareas</h1>
    <div class="container-list" @submit.prevent="createTask" id="scroll">
      <form class="container-form" action="index.html" method="post">
        <ul id="list-id" class="list">
          <li
            v-for="(task, index) in tasks"
            :key="task.id"
            :class="{completed: task.pending}"
            class="tasks-item"
          >
            <input v-model="task.pending" :id="index" class="glyphicon" type="checkbox" />
            <span class="label-task">{{ task.description }}</span>
            <a class="x" @click="deleteTask(index)">
              <ald-icon icon="trash" />
            </a>
          </li>
        </ul>
      </form>
    </div>

    <div id="modal-id" class="modal">
      <div class="label-input-container">
        <label class="label-input">Nueva tarea</label>
      </div>
      <div class="imput-task-container">
        <input v-model="newTask" type="text" class="imput-task" name="task" />
      </div>

      <button class="add-button" name="add-button" @click="createtask">Añadir</button>
      <p>
        <a @click="deleteCompleted">Eliminar tareas completadas</a>
      </p>
    </div>

    <!-- <div id="container-plus-id" class="container-plus">
      <div class="box-plus">
        <i class="fas fa-plus plus" />
      </div>
    </div> -->
  </div>
</template>
<script>
export default {
  name: "Listado",
  status: "wip",
  release: "1.0.0",
  data() {
    return {
      newTask: "",
      tasks: [
        {
          description: "Dar de comer al gato",
          pending: false
        },
        {
          description: "Comprar leche",
          pending: false
        },
        {
          description: "Escribir a 911",
          pending: false
        }
      ]
    };
  },
  methods: {
    createtask() {
      this.tasks.push({
        description: this.newTask,
        pending: false
      });
      this.newTask = "";
    },
    deleteTask(index) {
      this.tasks.splice(index, 1);
    },
    deleteCompleted() {
      this.tasks = this.tasks.filter(task => !task.pending);
    }
  }
};
</script>
<style lang = "css" >

.container {
  background-color: #ffffff;
  font-size: 15px;
  border: 1px solid lightgray;
  border-radius: 10px;
  width: 350px;
  height: 80vh;
  margin-top: 40px;
  font-size: 18px;
  font-family: arial;
}
#scroll{
  height:270px;
  width:344px;
  overflow-y:scroll;
  overflow-x:hidden;
}
.listado-component {
  background-color: #61d0cc;
  display: flex;
  justify-content: center;
}

h1 {
  text-align: center;
  color: #0cacc8;
}

.container-list {
  height: 350px;
  position: relative;
}

.list {
  display: flex;
  flex-direction: column;
}

.tasks-item {
  text-decoration: none;
  list-style: none;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding-right: 50px;
}

.icon-task {
  padding-left: 77px;
}

.container-plus {
  border-top: 1px solid #61d0cc;
  height: 70px;
  width: 350px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.modal {
  width: 300px;
  height: 250px;
  background: #0cacc8;
  position: absolute;
  bottom: 100px;
  display: flex;
  flex-direction: column;
  color: #ffffff;
  align-items: center;
  margin-left: 25px;
}

.label-input-container {
  text-align: left;
  padding-top: 35px;
}

.imput-task-container {
  padding-bottom: 35px;
}

.imput-task {
  width: 250px;
  height: 40px;
  border: 1px solid #ffffff;
  background: #0cacc8;
}

.add-button {
  width: 150px;
  height: 50px;
  border-radius: 50px;
  border: 4px solid #ffffff;
  display: flex;
  justify-content: center;
  cursor: pointer;
  background: #0cacc8;
  color: #ffffff;
  font-size: 20px;
}

.closed {
  display: none;
}

.completed {
  text-decoration: line-through;
  color: rgb(161, 161, 161);
}
</style>
