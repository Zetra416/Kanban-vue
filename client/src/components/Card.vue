<template>

<div :class="type.background" >
  <h3>{{type.name}}</h3>
  <div class="max-height">
    <draggable class="list-group kanban-column " :list="type.data" group="tasks">
    <div class="" v-for="(element, id) in type.data" :key="id" >
          <TaskCard @deletedTask='deletedTask' :type="element"/>
    </div>
  </draggable>
  </div>
</div>

</template>

<script>
import TaskCard from './TaskCard.vue';
import draggable from 'vuedraggable';

export default {
  name: 'Card',
  components: {
    TaskCard,
    draggable
  },
  data() {
    return{
    }
  },
  props: ['type'],
  methods: {
    deletedTask(id) {
      let type = this.type.name
      console.log("ini di card vue", type)
      this.$emit('deletedTask', {id, type} )
    }
  }
}

</script>
