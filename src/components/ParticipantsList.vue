<template>
  <div>
        <h1>List</h1>
        <div v-if="participants.length > 0">
        <div v-for="participant in participants" :key="participant.id">
            {{ participant.name}} {{ participant.lastName}} 
            <button type="submit" class="btn btn-primary" v-on:click.prevent="deleteParticipant(participant)" >Delete</button>
        </div>
        </div>
        <div v-else class="alert alert-dark" role="alert">
        	No participants yet!
        </div>
</div>

</template>

<script>
export default {
    props: ['participants'],
    data: function (){
        return {}
    }, 
    methods: {
        deleteParticipant: function(participant){
            this.$emit('deleteParticipant', participant);
        }
    }
}

</script>

</style>
