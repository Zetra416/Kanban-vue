<template>
  <div class="list-group-item">
    <p>name: {{type.name}}</p>
    <p>date: {{type.date}}</p>
    <b-button class="ml-2" variant="danger" @click="remove(type.id)">Delete</b-button>
  </div>
</template>


<script>


export default {
  name: 'TaskCard',
  components: {

  },
  props: ['type'],
  methods: {
    remove(id) {
      console.log("masuk nih", id)
      this.$emit('deletedTask', id)
    }
  }
}
</script>


<style>

</style>
