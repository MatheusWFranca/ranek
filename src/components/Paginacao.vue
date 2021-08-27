<template>
  <ul v-if="paginasTotal > 1">
    <li v-for="pagina in paginasTotal" :key="pagina">
      <router-link :to="{ query: query(pagina) }">{{ pagina }}</router-link>
    </li>
  </ul>
</template>

<script>
export default {
  name: 'Paginacao',
  props: {
    produtosPorPagina: {
      type: Number,
      default: 1,
    },
    produtosTotal: {
      type: Number,
      default: 1,
    },
  },
  methods: {
    query(pagina) {
      return {
        ...this.$route.query,
        _page: pagina,
      };
    },
  },
  computed: {
    paginasTotal() {
      const total = this.produtosTotal / this.produtosPorPagina;
      if (total !== Infinity) {
        return Math.ceil(total);
      } else {
        return 0;
      }
    },
  },
};
</script>

<style scoped>
ul {
  grid-column: 1 / -1;
}
li {
  display: inline-block;
}

li a {
  padding: 2px 8px;
  border-radius: 4px;
  margin: 4px;
}

li a.router-link-exact-active,
li a:hover {
  color: #e80;
}
</style>