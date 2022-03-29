<template>
  <div id="app">
      <h1 id="headingTop">Interview Experiences</h1>
      <ShowExperiences v-for="experience in experiences.slice().reverse()" :experience="experience" :mutableprop="experience.rate" v-bind:key="experience.id"/>    


<!-- Form to share experience-->


    <section class="enterDiv">
      <h1 id="heading">Share your Experience</h1>

      <b-field label="Name">
            <b-input v-model="name"></b-input>
        </b-field>

        <b-field label="Email">
            <b-input v-model="email" type="email" maxlength="30">
            </b-input>
        </b-field>
        
        <b-field label="Gender">
              <b-radio v-model="gender"
                name="name"
                native-value="Male">
                Male
              </b-radio>
              <b-radio v-model="gender"
                name="name"
                native-value="Female">
                Female
              </b-radio>
        </b-field>

        <b-field label="Company Name">
            <b-input v-model="company"></b-input>
        </b-field>
        <b-field label="Position Applied">
            <b-input v-model="position"></b-input>
        </b-field>
        <b-field label="Interview Date">
            <b-datepicker
                v-model="selected"
                :show-week-number="showWeekNumber"
                :locale="locale"
                placeholder="Click to select..."
                icon="calendar-today"
                :icon-right="selected ? 'close-circle' : ''"
                icon-right-clickable
                @icon-right-click="clearDate"
                trap-focus>
            </b-datepicker>
        </b-field>

        <b-field label="Interview Questions Level">
          <b-checkbox v-model="level"
                native-value="Beginner">
                Beginner
            </b-checkbox>
            <b-checkbox v-model="level"
                native-value="Intermediate">
                Intermediate
            </b-checkbox>
            <b-checkbox v-model="level"
                native-value="Hard">
                Hard
            </b-checkbox>
        </b-field>

        <br>

        <b-field label="Offer">
            <b-select v-model="offer" placeholder="Offer Status">
                <option>Accepted</option>
                <option>Rejected</option>
                <option>Decline</option>
            </b-select>
        </b-field>
        <br>
        <b-field label="Rate your Interview Experience">
        <b-rate v-model="rate"
            icon-pack="fas"  ></b-rate>
        </b-field>
        <br>

        <b-field label="Share your Interview Experience">
            <b-input v-model="userexp" maxlength="200" type="textarea"></b-input>
        </b-field>

        <b-button type="is-primary" @click="submit">Submit</b-button>
    </section>
  </div>
</template>

<script>

import ShowExperiences from "./components/Show.vue";
export default {
  name: 'App',
  components:{ShowExperiences},
  data(){
    return {
          selected: new Date(),
          showWeekNumber: false,
          locale: undefined,

          id:3,
          name: "",
          email: "",
          gender: null,
          company: "",
          position: "",
          level: [],
          offer: null,
          rate: 0,
          userexp:"",
      experiences: [
        {
          id:1,
          name: "Guneet Kaur",
          email: "guneet@gmail.com",
          gender: "Female",
          company: "Recruit CRM",
          position: "Associate Software Engineer",
          date: "2022-02-07",
          level: ["Intermediate"],
          offer: "Accepted",
          rate: 5,
          userexp:"The interview experience was very good. Candidate must possess basic DSA knowledge."
        },

        {
          id:2,
          name: "Kirat",
          email: "kirat@gmail.com",
          gender: "Female",
          company: "Enest Technologies",
          position: "Software Engineer",
          date: "2022-02-09",
          level: ["Beginner"],
          offer: "Decline",
          rate: 3,
          userexp:"Very easy to crack this interview. Just be familiar with basic python concepts."
        }
      ]
    }
  },

  methods:{
    submit(){

      let myDate = new Date(Date.parse(this.selected));
      let realDate =
        myDate.getFullYear() +
        "-" +
        ("0" + (myDate.getMonth() + 1)).slice(-2) +
        "-" +
        ("0" + myDate.getDate()).slice(-2);
      var newexperience= {
          id:this.id,
          name: this.name,
          email: this.email,
          gender: this.gender,
          company: this.company,
          position: this.position,
          date: realDate,
          level: this.level,
          offer: this.offer,
          rate: this.rate,
          userexp:this.userexp
      }
      this.experiences.push(newexperience);
          this.name="",
          this.email= "",
          this.gender= null,
          this.company= "",
          this.position= "",
          this.selected= new Date(),
          this.level= [],
          this.offer= null,
          this.rate=0,
          this.userexp="",
          this.id++;
    },

    clearDate () {
            this.selected = null
        }
  }
}
</script>

<style>

</style>
