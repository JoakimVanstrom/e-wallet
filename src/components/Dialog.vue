<template>
  <div>
      <div class="dialog-background"></div>
         <div class="dialog">
          <dialog>
      <h2>Do you want to delete this card?</h2>

      <button
      class="delete"
      @click="del"
      >Yes</button>
      <button
      class="canceldelete"
      @click="cancelDel">No</button>
          </dialog>
     </div>
  </div>
</template>

<script>
export default {
methods:{
    cancelDel(){
        this.$emit('close')
    },
    del(){
        this.$emit('delete')
        this.$emit('close')
    }
}
}
</script>

<style scoped lang="scss">
.dialog-background {
  height: 100vh;
  width: 100%;
  background-color: black;
  opacity: 50%;
  position: fixed;
  top: 0;
  left: 0;
}


dialog {
  display: grid;
  place-items: center;
  width: 25rem;
  border-radius: 1rem;
  border: none;
  padding: 2rem;
}
h2 {
  text-align: center;
  margin-bottom: 1rem;
}


button {
  width: 50%;
  padding: 1rem;
  margin: 0.8rem;
  font-size: 1.5rem;
  border: 2px solid black;
  border-radius: 0.5rem;
  background-color: white;
  cursor: pointer;
}
.delete:hover{
    background-image: linear-gradient(to right, rgb(221, 101, 101), rgb(255, 255, 255));
}
.canceldelete:hover {
    background-color: black;
    color: white;
}

</style>