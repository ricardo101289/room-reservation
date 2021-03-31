<template>
  <div class="menu text-left">
    <div class="date">
      Fecha
      <input type="date" name="" id="" class="calendar" v-model="myDate" @change="changeDate(myDate)" />
    </div>
    <div class="menu-toogle" style="width:20%">
      {{ typeTaxe }}
      <Toogle v-on:change-taxe="updateTaxe" />
    </div>
  </div>
</template>
<script>
import Toogle from "@/components/Toogle.vue";
export default {
  name: "Menu",
  components: {
    Toogle,
  },
  data() {
    return {
      typeTaxe: "Regular",
      myDate: ""
    };
  },
  methods: {
    updateTaxe(type) {
      this.typeTaxe = type || this.typeTaxe;
      this.$emit('update-taxe', this.typeTaxe)
      this.changeDate(this.myDate || new Date())
    },
    changeDate(date){
        this.$emit('update-date', date)
    }
  },
};
</script>
<style scoped lang="scss">
.menu {
  padding-bottom: 1rem;
  &-toogle {
    display: flex;
    flex-direction: column;
  }
}
.calendar {
  display: block;
  width: 90%;
  padding: 0.3rem;
  font-size: 1rem;
  line-height: 1.25;
  color: #464a4c;
  background-color: #fff;
  border: 1px solid rgba(0, 0, 0, 0.15);
  border-radius: 0.25rem;
}
.date{
    width: 30%;
    @media only screen and (max-width: 576px){
        width: 45%;
    }
}
</style>
