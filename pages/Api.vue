<template>
<div class="row">
  <div class="col-md-5">
    <h1 class="m">Sign Up for Info</h1>
    <div class="form-group pb-3">
      <label for="inputName">Name</label>
      <input
        type="name"
        class="form-control"
        id="inputName"
        aria-describedby="nameHelp"
        placeholder="Enter name"
        required
      />
    </div>
    <div class="form-group pb-3">
        <label for="exampleInputEmail1">Email address</label>
        <input
          type="email"
          class="form-control"
          id="exampleInputEmail1"
          aria-describedby="emailHelp"
          placeholder="Enter email"
        />
      </div>
      <div>
       <button v-on:click="submitted=true" type="submit" class="btn btn-primary">Submit</button>
     </div>
     <div v-if="submitted">
       <h1> Thank you for your request! We will reach out soon. </h1>
     </div>
  </div>
  <div class="col-md-5">
   <CovidCases v-if="covid" :covid="covid" />
 </div>
</div>
</template>

<script>
import CovidCases from '../CovidCases.vue'

export default {
  async fetch() {
  this.covid = await fetch(
    "https://covid19-japan-web-api.now.sh/api//v1/prefectures
  ).then((res) => res.json());
  },
  components: { CovidCases },
  data() {
    return {
      value: "",
      context: null,
      show: true,
      covid: undefined,
      submitted: false,
      time1: null
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">
@import "~/node_modules/bootstrap/scss/bootstrap.scss";
@import "../scss/_base.normalize.scss";
@import "../scss/_components.content.scss";
@import "../scss/_settings.responsive.scss";
@import "../scss/_settings.variables.scss";
@import "../scss/style.scss";
</style>
