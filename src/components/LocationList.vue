<template>
  <div class="location-list">
    <location v-if="locations.length > 0" @addId="addId(location.id)" @deleteId="deleteId(location.id)" v-for="location in locations" 
      :location=location
      :key=location.id >
    </location>
  </div>
</template>

<script>
import Location from '@/components/Location'
export default {
  name: 'locationList',
  props: ['locations'],
  components: {
    Location
  },
  methods: {
    addId: function (id) {
      this.$emit('addId', id)
    },
    deleteId: function (id) {
      var vm = this
      for (var i = 0; i < vm.locations.length; i++) {
        if (vm.locations[i].id === String(id)) {
          vm.locations.splice(i, 1)
          break
        }
      }
    }
  }
}
</script>

<style>

</style>
