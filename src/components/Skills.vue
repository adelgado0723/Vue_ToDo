<template>
  <div class="hello">
    <div class="holder">
      <form @submit.prevent="addSkill">
        <input
          class="skill-input"
          type="text"
          placeholder="Enter a skill you have..."
          v-model="skill"
          v-validate="'min:5'"
          name="skill"
        >
        <transition
          name="alert-in"
          enter-active-class="animated flipInX"
          leave-active-class="animated flipOutX"
        >
          <p class="alert" v-if="errors.has('skill')">{{ errors.first('skill') }}</p>
        </transition>
        <!-- {{skill}} -->
      </form>
      <ul>
        <transition-group
          name="list"
          enter-active-class="animated bounceInUp"
          leave-active-class="animated bounceOutDown"
        >
          <li v-for="(data, index) in skills" :key="index">
            {{ data.skill }}
            <i class="fa fa-minus-circle" v-on:click="remove(index)"></i>
          </li>
        </transition-group>
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
      // bgColor: 'yellow',
      // bgWidth: '100%',
      // bgHeight: '30px',
    };
  },
  methods: {
    addSkill() {
      this.$validator.validateAll().then((result) => {
        if (result) {
          this.skills.push({ skill: this.skill });
          this.skill = '';
        } else {
          console.log('Not Valid!');
        }
      });
    },
    remove(id) {
      this.skills.splice(id, 1);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import url('https://cdnjs.cloudflare.com/ajax/libs/animate.css/3.7.0/animate.min.css');
@import url('https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css');
.holder {
  background: #fff;
  /* display: grid; */
  /* grid-template-columns: 1fr; */
  /* width: 100%; */
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
  color: papayawhip;
  /* border-left: 5px solid #3eb3f6; */
  margin-bottom: 2px;
  background-color: black;
  padding: 20px;
  font-size: 1.3em;
  outline: none;
  /* list-style-type: none; */
  /* grid-column: 1/-1; */
  border: 0;
  width: calc(100% - 40px);
}
form {
  /* grid-row: 1/2; */
  /* width: 44.5vw; */
  width: 100%;
}
::placeholder {
  color: whitesmoke;
}
.container {
  box-shadow: 0px 0px 40px lightgray;
}
.alert {
  height: 30px;
  width: 100%;
  background-color: papayawhip;
  display: inline-block;
  padding: 5px;
  margin-top: -20px;
  font-weight: bold;
}
/* .alert-in-enter-active {
  animation: bounce-in 0.5s;
}
.alert-in-leave-active {
  animation: bounce-in 0.5s reverse;
}
@keyframes bounce-in {
  0% {
    transform: scale(0);
  }
  50% {
    transform: scale(1.5);
  }
  100% {
    transform: scale(1);
  }
} */
i {
  float: right;
}
</style>
