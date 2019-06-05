<template>
  <div class="hello">
    <div class="holder">
      <form @submit.prevent="addSkill">
        <input
          class="skill-input"
          type="text"
          placeholder="Enter a skill you have..."
          v-model="skill"
        >
        <!-- {{skill}} -->
      </form>
      <ul>
        <li v-for="(data, index) in skills" :key="index">{{ data.skill }}</li>
      </ul>
      <p>These are the skills that you posses:</p>
    </div>
    <!-- v-bind example without object -->
    <!-- <div v-bind:class="{ alert: showAlert, 'another-class': showClass }"></div> -->

    <!-- v-bind example with object -->
    <!-- <div v-bind:class="alertObject"></div> -->

    <!-- Binding the style now and not just toggling classes -->
    <!-- <div v-bind:style="{ backgroundColor: bgColor, width: bgWidth, height: bgHeight}"></div> -->
  </div>
</template>

<script>
export default {
  name: 'Skills',
  data() {
    return {
      skill: '',
      skills: [{ skill: 'Vue.js' }, { skill: 'Frontend Developer' }],
      // alertObject: {
      //   alert: true,
      //   'another-class': true,
      // },
      bgColor: 'yellow',
      bgWidth: '100%',
      bgHeight: '30px',
    };
  },
  methods: {
    addSkill() {
      this.skills.push({ skill: this.skill });
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.holder {
  background: #fff;
}

ul {
  margin: 0;
  padding: 0;
  list-style-type: none;
}

ul li {
  padding: 20px;
  font-size: 1.3em;
  background-color: #e0edf4;
  border-left: 5px solid #3eb3f6;
  margin-bottom: 2px;
  color: #3e5252;
}

p {
  text-align: center;
  padding: 30px 0;
  color: gray;
}
.skill-input {
  width: 100%;
  color: papayawhip;
  background-color: black;
  padding: 20px;
  font-size: 1.3em;
}
::placeholder {
  color: whitesmoke;
}
.container {
  box-shadow: 0px 0px 40px lightgray;
}
</style>
