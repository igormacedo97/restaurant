<template>
  <div class="item">
    <div class="container">
      <div class="item--tag" v-if="item.offer">Oferta</div>
      <img class="item--img" :src="imagePath" alt="" />
    </div>
    <div class="content">
      <h2 class="item--name">{{ item.name }}</h2>
      <p class="item--description">{{ item.description }}</p>
      <p class="item--price">{{ item.price | currency }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "Item",
  filters: {
    currency(value) {
      return `R$ ${value.toLocaleString("pt-br", {
        minimumFractionDigits: 2,
      })}`;
    },
  },
  props: {
    item: {},
  },
  computed: {
    selectedCategory() {
      return this.$store.state.selectedCategory;
    },
    imagePath() {
      return require(`../assets/images/${this.selectedCategory}/${this.item.id}.png`);
    },
  },
};
</script>

<style lang="less" scoped>
.item {
  width: 215.95px;
  height: 290px;
  border-radius: 8px;
  background: white;
  position: relative;
  margin: 20px;
  padding: 20px;

  display: flex;
  flex-direction: column;

  &--tag {
    position: absolute;
    background: @pink;
    border-radius: 8px;
    color: white;
    top: 15px;
    right: 15px;
    font-weight: 500;
    font-size: 12px; //0.75rem;
    padding: 2.5px 10px;
  }

  &--img {
    display: block;
    margin: auto;
    width: 100%;
  }

  &--name {
    font-weight: 800;
    font-size: 18px; //1.125rem;
    margin: 0;
  }

  &--description {
    color: @dark-grey;
    font-weight: 300;
    font-size: 12px; //0.75rem;
    margin: 0;
  }

  &--price {
    font-weight: 600;
    font-size: 18px; //1.125rem;
    color: @yellow;
    margin: 0;
  }

  .content {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    height: 100%;
    max-height: 100%;
    margin-top: 10px;
  }

  @media @tablets {
    width: 100%;
    height: fit-content;
    border: 1px solid @light-grey;
    display: flex;
    flex-direction: row;
    margin: 10px 0;
    padding: 10px 20px;

    &--tag {
      position: static;
      order: 1;
      width: fit-content;
    }

    .container {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      margin-right: 10px;
    }

    &--img {
      width: 86px;
      order: 0;
      margin: 0 0 10px 0;
    }

    &--price {
      text-align: right;
      margin: 5px 0 0 0;
    }

    .content {
      flex-grow: 1;
    }
  }
}
</style>
