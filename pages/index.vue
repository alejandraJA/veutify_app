<template>
  <section class="body">
    <v-card elevation="2" class="container">
      <LoginVue class="item" />
      <SingIn class="item" />
    </v-card>
  </section>
</template>

<script>
import LoginVue from "../components/Login.vue";
import SingIn from "../components/SingIn.vue";
export default {
  components: {
    LoginVue,
    SingIn,
  },
  data() {
    return {
      email: "",
      password: "",
      show1: false,
      rules: {
        required: (value) => !!value || "Required.",
        min: (v) => v.length >= 8 || "Min 8 characters",
        emailMatch: () => `The email and password you entered don't match`,
      },
      rulesEmail: {
        required: (value) => !!value || "Required.",
        counter: (value) => value.length <= 20 || "Max 20 characters",
        email: (value) => {
          const pattern =
            /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
          return pattern.test(value) || "Invalid e-mail.";
        },
      },
      switch1: true,
    };
  },
};
</script>

<style>
.body {
  padding: 32px;
}
.title {
  font-size: 32px;
}

.subtitle {
  font-size: 16px;
  font-weight: 300;
}

.container {
  display: flex;
  align-items: center;
  background: #191d26;
  justify-content: center;
  padding: 32px;
}

.item {
}
</style>
