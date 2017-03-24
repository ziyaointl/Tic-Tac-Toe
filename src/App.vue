<template>
  <div id="app">
    <section class="hero is-light is-fullheight">
      <div class="hero-body">
        <div class="container has-text-centered">
          <div class="square">
            <div class="columns is-gapless">
              <div class="column is-4">
                Column
              </div>
              <div class="column is-4">
                Column
              </div>
              <div class="column is-4">
                Column
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
  export default {
    name: 'app',
    data() {
      return {

      }
    }
  }
</script>

<style lang="scss">
  @import "css/bulma/utilities/_all.sass";
  @import "css/bulma/base/_all.sass";
  @import "css/bulma/layout/_all.sass";
  @import "css/bulma/elements/_all.sass";
  @import "css/bulma/grid/_all.sass";
  @import "css/bulma/components/_all.sass";
  @import "css/bulma/styles.sass";
</style>