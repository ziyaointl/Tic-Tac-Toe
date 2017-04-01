<template>
  <div id="app">
    <section class="hero is-light is-fullheight">
      <div class="hero-body">
        <div class="centered">
          <div class="modal is-active">
            <div class="modal-background"></div>
            <div class="modal-content">
              <div class="card">
                <div class="card-content has-text-centered">
                  <h1 class="title">Please Select Your Symbol</h1>
                  <a class="button" @click="selectX">X</a>
                  <a class="button" @click="selectO">O</a>
                </div>
              </div>
            </div>
          </div>
          <div class="board">
            <table>
              <tr>
                <td></td>
                <td></td>
                <td></td>
              </tr>
              <tr>
                <td></td>
                <td></td>
                <td></td>
              </tr>
              <tr>
                <td></td>
                <td></td>
                <td></td>
              </tr>
            </table>
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
        isCircle: true
      }
    },
    methods: {
      closeModals() {
        let modals = document.getElementsByClassName('modal');
        for (let i = 0; i < modals.length; ++i) {
          modals[i].classList.remove("is-active");
        }
      },
      selectX() {
        this.closeModals();
        this.isCircle = false;
        let elements = document.getElementsByTagName("td");
        for (let i = 0; i < elements.length; ++i) {
          elements[i].innerHTML = "<p>" + i + "</p>";
        }
      },
      selectO() {
        this.closeModals();
      },
      reset() {
        isCircle = true;
      }
    }
  }
</script>

<style lang="scss">
  @import "css/styles.scss";
</style>