<template>

  <div class="">
    <v-card
      class="my-16 mx-auto"
      max-width="600"
      variant="outlined"
    >
      <v-card class="mx-5 mt-10" >
        <h1 class="text-center mb-8"><u>Tell My Age</u></h1>

        <v-text-field
          v-model="Name"
          label="Name"
        ></v-text-field>

        <v-text-field
          v-model="DOB"
          label="Date of Birth"
        ></v-text-field>

        <v-card-actions>
          <v-btn type="submit" variant="flat" block color="info"  class="">View Age</v-btn>
        </v-card-actions>
      </v-card>
      <p class="text-center mx-10 my-10 text-orange font-weight-medium" >Hi ! kaveesha, you've lived :
        --years, --months, --days, --hours, --minits, --seconds</p>
    </v-card>
  </div>



</template>

<script>
  export default{
    name: "HomePage",
    data(){
      return({
        dob:'2000/05/20',
        name:'Kaveesha'
      })
    },
    methods: {

    }
  }
</script>
