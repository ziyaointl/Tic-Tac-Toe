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
            this.states[i] = "O";
          } else {
            this.cells[i].innerHTML = "<h2>X</p2>";
            this.states[i] = "X";
          }
          console.log(this.compareCells(2, 4, 6));
          this.checkWin(i);
          this.isCircle = !this.isCircle;
        }
      },
      checkWin(index) {
        if (this.checkColumn(this.getColumn(index)) === "O" || this.checkRow(this.getRow(index)) === "O" || this.checkDiagonal() ===
          "O") {
          alert("O");
        } else if (this.checkColumn(this.getColumn(index)) === "O" || this.checkRow(this.getRow(index)) === "O" || this
          .checkDiagonal() === "O") {
          alert("X");
        }
      },
      checkRow(index) {
        let startCell = index * 3;
        return this.compareCells(startCell, startCell + 1, startCell + 2);
      },
      checkColumn(index) {
        return this.compareCells(index, index + 3, index + 6);
      },
      checkDiagonal() {
        let result = this.compareCells(0, 4, 8);
        if (result !== "none") {
          return result;
        }
        result = this.compareCells(2, 4, 6);
        return result;
      },
      getRow(index) {
        return Math.floor(index / 3);
      },
      getColumn(index) {
        return index % 3;
      },
      compareCells(index1, index2, index3) {
        if (this.states[index1] === this.states[index2]) {
          if (this.states[index2] === this.states[index3]) {
            if (this.states[index1] === "O") {
              return "O";
            }
            if (this.states[index1] === "X") {
              return "X";
            }
          }
        }
        return "none";
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