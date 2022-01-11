<template>
  <div>
    <h1 class="m">Covid Cases of Japanese Prefectures</h1>
    <ul>
      <li class="covidcases">
        <b>{{ name_en }}:</b>
        {{getCases(name_en.cases , name_en.deaths)}}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {

    };
  },
  name: "CovidCases",
  // Set component props
  props: {
    prefecture: {
      required: true,
    },
  },
  methods: {
  getCases(cases, deaths) {
  if (cases + death > 10000){
    return name_en.cases + name_en.death + " Danger!";
  } else {
    return name_en.cases + name_en.death + " Safe!";
  }
  },
  },
};
</script>


<style lang="scss">
// Store page content

.covidcases {
  display: block;
}

@import "~/node_modules/bootstrap/scss/bootstrap.scss";
@import "../scss/_base.normalize.scss";
@import "../scss/_components.content.scss";
@import "../scss/_settings.responsive.scss";
@import "../scss/_settings.variables.scss";
@import "../scss/style.scss";
</style>
