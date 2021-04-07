<template>
  <TicketList 
    :data=""
  />
  <CreateTicket 
    @newTicket="createNewTicket($event)"
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
      key: value
    }
  },
  mounted () {
    ;
  },
  methods: {
    createNewTicket(ticket){
      console.log()
    }
  },
}
</script>

<style lang="scss" scoped>

</style>
