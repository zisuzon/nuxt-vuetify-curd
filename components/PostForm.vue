<template>
  <v-layout row wrap align-center>
    <v-flex xd12>
      <h3 class="display-3">Write a new Post</h3>
      <v-form ref="form" v-model="valid" lazy-validation>
        
        <v-text-field
          v-model="title"
          :rules="titleRules"
          :counter="10"
          label="Title"
          required
        ></v-text-field>

        <v-text-field
          textarea
          v-model="description"
          :rules="descriptionRules"
          label="Description"
          required
        ></v-text-field>

        <v-text-field
          v-model="imageUrl"
          :rules="imageUrlRules"
          label="Image Url"
          required
        ></v-text-field>
    
        <v-btn
          :disabled="!valid"
          @click="submit"
        >
          submit
        </v-btn>

        <v-btn @click="clear">clear</v-btn>
      
      </v-form>
    </v-flex>
  </v-layout>
</template>

<script>
export default {
  data: () => ({
    valid: true,
    title: null,
    titleRules: [
      v => !!v || 'Title is required'
    ],
    description: null,
    descriptionRules: [
      v => !!v || 'Description is required'
    ],
    imageUrl: null,
    imageUrlRules: [
      v => !!v || 'Image Url is required'
    ]
  }),
  methods: {
    submit () {
      if (this.$refs.form.validate()) {
        console.log('SUBMIT THE FUCKING FORM')
        // axios.post('/api/submit', {
        //   name: this.name,
        //   email: this.email,
        //   select: this.select,
        //   checkbox: this.checkbox
        // })
      }
    },
    clear () {
      this.$refs.form.reset()
    }
  }
}
</script>
