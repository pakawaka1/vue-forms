<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div class="columns" id="app">
      <div class="column is-two-thirds">
        <section class="section">
          <h1 class="title">Fun with Forms in Vue 2.0</h1>
          <p class="subtitle">
            Learn how to work with forms, including <strong>validation</strong>!
          </p>
          <hr />

          <!-- form starts here -->
          <section class="form">
            <!------------------------------------------ Name Field--------------------------->
            <div class="field">
              <label class="label">Name</label>
              <div class="control">
                <input
                  @input="showName"
                  v-model="form.name"
                  class="input"
                  type="text"
                  placeholder="Text input"
                />
              </div>
            </div>
            <!-------------------------------- Message Field --------------------------------------------->
            <div class="field">
              <label class="label">Message</label>
              <div class="control">
                <textarea
                  v-model="form.message"
                  class="textarea"
                  placeholder="Message"
                ></textarea>
              </div>
            </div>
            <!------------------------------ Inquiry Type (with options in JS)-------------------------------------->
            <div class="field">
              <label class="label">Inquiry Type</label>
              <div class="control">
                <div class="select">
                  <select v-model="form.inquiry_type">
                    <option disabled value="">Nothing selected</option>
                    <option
                      v-for="option in options.inquiry"
                      :key="option.value"
                    >
                      {{ option.text }}
                    </option>
                  </select>
                </div>
              </div>
            </div>
            <!---------------Use Cases (multiple options in HTML)---------------------------------------------->
            <div class="field">
              <label class="label">LogRocket Usecases</label>
              <div class="control">
                <div class="select is-multiple">
                  <select multiple v-model="form.logrocket_usecases">
                    <option>Debugging</option>
                    <option>Fixing Errors</option>
                    <option>User support</option>
                  </select>
                </div>
              </div>
            </div>

            <!---terms (true/false)  -->
            <div class="field">
              <div class="control">
                <label class="checkbox">
                  <input type="checkbox" v-model="form.terms" />
                  I agree to the <a href="#">terms and conditions</a>
                </label>
              </div>
            </div>

            <!---------- concepts(multiple checkbox values)------->
            <div class="field">
              <label>
                <strong>What dev concepts are you interested in?</strong>
              </label>
              <div class="control">
                <label class="checkbox">
                  <input
                    type="checkbox"
                    v-model="form.concepts"
                    value="promises"
                  />
                  Promises
                </label>
                <label class="checkbox">
                  <input
                    type="checkbox"
                    v-model="form.concepts"
                    value="testing"
                  />
                  Testing
                </label>
              </div>
            </div>
            <!---------------------------single radio button-->>
            <div class="field">
              <label>
                <strong>Is JavaScript awesome?</strong>
              </label>
              <div class="control">
                <label class="radio">
                  <input v-model="form.js_awesome" type="radio" value="Yes" />
                  Yes
                </label>
                <label class="radio">
                  <input v-model="form.js_awesome" type="radio" value="Yeap!" />
                  Yeap!
                </label>
              </div>
            </div>
            <div class="field is-grouped">
              <div class="control">
                <button class="button is-primary" @click="getName">
                  Submit
                </button>
              </div>
            </div>
          </section>
        </section>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Form',
  props: {
    msg: String,
  },

  data() {
    return {
      form: {
        name: '',
        message: '',
        inquiry_type: '',
        logrocket_usecases: [],
        terms: false,
        concepts: [],
        js_awesome: '',
      },
      options: {
        inquiry: [
          { value: 'feature', text: 'Feature Request' },
          { value: 'bug', text: 'Bug Report' },
          { value: 'support', text: 'Support' },
        ],
      },
    };
  },

  computed: {
    // Return cached values until dependencies change
  },
  watch: {},
  methods: {
    showName() {
      this.$emit('nameChange', this.form.name);
    },
    getName() {
      alert('Thank you ' + this.form.name + 'for your submittal.');
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
