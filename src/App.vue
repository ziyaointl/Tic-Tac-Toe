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
                <td @click="cellClicked(0)"></td>
                <td @click="cellClicked(1)"></td>
                <td @click="cellClicked(2)"></td>
              </tr>
              <tr>
                <td @click="cellClicked(3)"></td>
                <td @click="cellClicked(4)"></td>
                <td @click="cellClicked(5)"></td>
              </tr>
              <tr>
                <td @click="cellClicked(6)"></td>
                <td @click="cellClicked(7)"></td>
                <td @click="cellClicked(8)"></td>
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
        isCircle: true,
        cells: document.getElementsByTagName("td"),
        states: []
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
      },
      selectO() {
        this.closeModals();
      },
      reset() {
        isCircle = true;
      },
      cellClicked(i) {
        if (this.cells[i].innerHTML === "") {
          if (this.isCircle) {
            this.cells[i].innerHTML = "<h2>O</p2>";
          } else {
            this.cells[i].innerHTML = "<h2>X</p2>";
          }
          checkWin();
          this.isCircle = !this.isCircle;
        }
      },
      checkWin() {

      },
      checkRow(index) {
        let startCell = index * 3;
        if (this.cells[startCell] === this.cells[startCell + 1] === this.cells[startCell + 2]) {
          if (this.cells[startCell] === "O") {
            return "O";
          }
          if (this.cells[startCell] === "X") {
            return "X";
          }
        }
        return "none";
      },
      checkColumn(index) {
        if (this.cells[index] === this.cells[index + 3] === this.cells[index + 6]) {
          if (this.cells[startCell] === "O") {
            return "O";
          }
          if (this.cells[startCell] === "X") {
            return "X";
          }
        }
        return "none";
      },
      checkDiagonal() {
        if (this.cells[0] === this.cells[4] === this.cells[8]) {
          if (this.cells[startCell] === "O") {
            return "O";
          }
          if (this.cells[startCell] === "X") {
            return "X";
          }
        }
        if (this.cells[2] === this.cells[4] === this.cells[6]) {
          if (this.cells[startCell] === "O") {
            return "O";
          }
          if (this.cells[startCell] === "X") {
            return "X";
          }
        }
        return "none";
      },
      getRow(index) {
        return index / 3;
      },
      getColumn(index) {
        return index % 3;
      }
    },
    mounted() {
      for (let i = 0; i < this.cells.length; ++i) {
        this.states.push("empty");
      }
    }
  }
</script>

<style lang="scss">
  @import "css/styles.scss";
</style>