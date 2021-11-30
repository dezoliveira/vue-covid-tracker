<template>

  <label class="flex justify-center form-select">Selecione um País:</label>
  <div class="flex justify-center align-center">
    <select @change="onChange()" 
      v-model="selected" 
      class="text-center form-select bg-white w-80 mb-10 block border p-3 rounded  focus:outline-none focus:ring-2 focus:ring-green-600 shadow-md"
      >
<option value="0">--</option>
      <option 
        v-for="country in countries"
        :value="country.ID"
      >
        {{country.Country}}
      </option>
    </select>
  </div>
</template>

<script>
export default {
  name: 'CountrySelect',

  props: ['countries'],
  
  data(){
    return {
      selected: 0
    }
  },

  methods:{
    onChange() {

      const country = this.countries.find((item) => item.ID === this.selected)
      this.$emit('get-country', country)
    },
  }

}
</script>
