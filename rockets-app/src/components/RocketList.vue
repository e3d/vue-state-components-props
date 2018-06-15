<template lang="html">
  <div>
    <section class="row">
      <h3>hello H3</h3>

      <select v-model="currentRocket"
              placeholder="Choose rocket:">
        <option v-for="rocket in rockets"
                :key="rocket.name"
                :value="rocket">{{rocket.name}}
        </option>

      </select>    
    </section>
    <div>
      <rocket :rocket="currentRocket"></rocket>
    </div>
  </div>
</template>

<script>
import { mapGetters } from 'vuex';

import Rocket from '@/components/Rocket';

export default {
  name: 'rocket-list',
  //props: ['rockets'],
  computed: {
    // mix the getters into computed with object spread operator
    ...mapGetters([
      'rockets', 
      // 'currentRocket'
    ]),
    currentRocket: {
      get () {
        return this.$store.state.currentRocket
      },
      set (value) {
        this.$store.commit('updateCurrentRocket', value)
      }
    }
  },  

  components: {
    Rocket,
  },
};
</script>
