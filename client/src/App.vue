<template>
  <div class="container mt-5">
    <div class ="row">
      <div class="col form-inline">
        <b-form-input v-model="task" placeholder="Enter Task" @keyup.enter="add"></b-form-input>
        <b-button class="ml-2" variant="primary" @click="add">Add</b-button>
      </div>
    </div>

    <div class="row mt-3 ">
    <div class=" col-md-3 mt-3 p-2" v-for="(element, id) in listType" :key="id">
      <Card @deletedTask='deletedTask' :type="element" />
      <!-- <div class="col-md-3 p-2 alert alert-secondary">
        <h3>Backlog</h3>
        <div class="max-height">
          <draggable class="list-group kanban-column" :list="arrBacklog" group="tasks">
            <div class="list-group-item" v-for="(element, idx) in arrBacklog" :key="element.name">
              <p>name: {{element.name}}</p>
              <p>date: {{element.date}}</p>
              <b-button class="ml-2" variant="danger" @click="remove(idx, 'backlog')">Delete</b-button>
            </div>
          </draggable>
        </div>
      </div>

      <div class="col-md-3">
        <div class="p-2 alert alert-primary">
          <h3>In Progress</h3>
          <draggable class="list-group kanban-column" :list="arrInProgress" group="tasks">
            <div class="list-group-item" v-for="(element, idx) in arrInProgress" :key="element.name">
              name: {{element.name}}
              date: {{element.date}}
              <b-button class="ml-2" variant="danger" @click="remove(idx, 'inProgress')">Delete</b-button>
            </div>
          </draggable>
        </div>
      </div>

      <div class="col-md-3">
        <div class="p-2 alert alert-warning">
          <h3>Tested</h3>
          <draggable class="list-group kanban-column" :list="arrTested" group="tasks">
            <div class="list-group-item" v-for="element in arrTested" :key="element.name">
              name: {{element.name}}
              date: {{element.date}}
            </div>
          </draggable>
        </div>
      </div>

      <div class="col-md-3">
        <div class="p-2 alert alert-success">
          <h3>Done</h3>
          <draggable class="list-group kanban-column" :list="arrDone" group="tasks">
            <div class="list-group-item" v-for="element in arrDone" :key="element.name">
              name: {{element.name}}
              date: {{element.date}}
            </div>
          </draggable>
        </div>
      </div>-->
    </div>
  </div>
  </div>
</template>

<script>
// import draggable from 'vuedraggable';
import Card from './components/Card.vue';

export default {
  name: 'App',
  components: {
    // draggable,
    Card
  },
  data() {
    return{
      listType: [
        {name: 'Backlog', background: 'alert p-3 alert-secondary', data:[
          {id: 1, name: 'Code SignUpPage', date: '26/10/2020'},
          {id: 2, name: 'Test Dashboard', date: '26/10/2020'},
          {id: 3, name: 'Style Registration', date: '26/10/2020'},
          {id: 4, name: 'Help with Designs', date: '26/10/2020'},
        ]},
        {name: 'InProgress', background: 'alert p-3 alert-primary', data: [
          {id: 5, name: 'Code SignUpPage', date: '26/10/2020'},
          {id: 6, name: 'Test Dashboard', date: '26/10/2020'},
        ]},
        {name: 'Tested', background: 'alert p-3 alert-warning', data: []},
        {name:'Done', background: 'alert p-3 alert-success', data: []}
      ],
      // arrBacklog: [
      //   {name: 'Code SignUpPage', date: '26/10/2020'},
      //   {name: 'Test Dashboard', date: '26/10/2020'},
      //   {name: 'Style Registration', date: '26/10/2020'},
      //   {name: 'Help with Designs', date: '26/10/2020'},
      // ],
      task: '',
      // arrInProgress: [],
      // arrTested: [],
      // arrDone: [],
    }
  },
  methods:{
    add() {
      let newId = 0
      if(this.listType[0].data.length > 0) newId = this.listType[0].data[this.listType[0].data.length - 1].id + 1
      if(this.task) {
        this.listType[0].data.push({id: newId, name: this.task, date: '27/10/2020'});
        this.task = '';
      }
    },
    deletedTask(data) {
      console.log('ini id dan type di app vue', data)
      // this.listType[0].data.forEach((list) => {
      //   console.log(list.id)
      // });
      let list;
      switch (data.type) {
        case 'Backlog':
         list = this.listType[0].data
         this.listType[0].data  = list.filter((list) => list.id !== data.id )
         console.log("ini data baru", this.listType[0].data)
         break;
        case 'InProgress':
         list = this.listType[1].data
         this.listType[1].data  = list.filter((list) => list.id !== data.id )
         console.log("ini data baru", this.listType[0].data)
         break;
        case 'Tested':
         list = this.listType[2].data
         this.listType[2].data  = list.filter((list) => list.id !== data.id )
         console.log("ini data baru", this.listType[0].data)
         break;
        case 'Done':
         list = this.listType[3].data
         this.listType[3].data  = list.filter((list) => list.id !== data.id )
         console.log("ini data baru", this.listType[0].data)
         break;
      }

      // console.log(tempList);

      // console.log(list.data, "ini type list app vue")
    }
  }
}
</script>

<style>
.kanban-column {
  min-height: 300px;
}

.max-height {
  max-height: 500px;
  overflow-y: scroll;
}

.container {
  max-width: 80% !important;
}

</style>
