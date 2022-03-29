<template>
  <div class="showDiv">
        <ul>
          <li>Company: <span class="companystyle">{{experience.company}}</span>
          <span class="positionhead">Position: </span><span class="positionstyle">{{experience.position}}</span>
          <span class="positionhead">Rating: </span> <b-rate style="display: inline;" v-model="mutableprop"
            icon-pack="fas" disabled ></b-rate></li>
            <br>
          <li>Interview Difficulty: <span  v-for="(level,index) in experience.level" :key="index" style="background-color:#A72693;color: white; border-radius: 5px; padding: 5px;"> {{level}}</span>
          <span class="positionhead">Offer: </span><span style="background-color:#0A91AB;color: white; border-radius: 5px; padding: 5px;"> {{experience.offer}}</span></li>
          <br>
          <li>Interview Experience: <br><br>
            <span style="background-color:#346751;color: white; font-weight: normal; border-radius: 5px; padding: 5px;">{{experience.userexp}}</span></li>
          <br>
          <br>
          <li>Name: {{experience.name}}</li>
          <li>Email: {{experience.email}}</li>
          <li>Gender: {{experience.gender}}</li>
          <li>Interview Date: {{experience.date}}</li>

          <li>{{experience.upload}}</li>
        </ul>
      </div>
</template>

<script>
export default {
  name: 'ShowExperiences',
  props: ["experience"],
  data(){
   return{
     mutableprop: this.experience.rate
  }
   } 
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
