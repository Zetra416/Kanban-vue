<template>
  <div class="list-group-item">
    <p>name: {{type.name}}</p>
    <p>date: {{type.date}}</p>
    <b-button class="ml-2" variant="danger" @click="remove(idx, 'backlog')">Delete</b-button>
  </div>
</template>


<script>


export default {
  name: 'TaskCard',
  components: {

  },
  props: ['type']
}
</script>


<style>

</style>
