<template>
<div class="cardComponentWrapper">
  <p>{{ title }}</p>
  <p>{{ price  }}  <span class="cardComponentPriceSpan" v-if="periodMentioned"> / {{ periodMentioned }}</span>   </p>
  <div class="cardComponentList">
  <slot name="dropdownCard"></slot>
    <div class="cardComponentBenefits">
    <p v-for="benefit of benefits">{{ benefit }}</p>
    </div>
  </div>

  <button :class="active ? 'active' : ''">{{ button }}</button>
  </div>
</template>

<script>
export default {
  name: 'CardComponent',
  props:{
    title:{
      type:String,
      required:true,
    },
    price:{
      type:String,
      required:true,

    },
    benefits:{
      required:true,
    },
    button:{
      type:String,
      required:true,
    },
    active:{
      type:Boolean
    },
    periodMentioned:{
      type:String
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
