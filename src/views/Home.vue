<template>
  <div class="home">
    <Menu class="box-flex box-space-mobile" v-on:update-taxe="updateTaxeRegular" v-on:update-date="updateDate" />
    <div class="box-flex box-flex-mobile">
      <Card v-for="hotel in hotels"  v-bind:key="hotel" :hotel = hotel :recompensa = recompensa :day = day  />
    </div>
  </div>
</template>

<script>
import Menu from '@/components/Menu.vue';
import Card from '@/components/Card.vue';
import hotels from '@/assets/json/Hotels.json';

export default {
  name: 'Home',
  components: {
    Menu,
    Card
  },
  data() {
    return {
      hotels: [],
      recompensa: false,
      days : ["Lunes", "Martes", "Miercoles", "Jueves", "Viernes", "Sabado","Domingo"],
      day : String
    }
  },
  created(){
    this.updateDate(new Date());
  },
  methods:{
    updateTaxeRegular(type){
      type == "Regular" ? this.recompensa = false : this.recompensa = true;
    },
    updateDate(updateDate){
			const date = new Date(updateDate);
      this.day = this.days[date.getDay()]
      this.day == "Sabado" || this.day == "Domingo" ? this.updatePrices(true) : this.updatePrices(false)
    },
    updatePrices(isWeekend){
      this.hotels = hotels.map((acc) => ({
        imageUrl:acc.imageUrl,
        name:acc.name,
        normalRate: isWeekend == true ? acc.weekendRate : acc.normalRate,
        specialRate: isWeekend == true ? acc.specialWeekendRate : acc.specialRate,
        score:acc.score
      }), {})
      this.searchsCheaperRate()
    },
    searchsCheaperRate(){
      this.hotels = this.hotels.map((acc, index) => ({
        imageUrl:acc.imageUrl,
        name:acc.name,
        normalRate: acc.normalRate,
        specialRate: acc.specialRate,
        cheaperNormalRate: this.finder(Math.min, this.hotels, function(x) { return x.normalRate; }, index, 'normalRate'),
        cheaperSpecialRate: this.finder(Math.min, this.hotels, function(x) { return x.specialRate; }, index, 'specialRate'),
        score:acc.score
      }), {})
    },
    finder(cmp, arr, getter, index, typeRate) {
      let isLess = false;
      var val = getter(arr[0]);
      for(var i=1;i<arr.length;i++) {
          val = cmp(val, getter(arr[i]))
      }
      if(arr[index][typeRate] == val ) isLess = true
      return isLess;
    }
  }
}
</script>

<style scoped lang="scss">

</style>