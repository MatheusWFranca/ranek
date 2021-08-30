<template>
  <section>
    <h2>Crie a sua Conta</h2>
    <transition mode="out-in">
      <button v-if="!criar" class="btn" @click="criar = true">
        Criar Conta
      </button>
      <UsuarioForm v-else>
        <button class="btn btn-form" @click.prevent="criarUsuario">
          Criar Usuário
        </button>
      </UsuarioForm>
    </transition>
  </section>
</template>

<script>
import UsuarioForm from '@/components/UsuarioForm.vue';

export default {
  name: 'LoginCriar',
  data() {
    return {
      criar: false,
    };
  },
  components: {
    UsuarioForm,
  },
  methods: {
    async criarUsuario() {
      try {
        await this.$store.dispatch('criarUsuario', this.$store.state.usuario);
        await this.$store.dispatch(
          'getUsuario',
          this.$store.state.usuario.email
        );
        this.$router.push('/usuario');
      } catch (error) {
        console.log(error);
      }
    },
  },
};
</script>

<style scoped>
h2 {
  text-align: center;
  margin: 40px 0px 10px 0;
}

.btn {
  width: 100%;
  max-width: 200px;
  margin: 0px auto 0px auto;
}

.btn-form {
  max-width: 100%;
}
</style>