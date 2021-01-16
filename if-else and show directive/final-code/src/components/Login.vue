<template>
  <div class="main-content bg-default">
    <b-container>
      <b-row cols="12">
        <b-col cols="6" offset="3">
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
                    <b-form-input id="username" v-model="model.email" type="text"></b-form-input>
                    <span v-if="model.email.length<2" class="error">username is required</span>
                    <span v-else-if="model.email.length>=2 && model.email.length<4" class="error">username is not correct</span>
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
                      type="password" v-model="model.password"></b-form-input>
                      <span v-show="model.password.length<2" class="error">password is required</span>

                  </b-col>
                </b-row>
                <b-row class="my-1 mb-3">
                  <b-col sm="9">
                    <b-form-checkbox
                      id="rememberMe"
                      name="rememberMe"
                       v-model="model.rememberMe"
                      value="true" unchecked-value="false"
                    >
                      Remember Me
                    </b-form-checkbox>
                  </b-col>
                </b-row>
              </b-container>
            </b-card-body>
            <b-button  variant="primary">Sign in</b-button>
          </b-card>
        </b-col>
      </b-row>
      <div class='output-container'>
      {{model}}
      </div>
    </b-container>
  </div>
</template>
<script>
export default {
  data() {
    return {
      model: {
        email: "",
        password: "",
        rememberMe: false,
      },
    };
  },

  methods: {
    onSubmit() {
      // this will be called only after form is valid. You can do api call here to login
    },
  },
};
</script>
<style scoped>
span.error{
  color: red;
}
div.output-container{
  margin-top: 10px;
  /* color: white; */
}
.main-content .card{
  border:1px solid black;
  box-shadow: 5px 10px 10px 2px grey; 
}
#username.error{
  border-color: red;
}
#username.error:focus{
  box-shadow: none;
}
</style>