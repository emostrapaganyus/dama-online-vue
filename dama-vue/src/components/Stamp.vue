<template>                  
    <span ref="stamp"  
        :class="[ this.props.isSelected ? 'active':'', `p${this.props.player}stamp`]"
        :id="this.props.id"
        @click="this._isSelected = !this._isSelected"
    ></span>
</template>

<script>
export default {
  props: {
    id: { type: Number },
    player: { type: Number },
    isSelected: {
      type: Boolean,
      default: false
    }
  },
  
  data() {
    return {
      _isSelected: this.isSelected
    };
  },
};
</script>

<style>
</style>
