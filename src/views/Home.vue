<template>
  <section>
    <h1>👍 Compre ou Venda 👎</h1>
    <ProdutosBuscar />
    <ProdutosLista />
  </section>
</template>

<script>
import ProdutosBuscar from '@/components/ProdutosBuscar.vue';
import ProdutosLista from '@/components/ProdutosLista.vue';

export default {
  components: {
    ProdutosBuscar,
    ProdutosLista,
  },
};
</script>

<style scoped>
h1 {
  color: #87f;
  font-size: 2rem;
  font-family: 'Nunito', sans-serif;
  margin-top: 40px;
  text-align: center;
}
</style>
