<template>
<div id="container-fluid">
    <nav class="navbar navbar-light bg-light">
      <span class="navbar-text">
        Participants list
      </span>
    </nav>
    <participants-list v-bind:participants="participants" v-on:deleteParticipant='deleteParticipant($event)'></participants-list>
      <form v-on:submit.prevent="onSubmit()">
        <h1>Add participant</h1>
        <div class="form-group">
          <label for="participantName">Name</label>
          <input v-model="newParticipantName" type="text" class="form-control" id="participantName" placeholder="Fill name">
        </div>
        <div class="form-group">
          <label for="participantSurname">Surname</label>
          <input v-model="newParticipantSurname" type="text" class="form-control" id="participantSurname" placeholder="Fill surname">
        </div>
        <button class="btn btn-info" type="submit">Submit</button>
      </form>
    </div>
  </div>
 </div>
</template>

<script>
import ParticipantsList from './components/ParticipantsList.vue';

export default {
  components: {ParticipantsList},
  data: function (){
    return {
      participants: [],
      newParticipantName: null,
      newParticipantLastName: null,
    }
  }, 
  methods: {
    addParticipant: function(){
      var newParticipant = { id: Math.random()*1000, name: this.newParticipantName, lastName: this.newParticipantLastName };
      this.participants.push(newParticipant);
      this.newParticipantName = null;
      this.newParticipantLastName = null;
    },
    deleteParticipant: function(participant){
      this.participants = this.participants.filter((added) => added.id !== participant.id);
    }
  }
}

</script>

<style>
.container-fluid {
  margin: 0;
  padding: 0;
}

.app-content {
  margin: 30px;
}
</style>