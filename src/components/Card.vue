<template>
<div class="card" :class="classObject">
    <div class="overflow-hidden">
        <img :src="hotel.imageUrl" alt="hotel.name" style="width:100%">
    </div>
    <div class="card-price">
        <div style="display:flex">
            <div class="start score-color" style="font-size: 1rem;" v-for="score in hotel.score" v-bind:key="score">
                ☆
            </div>
        </div>
        <div class="card-price-content" v-if="recompensa">
            {{day}} <strong>${{hotel.specialRate}}</strong> 
        </div>
        <div class="card-price-content" v-else>
            {{day}} <strong>${{hotel.normalRate}}</strong> 
        </div>
    </div>
  <div class="container">
    <h4 class="text-left"><b>{{hotel.name}}</b></h4>
    <span class="btn curso-pointer" @click="reserve(hotel)" :class="{reserve: hotel.reserve}" >Reserva</span>
    <div class="box-flex mt-1">
        <div class="start no-color curso-pointer" v-for="score in hotel.score" 
            v-bind:key="score" @click="rateHotel(score)" :class="{active: score <= rate}">
            ☆
        </div>
    </div>
  </div>
</div>
</template>
<script>
export default {
  name: 'Card',
  props: {
    hotel: {},
    recompensa : Boolean,
    day: String
  },
  data(){
      return {
          rate: 0
      }
  },
  methods:{
    rateHotel(rate){
        this.rate = rate;
    },
    reserve(hotel){
        hotel.reserve = !hotel.reserve || false;
        console.log(hotel);
    }
  },
  computed: {
    classObject() {
        return {
            activeNormalRate: this.hotel.cheaperNormalRate && !this.recompensa,
            activeSpecialRate: this.hotel.cheaperSpecialRate && this.recompensa
        }
    }
    }
}
</script>
<style scoped lang="scss">
    .card {
        box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
        transition: 0.3s;
        width: 32%;
        margin: 5px;
        @media only screen and (max-width: 767px){
            width: 90%;
        }
        &-price{
            width: 100%;
            display: flex;
            justify-content: space-around;
            align-items: flex-end;
            margin-top: -2rem;
            padding-right: 20px;
            &-content{
                width: 200px;
                border-radius: 6px;
                border: 1px solid #ccc;
                padding: 12px 20px 12px 20px;
                background: #ffff;
            }
        }
    }
    img{
        margin-bottom: -1.1vw;
        display: block;
        flex-grow: 1;
    }
    .card:hover {
    box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2);
    }

    .container {
            padding: 2px 16px 16px;
    }
    .start{
        font-size: 2rem;
    }
    .score-color{
        color: #e6c311;
    }
    .active{
        color: #e6c311 !important;
    }
    .no-color{
        color: #2c3e50
    }
    h4{
        text-align: center;
    }
    .activeNormalRate{
        box-shadow: 0 4px 8px 0 #e1be0de6  !important;
        color:#f03f51
    }
    .activeSpecialRate{
        box-shadow: 0 4px 8px 0 #e1be0de6 !important;;
        color:#f03f51
    }
    .btn{
        background-color: #ffff;
        color: #270570;
        border: 1px solid #cccccc;
        padding: 5px;
        font-size: 0.9rem;
        font-weight: 500;
        border-radius: 6px;
    }
    .reserve{
        background: #f03f51;
    }
</style>
