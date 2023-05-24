<template>

  <div class="">
    <v-card
      class="my-16 mx-auto"
      max-width="600"
      variant="outlined"
    >
      <v-card class="mx-5 my-10" >
        <h1 class="text-center mb-8"><u>Tell My Age</u></h1>

        <v-text-field
          v-model="name"
          label="Name"
        ></v-text-field>

        <v-text-field
          v-model="dob"
          label="Date of Birth "
          placeholder="YYYY-MM-DD"
        ></v-text-field>

        <v-card-actions>
          <v-btn type="submit"  @click="calculateAge" variant="flat" block color="info" >View Age</v-btn>
        </v-card-actions>
      </v-card>
      <p id="T1" class=" text-center mx-10 my-10 text-orange font-weight-medium" style="display: none;">Hi ! {{ name }}, you've lived :
        {{year}} years, {{month}} months, {{ days }} days, {{ hours }} hours, {{ min }} minits, {{ sec }} seconds</p>
      <hr>
      <p id="T2" class=" text-center mx-10 my-5 text-red font-weight-medium" style="display: none;">Your Next Birthday is coming up in {{to_next}} Days</p>
    </v-card>

  </div>



</template>

<script>
  export default{
    name: "HomePage",
    data(){
      return({
        dob:'',
        name:'',
        year:'',
        month:'',
        days:'',
        hours:'',
        min:'',
        sec:'',
        to_next:''

      })
    },
    methods: {
      calculateAge(){
        let dob = new Date(this.dob);
        let today = new Date();

        let ageInMills = today- dob;
        let ageInSec = Math.floor(ageInMills/1000);

        let year = Math.floor(ageInSec/31536000);
        ageInSec %= 31536000;

        let month = Math.floor(ageInSec/2628000);
        ageInSec %= 2628000;

        let days = Math.floor(ageInSec/86400);
        ageInSec %= 86400;

        let hours = Math.floor(ageInSec/3600);
        ageInSec %= 3600;

        let min = Math.floor(ageInSec/60);
        ageInSec %= 60;

        this.year = year;
        this.month = month;
        this.days = days;
        this.hours = hours;
        this.min = min;
        this.sec = ageInSec;

        this.showText();
        this.daysToNextBirthday();
        //setInterval(this.calculateAge,1000);
      },

      daysToNextBirthday(){
        let dob = new Date(this.dob);
        let today = new Date();
        let next = new Date(today.getFullYear(),dob.getMonth(),dob.getDate());
        if (next<today){
          next.setFullYear(today.getFullYear()+1);
        }
        this.to_next = Math.round((next-today)/86400000);
      },

      showText(){
        let txt1 = document.getElementById("T1");
        let txt2 = document.getElementById("T2");

        txt1.style.display = "block";
        txt2.style.display = "block";
      }

    }
  }
</script>
