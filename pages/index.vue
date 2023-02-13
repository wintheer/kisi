<template>
  <div class="card-views">
    <h1 class="grid--span-4">Connect people and spaces</h1>
    <Card
      v-for="(card, index) in cards"
      class="card"
      :key="card.id"
      :class="`grid--span-${spanWidthForCard(index)}`"
      :backgroundImagePath="images[index % images.length]"
    >
      <template v-slot:header>
        <h2>{{ card.header }}</h2>
      </template>
      <template v-slot:description>
        <span>{{ card.description }}</span>
      </template>
    </Card>
    <!-- button always has its own place -->
    <div class="grid--span-2 flex center-horizontally">
      <Button label="More cards" @click="addMoreCards" />
    </div>
  </div>
</template>

<script>
import Button from '../components/button.vue';
import cloud from '../static/images/cloud.avif';
import connect from '../static/images/connect.avif';
import credentials from '../static/images/credentials.avif';
import intrusion from '../static/images/intrusion.avif';
import sharedWorkspaces from '../static/images/shared-workspaces.avif';
import unlocked from '../static/images/unlocked.avif';

export default {
  name: 'IndexPage',
  components: { Button },
  data() {
    return {
      cards: [],
      images: [cloud, connect, credentials, intrusion, sharedWorkspaces, unlocked]
    };
  },
  mounted() {
    this.addMoreCards();
  },
  methods: {
    /**
     * fetches more descriptions from API so that more images can be shown
     */
    addMoreCards() {
      this.$axios
        .get('quotes', {
          params: {
            limit: 5,
            skip: this.cards.length
          }
        })
        .then(({ data }) => {
          // Used api uses Author/quote - i want header/description
          const mappedValues = data.quotes.map((quote) => {
            return { header: quote.author, description: quote.quote, id: quote.id };
          });
          this.cards = [...this.cards, ...mappedValues];
        });
    },
    /**
     * returns a span width that is being used to display width of card in grid view.
     * @param {Number} index
     */
    spanWidthForCard(index) {
      return (index % 3) + 3;
    }
  }
};
</script>

<style lang="scss" scoped>
.card-views {
  display: grid;

  gap: 1rem;
  grid-template-columns: repeat(5, 1fr);
}

.grid--span-2 {
  grid-column: span 2;
}

.grid--span-3 {
  grid-column: span 3;
}

.grid--span-4 {
  grid-column: span 4;
}

.grid--span-5 {
  grid-column: span 5;
}

.grid--span-6 {
  grid-column: span 6;
}

@media only screen and (min-width: 800px) {
  .card-views {
    display: grid;

    gap: 1rem;
    grid-template-columns: repeat(10, 1fr);
  }
}

// Use grid for small laptop sizes and up
@media only screen and (min-width: 1200px) {
  .card-views {
    display: grid;

    gap: 1rem;
    grid-template-columns: repeat(12, 1fr);
  }
}
</style>