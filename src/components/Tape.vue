<template>
  <div class="tape">
      <div class="box" v-for="index in 31" :key="index">
          <div class="boxtext">{{ arr[lpoint+index] }}</div>
          <div class="arrow" v-if="index == 31-15">
            <svg xmlns="http://www.w3.org/2000/svg" width='20px' height='20px' fill="#ff4b32FF" class="bi bi-arrow-up" viewBox="0 0 16 16">
              <path fill-rule="evenodd" d="M8 15a.5.5 0 0 0 .5-.5V2.707l3.146 3.147a.5.5 0 0 0 .708-.708l-4-4a.5.5 0 0 0-.708 0l-4 4a.5.5 0 1 0 .708.708L7.5 2.707V14.5a.5.5 0 0 0 .5.5z"/>
            </svg>
          </div>
      </div>
  </div>
</template>

<script>
import { ref, watch } from '@vue/runtime-core'

export default {
  props: ["arr", "lpoint"],
  setup(props, {}){
    const arr = ref(props.arr)
    const lpoint = ref(props.lpoint)

    watch(
      () => props.lpoint,
      () => {
        lpoint.value = props.lpoint
      }
    )

    return { arr, lpoint }
  }
}
</script>

<style>
.tape{
  margin-top: 5px;
  margin-bottom: 20px;
  display: flex;
  position: absolute;
  width: 100%;
  top: -10%;
  left: 50%;
  transform: translate(-50%, -50%);
  justify-content: space-around;
}
.box{
  border: 2px solid black;
  width: 25px;
  height: 25px;
  position: relative;

}
.boxtext{
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
.arrow{
  position: absolute;
  top: 110%;
  left: 50%;
  transform: translate(-50%, 0);
}
</style>