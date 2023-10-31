<template>
  <q-page class="bg-grew-3 column">
    <div class="classrow q-pa-sa bg-primary">
      <q-input
      v-model="newTask"
      @keyuo.enter="addtask"
      class="col"
      square
      filled
      bg-color="white"
       placeholder="Add task"
       dense>
        <template v-slot:append>
          <q-btn
          @click="addTask"
          roubd
          dense
          flat
          icon="add" />
        </template>
      </q-input>
    </div>
    <q-list
    class="bg-white"
    separator
    bordered>
      <q-item
       v-for="(task) in tasks"
       :key="task.title"
       @click="task.done = !task.done"
       :class="{'done bg-blue-1' : task.done}"
       clickable
       v-ripple>
        <q-item-section avatar>
          <q-checkbox
          v-model="task.done"
          class="no-pointer-events"
          color="primary" />
        </q-item-section>
        <q-item-section>
          <q-item-label>{{ task.title }}</q-item-label>
        </q-item-section>
        <q-item-section
        v-if="task.done"
        side>
        <q-btn
        @click.stop="deleteTask"
        flat
        round
        dense
        color="primary"
        icon="delete" />
        </q-item-section>
      </q-item>
    </q-list>
    <div
     v-if="!tasks.length"
    class="no-tasks absolute-center">
        <q-icon
        name="check"
        size="100px"
        color="primary" />
      <div class="text-h5 text-primary text-center">
        Sem Conteudo
        </div>
     </div>
  </q-page>
</template>

<script>
export default {
  data() {
    return {
      newTask: '',
      tasks: [
        {
          title: 'Instalar',
          done: false
        },
        {
          title: 'BackUp',
          done: false
        },
        {
          title: 'Drivers',
          done: false
        },
      ]
    }
  },

  methods: {
      deleteTask()
  {


      this.task.splice()
      this.q.notify(apagado)

    }
  },
  addTask () {
    this.task.push({
      title: this.newTask,
      done: false
    })
    this.newTask = ''
  }
}
</script>

<style lang="scss">
.done {
  .q-item_label {
text-decoration: line-through;
color: #bbb
  }
}
.no-tasks {
  opacity: 0,5;
}
</style>
