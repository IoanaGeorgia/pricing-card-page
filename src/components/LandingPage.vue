<template>
  <div class="mainWrapper">

    <div class="currentPlanWrapper">
      <p>Your current plan</p>
      <p>Starter Trial . 500MAUs</p>
    </div>


    <p class="planTitle">Choose a plan</p>

    <p class="billedOption">
      <span>Billed monthly</span>
      <label class="billingOptionButton">
        <input type="checkbox">
        <span class="billingOptionSlider round"></span>
      </label>
      <span>Billed annualy</span>
    </p>


    <div class="cardWrapper">
      <div v-for="i of cardsInfoObject">
        <CardComponent :title="i.title" :price="i.price" :benefits="i.benefits" :button="i.button" :active="i.active"
          :periodMentioned="i.periodMentioned">
          <template v-slot:dropdownCard>
            <div class="cardWrapperSlot" v-if="i.dropdown">
              <div class="dropdown">
                <button class="dropbtn">{{ dropdownContent }}</button>
                <div class="dropdown-content">
                  <p @click="setDropdown('1000 MAUs')">1000 MAUs</p>
                  <p @click="setDropdown('2500 MAUs')">2500 MAUs</p>
                  <p @click="setDropdown('+5000 MAUs')">+5000 MAUs</p>
                </div>
              </div>
              <p>Monthly active users</p>
            </div>
          </template>
        </CardComponent>
      </div>

    </div>

  </div>
</template>

<script>
import CardComponent from './CardComponent.vue';
export default {
  name: 'LandingPage',
  components: { CardComponent },
  data() {
    return {
      dropdownContent: '2500 MAUs',
      cardsInfoObject: [
        {
          title: 'Starter',
          price: '$19',
          benefits: [
            '500MAUs',
            '3 projects',
            'Unlimited guides',
            'Unlimited flows',
            'Unlimited branded themes',
            'Email support',

          ],
          button: 'Choose Plan',
          active: false,


        },
        {
          title: 'Pro',
          price: '$99',
          benefits: [
            'All starter features, plus:',
            'Unlimited projects',
            'Unlimited fully customizable themes',
            'A dedicated Customer Success Manager',
          ],
          button: 'Choose Plan',
          active: true,
          dropdown: true,
          periodMentioned: 'month'
        },
        {
          title: 'Enterprise',
          price: "Let's Talk!",
          benefits: [
            'All pro features',
            'Unlimited MAUs',
            'Dedicated environment',
            'Enterprise account administration',
            'Premium support and services'
          ],
          button: 'Contact Us',
          active: false
        }
      ]
    }
  },
  methods: {
    setDropdown(dropdownInfo) {
      this.dropdownContent = dropdownInfo
    }
  }


}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
