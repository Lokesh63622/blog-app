<template>
  <div class="home">
    <h2>Welcome, {{ user.username }}!</h2>
      <p
        class="latter-space"
        style="width: 50%; margin-left: 28%;font-style: italic"
      >
        <b>Subject: Update on Task </b> Hi sir I hope this
        message finds you well. I wanted to provide you with an update regarding
        Blog App. Unfortunately, I haven't been able to complete the task as
        planned due to in my current project we are going live on monday for
        that we are resolveing the defects from last one week. I sincerely
        apologize for any inconvenience please go thought my git all the other
        task done by me 
        <a href="https://github.com/Lokesh63622/Task1CRUD"
          >https://github.com/Lokesh63622/Task1CRUD</a
        > and
        <br />
        <a href="https://github.com/Lokesh63622/VisaRejectionTask"
          >https://github.com/Lokesh63622/VisaRejectionTask</a
        >
        go through the above links if i am fit to ur projrct please let me know
        i belive i will give my 100% work to company thank you
      </p>
    <button class="back-g" @click="logout">Sign Out</button>
  </div>
</template>

<script>
export default {
  name: "HomePage",
  computed: {
    user() {
      return this.$store.state.user;
    },
  },
  methods: {
    logout() {
      // Clear user data and redirect to login page
      this.$store.commit("logout");
      this.$router.push("/login");
    },
  },
};
</script>

<style scoped>
.latter-space {
  word-break: keep-all;
};
button{
  background: transparent;
  border: none;
  outline: none;
  color: #fff;
  background: #03a9f4;
  padding: 10px 20px;
  cursor: pointer;
  border-radius: 5px;
}
/* .home {
    max-width: 300px;
    margin: 0 auto;
  } */
</style>
