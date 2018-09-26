<template>
    <div class="game-area col-md-7 col-lg-8">
        <div class="table-border">
            <div class="table">
              <template v-for="(it, x) in 8">
                <div ref="cells" v-for="(it, y) in 8" :key="x + '-' + y" :class="'cell '+ cellColor(x, y)" :coord="'' + x + y" :row="x" :column="y">
                  <div class="stamp-parent">
                    
                    <!-- <stamp :id="this.stampId(player)" 
                           :player="player"
                           :isSelected="false" 
                           
                           ></stamp> -->

                  </div>
                </div>
              </template>
           </div>
       </div>
    </div>
</template>

<script>
let stampP1Counter = 1;
let stampP2Counter = 1;

import Vue from 'vue'
import Stamp from "./Stamp";

export default {
  data() {
    return {
      Stamp,
      selectedStamp: undefined
    };
  },
  mounted() {
    console.log("asdf");
    for (let x = 0; x < 8; x++) {
      for (let y = 0; y < 8; y++) {
        if (x == 1 || x == 2 || x == 5 || x == 6) {
          let player = x == 5 || x == 6 ? 1 : 2;

          let StampCompClass = Vue.extend(Stamp);

          let _stamp = new StampCompClass();

          _stamp.props = {
            id: this.stampId(player),
            player,
            isSelected: false
          };

          _stamp.$mount();

          //console.log(this.$refs.cells[x * 8 + y].children[0]);

          this.$refs.cells[x * 8 + y].children[0].appendChild(_stamp.$el);

          //console.log(this.$refs.cells[x * 8 + y]);
        }
      }
    }
  },
  methods: {
    cellColor(x, y) {
      return x % 2 == 0
        ? y % 2 == 0 ? "black" : "white"
        : y % 2 == 1 ? "black" : "white";
    },

    focusStamp(event) {
      // console.log(x + "  " + y);

      console.log(event.target);
    },

    stampId(player) {
      return player == 1
        ? "p1-stamp-" + stampP1Counter++
        : "p1-stamp-" + stampP2Counter++;
    }
  }
};
</script>

<style lang="scss">
.game-area {
  /* width: 63%; */
  border: 1px inset;
  float: left;
  height: 100%;
  padding: 15px;

  .table-border {
    width: 75%;
    border: 1px solid;
    margin: 0 auto;

    .table {
      margin: 0 !important;
      .cell {
        width: 12.5%;
        height: 12.5%;
        border: 1px solid;
        float: left;
        position: relative;

        .stamp-parent {
          position: relative;
          display: contents;
        }
      }

      .black {
        background: black;
      }
      .white {
        background: white;
      }
    }
  }
}

.table,
.cell::after {
  content: "";
  display: block;
  padding-bottom: 94%;
}
.p1stamp {
  position: absolute;
  width: 70%;
  height: 70%;
  left: 15%;
  top: 15%;
  border-radius: 70px;
  border-style: ridge;
  border-width: 6px;
  border-color: #989898;
  background: radial-gradient(
    ellipse at center,
    #e27676 9%,
    #615757 67%,
    #929292 90%
  ) !important;
}
.p2stamp {
  position: absolute;
  width: 70%;
  height: 70%;
  left: 15%;
  top: 15%;
  border-radius: 70px;
  border-style: ridge;
  border-width: 6px;
  border-color: #989898;
  background: radial-gradient(
    ellipse at center,
    #c38e8e 9%,
    #901d1d 68%,
    #929292 90%
  ) !important;
}
</style>
