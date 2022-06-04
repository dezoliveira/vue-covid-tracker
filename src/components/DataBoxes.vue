<template>
  <div class="grid md:grid-cols-2 gap-4 mb-4">
    <!-- Box 1 -->
    <div class="shadow-md border bg-green-500 text-white p-10 text-center rounded d-flex justify-content-center">
      <i class="fas fa-heartbeat text-3xl"></i>
      <h3 class="text-3xl text-white-900 font-bold mb-4">
        Casos
      </h3>

      <div class="text-2xl mb-4">
        <span class="font-bold">Novos:</span>
        {{numberFormatter(stats.NewConfirmed)}}
      </div>

      <div class="text-2xl mb-4">
        <span class="font-bold">Total:</span>
        {{numberFormatter(stats.TotalConfirmed)}}
      </div>

    </div>

    <!-- Box 2 -->
    <div class="shadow-md bg-red-500 text-white p-10 text-center rounded d-flex justify-content-center">
      <i class="fas fa-procedures text-3xl"></i>
      <h3 class="text-3xl text-white-900 font-bold mb-4">
        Mortos
      </h3>

      <div class="text-2xl mb-4">
        <span class="font-bold">Novos:</span>
        {{numberFormatter(stats.NewDeaths)}}
      </div>

      <div class="text-2xl mb-4">
        <span class="font-bold">Total:</span>
        {{numberFormatter(stats.TotalDeaths)}}
      </div>

    </div>

  </div>

</template>

<script>
export default {
  name: 'DataBoxes',
  props: ['stats'],
  methods: {
    numberFormatter(x){
      if(x > 999 && x < 1000000){
        return (x/1000).toFixed(1) + 'K'; // convert to K for number from > 1000 < 1 million 
    }else if(x > 1000000){
        return (x/1000000).toFixed(1) + 'M'; // convert to M for number from > 1 million 
    }else if(x < 900){
        return x; // if value < 1000, nothing to do
    }
    }
  }
}
</script>
