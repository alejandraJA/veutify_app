<template>
  <section>
    <h1 class="title">Sing in</h1>
    <p class="subtitle">Welcome back</p>
    <v-form class="form">
      <v-text-field
        v-model="email"
        label="Email"
        placeholder="email@email.com"
        :rules="[rulesEmail.required, rulesEmail.counter, rulesEmail.email]"
        filled
        rounded
      />
      <v-text-field
        v-model="password"
        :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
        :rules="[rules.required, rules.min]"
        :type="show1 ? 'text' : 'Password'"
        name="input-10-1"
        label="Password"
        hint="At least 8 characters"
        counter
        @click:append="show1 = !show1"
        filled
        rounded
        dense
      />
      <v-text-field
        v-model="password"
        :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
        :rules="[rules.required, rules.min]"
        :type="show1 ? 'text' : 'Password'"
        name="input-10-1"
        label="Repeat your password"
        hint="At least 8 characters"
        counter
        @click:append="show1 = !show1"
        filled
        rounded
        dense
      />
    </v-form>
    <section>
      <v-btn
        color="primary"
        elevation="2"
        v-text="'Sing in'"
        rounded
        block
        style="margin-top: 32px"
      />
    </section>
  </section>
</template>

<script>
export default {
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
    };
  },
};
</script>

<style scoped>
</style>
