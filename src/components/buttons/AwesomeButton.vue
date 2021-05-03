<template>
  <button class="button">
      <slot name="text">{{text}}</slot>
  </button>
</template>


<script>
export default {
    name: "AwesomeButton",
    props: {
        text: {
        type: String,
        default: ''
        }
    }
};
</script>


<style lang="scss" scoped>
.button {
  cursor: pointer;
  background-color: transparent;
  color: #000;
  border: 3px solid #000;
  padding: .5px 1rem;
  font-size: 1rem;
  outline: none;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: .4rem;
  transition: background-color 0.1s ease-in, color 0.1s ease-in,
    border-color 0.1s ease-in;
  &:hover {
    background-color: #000;
    color: #fff;
    border-color: #000;
  }
}
</style>