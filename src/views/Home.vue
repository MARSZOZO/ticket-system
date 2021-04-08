<template>
  <TicketList
    :data="newTicket" 
  />
  <CreateTicket 
    @createNewTicket="addTicket($event)"
  />
</template>

<script>
import TicketList from '@/components/TicketList.vue'
import CreateTicket from '@/components/CreateTicket.vue'

export default {
  components : {
    TicketList,
    CreateTicket
  },
  data() {
    return {
      newTicket: []
    }
  },
  methods: {
    addTicket(data){
      this.newTicket.push(data)
    }
  },
}
</script>

<style lang="scss" scoped>

</style>
