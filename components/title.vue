<template>
  <v-row
      class="d-flex flex-column justify-center title-wrapper mt-8"
    >
      <h1
        class="mx-auto mb-0 title-background"
      >
        {{ title }}
      </h1>

      <h2
        class="mx-auto mb-0 title-primary"
      >
        {{ title }}
      </h2>
    </v-row>
</template>

<script>
export default ({
  name: 'Title',
  props: [
   'title'
  ]
})
</script>
