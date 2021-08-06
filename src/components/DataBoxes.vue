<template>
  <div class="grid md:gridd-cols-2 gap-4">
    <!-- Box 1  -->
    <div class="shadow-mf bg-blue-100 p-10 text-center rounded">
      <h3 class="text-3xl text-blue-900 font-bold mb-4">
        Cases

        <div class="text-2xl mb-4">
          <span class="font-bold">New:</span>
          {{ stats.NewConfirmed }}
        </div>
        <div class="text-2xl mb-4">
          <span class="font-bold">Total:</span>
          {{ stats.TotalConfirmed }}
        </div>
      </h3>
    </div>
    <!-- Box 2  -->
    <div class="shadow-mf bg-blue-100 p-10 text-center rounded">
      <h3 class="text-3xl text-blue-900 font-bold mb-4">
        Cases

        <div class="text-2xl mb-4">
          <span class="font-bold">New:</span>
          {{ stats.NewDeaths }}
        </div>
        <div class="text-2xl mb-4">
          <span class="font-bold">Total:</span>
          {{ stats.TotalDeaths }}
        </div>
      </h3>
    </div>
  </div>
</template>

<script>
export default {
  name: 'DataBoxes',
  props: ['stats'],
  methods: {},
};
</script>

<style>
</style>
