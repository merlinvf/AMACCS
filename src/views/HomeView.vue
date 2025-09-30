<template>
  <div class="home">
    <FormularioComp/>
  </div>
</template>

<script>
// @ is an alias to /src
import FormularioComp from '@/components/FormularioComp.vue';


export default {
  name: 'HomeView',
  components: {
    FormularioComp
  }
}
</script>
