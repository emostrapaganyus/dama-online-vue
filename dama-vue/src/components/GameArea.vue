<template>
    <div class="game-area col-md-7 col-lg-8">
        <div class="table-border">
            <div class="table">
              <template v-for="(it, x) in 8">
                <div v-for="(it, y) in 8" :key="x + '-' + y" :class="'cell '+ cellColor(x, y)" :coord="'' + x + y" :row="x" :column="y">
                  <div class="stamp-parent">
                  
                    <span ref="stamp" v-if="x==5 || x==6 || x==1 || x==2" 
                          
                          :class="'stamp' + (x==5 || x==6 ? '1' : '2' )"
                          
                          :coord="'' + x + y"
                          v-on:click="focusStamp"
                          ></span>
                  </div>
                </div>
              </template>
           </div>
       </div>
    </div>
</template>

<script>
export default {
  data() {
    return {
    };
  },
  mounted(){
    this.counter1=0
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

    stampId(x, y) {
      console.log(this.p1StampCount++)

      return (x == 5 || x == 6)
        ? "p1-st-" + this.p1StampCount++
        : "p2-st-" + this.p2StampCount++;
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
.stamp2 {
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
.stamp1 {
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
