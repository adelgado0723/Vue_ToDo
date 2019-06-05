<template>
  <div class="about">
    <h1>Hello {{ their_name }}, this is an About page</h1>
    <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Voluptatum numquam recusandae itaque aperiam earum consequatur. Modi molestias quia eligendi voluptatibus, necessitatibus repudiandae consequatur, beatae, rerum voluptatum excepturi recusandae dolorum laudantium.</p>
  </div>
</template>

<script>
export default {
  name: 'Skills',
  data() {
    return {
      their_name: this.$route.params.name,
    };
  },
};
</script>
