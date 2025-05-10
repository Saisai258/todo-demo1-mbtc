<template>
  <v-container>
    <h2>{{ title }}</h2>
    <div>
    <v-text-field label="Enter your name" v-model="name"></v-text-field>
    Hello: {{ name }}
</div>
  </v-container>
</template>

<script>

export default {
  name: 'HelloWorld',

  data: () => ({
    title: "This is My First  Vue Project",
    name:""
  }),
}
</script>
