<template>                  
    <span  
        :class="[ isSelected ? 'active':'', `p${this.props.player}stamp`]"
        :id="this.props.id"
        @click="$emit('clicked', $event)"
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
  data: function() {
    return {};
  },
  mounted() {
    // console.log(this.$parent);
    
  }
};
</script>

<style>
</style>
