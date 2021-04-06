<template>
  <v-card flat>
    <v-snackbar v-model="snackbar" absolute top right color="success">
      <v-icon dark> mdi-checkbox-marked-circle </v-icon>
      <span>Registration successful!</span>
    </v-snackbar>
    <v-form ref="form" @submit.prevent="submit">
      <v-container fluid>
        <v-row>
          <v-col cols="12" sm="6">
            <v-text-field
              v-model="form.firstName"
              :rules="rules.name"
              color="success darken-2"
              label="Firstname"
              required
            ></v-text-field>
          </v-col>
          <v-col cols="12" sm="6">
            <v-text-field
              v-model="form.lastName"
              :rules="rules.name"
              color="success darken-2"
              label="Lastname"
              required
            ></v-text-field>
          </v-col>
          <v-col cols="12" sm="6">
            <v-text-field
              v-model="form.email"
              :rules="rules.email"
              color="success darken-2"
              label="Email"
              required
            ></v-text-field>
          </v-col>
          <v-col cols="12">
            <v-textarea
              v-model="form.message"
              color="teal"
              label="Message"
              required
            >
            </v-textarea>
          </v-col>
        </v-row>
      </v-container>
      <v-card-actions>
        <v-btn text @click="resetForm"> Cancel </v-btn>
        <v-spacer></v-spacer>
        <v-btn :disabled="!formIsValid" text color="primary" type="submit">
          Submit
        </v-btn>
      </v-card-actions>
    </v-form>
  </v-card>
</template>

<script>
export default {
  data() {
    const defaultForm = Object.freeze({
      firstName: '',
      lastName: '',
      email: '',
      message: '',
    })

    return {
      form: Object.assign({}, defaultForm),
      rules: {
        firstName: [
          (val) => (val || '').length > 0 || 'This field is required',
        ],
        lastName: [(val) => (val || '').length > 0 || 'This field is required'],
        email: [(val) => (val || '').length > 0 || 'This field is required'],
        message: [(val) => (val || '').length > 0 || 'This field is required'],
      },
      defaultForm,
    }
  },

  computed: {
    formIsValid() {
      return (
        this.form.firstName &&
        this.form.lastName &&
        this.form.email &&
        this.form.message
      )
    },
  },

  methods: {
    resetForm() {
      this.form = Object.assign({}, this.defaultForm)
      this.$refs.form.reset()
    },
    submit() {
      this.snackbar = true
      this.resetForm()
    },
  },
}
</script>