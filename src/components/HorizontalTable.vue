<template>
  <div class="about">
    <b-btn v-b-toggle.collapse1 variant="primary">Toggle Detailed Lines</b-btn>
    <b-collapse id="collapse1" class="mt-2">
        <!-- <b-card> -->
            <b-table hover :items="items"></b-table>
        <!-- </b-card> -->
    </b-collapse>
  </div>
</template>

<script>
export default {
  name: "horizontaltable",
  data() {
    return {
      items: [
        {
          train_service: true,
          affected_operator: 40,
          delay_time: "Dickerson",
          time_to_delay: "Macdonald",
          confidence: "70%"
        }
      ]
    };
  }
};
</script>

<style scoped>

</style>
