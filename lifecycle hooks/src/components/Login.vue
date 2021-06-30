<template>
  <div class="main-content bg-default">
    <b-container>
      <div v-html="htmlVar" class="mb-4"></div>
      <b-row cols="12" class="mb-4">
        <b-col sm="6">
          <UserList ComponentTitle="Parent" :html="htmlVar" />
        </b-col>
        <b-col cols="6">
          <b-card
            title="Sign in"
            img-src="img/brand/large logo.png"
            img-alt="Image"
            img-top
            tag="article"
          >
            <b-card-body>
              <b-container fluid>
                <b-row class="my-1 mb-3">
                  <b-col sm="3">
                    <label for="username">User name:</label>
                  </b-col>
                  <b-col sm="9">
                    <b-form-input
                      id="username"
                      v-model="model.email"
                      type="text"
                      @blur="usernameBlur"
                      @keyup.enter="usernameBlur"
                      :class="{ error: model.email.length < 2 }"
                    >
                    </b-form-input>
                    <span v-if="model.email.length < 2" class="error">
                      username is required
                    </span>
                    <span
                      v-else-if="
                        model.email.length >= 2 && model.email.length < 4
                      "
                      class="error"
                    >
                      username is not correct
                    </span>
                    <span v-else>user name is correct</span>
                  </b-col>
                </b-row>
                <b-row class="my-1 mb-3">
                  <b-col sm="3">
                    <label for="passwordfield">password:</label>
                  </b-col>
                  <b-col sm="9">
                    <b-form-input
                      id="passwordfield"
                      type="password"
                      v-model="model.password"
                      :class="[model.password.length < 2 ? 'error' : 'success']"
                    ></b-form-input>
                    <span v-show="model.password.length < 2" class="error"
                      >password is required</span
                    >
                  </b-col>
                </b-row>
                <b-row class="my-1 mb-3">
                  <b-col sm="9">
                    <b-form-checkbox
                      id="rememberMe"
                      name="rememberMe"
                      v-model="model.rememberMe"
                      value="true"
                      unchecked-value="false"
                    >
                      Remember Me
                    </b-form-checkbox>
                  </b-col>
                </b-row>
              </b-container>
            </b-card-body>
            <b-button
              variant="primary"
              v-bind:disabled="signinDisable"
              v-on:click="onSubmit($event)"
              >Sign in</b-button
            >
          </b-card>
        </b-col>
      </b-row>
      <b-row cols="12">
        <b-col cols="6" offset="6">
          {{ model }}
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>
<script>
import UserList from "./UserList.vue";
export default {
  beforeCreate: function () {
    console.log("before created", this.model);
  },
  created: function () {
    console.log("created", this.model);
  },
  beforeMount: function () {
    console.log("before mounted", this.model, this.$el);
  },  
  mounted: function () {
    console.log("mounted", this.$el.innerText);
    setTimeout(()=>{
      this.destroyed()
    }, 2000)
  },
  beforeUpdate: function () {
    console.log("before update",this.model.email);
  },
  updated: function () {
    console.log("updated",this.model.email);
  },
  beforeDestroy: function () {
    console.log("before destroy");
  },
  destroyed: function () {
    console.log("destroy");
  },
  components: {
    UserList,
  },
  data() {
    return {
      model: {
        email: "",
        password: "",
        rememberMe: false,
      },
      htmlVar: "<span>Hi there</span>",
    };
  },
  computed: {
    signinDisable: function () {
      return this.model.email.length < 2 || this.model.password.length < 2;
    },
  },
  methods: {
    onSubmit(event) {
      // this will be called only after form is valid. You can do api call here to login
      console.log(event);
      console.info("submit");
    },
    usernameBlur() {
      console.log("usernameBlur");
    },
    userSelected(event, userId) {
      console.log(event);
      console.log(`selected user id ${userId}`);
    },
  },
};
</script>
<style scoped>
span.error {
  color: red;
}

div.output-container {
  margin-top: 10px;
  /* color: white; */
}
.main-content .card {
  border: 1px solid black;
  box-shadow: 5px 10px 10px 2px grey;
}
input.error {
  border-color: red;
}
input.error:focus {
  box-shadow: none;
}
input.success {
  border-color: green;
}
input.success:focus {
  box-shadow: none;
}
.pointer {
  cursor: pointer;
}
</style>