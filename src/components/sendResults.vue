<template>
  <div class="sentResult" v-if="isMultiChoice">
    <div>
       <input type="radio" name="ans" value="A" v-model="student_ans"> A
    </div>
    <div>
       <input type="radio" name="ans" value="B"  v-model="student_ans"> B
    </div>
    <div>
       <input type="radio" name="ans" value="C"  v-model="student_ans"> C
    </div>
    <div>
       <input type="radio" name="ans" value="D"  v-model="student_ans"> D
    </div>
    <div>
       <button v-on:click="clickEventSent">Sent {{student_ans}}</button>
    </div>
  </div>
<!--  <div class="sentResult" v-if="isMultiChoice">-->
<!--    <div>-->
<!--       <button v-on:click="clickEventSent">Sent {{student_ans}}</button>-->
<!--    </div>-->
<!--  </div>-->
</template>

<script>
import { defineComponent } from '@vue/composition-api'
import { ref } from 'vue'

export default defineComponent({
  name: 'sentResult',
  props: {
    isMultiChoice: {
      type: Boolean
    },
    isLongResponse: {
      type: Boolean
    }
  },
  setup (props, {emit}) {
    const student_ans = ref('A')
    const clickEventSent = () => {
      console.log('click', student_ans.value)
      emit('sentResult', student_ans.value)
    }

    return {
      student_ans,
      clickEventSent
    }
  }
})
</script>

<style>
.sentResult{
  width: 100%;
  height: 20vh;
}
.sentResult div{
  width: 15%;
  float: left;
}
.sentResult div button{
  width: 50%;
  height: 5vh;
  margin-top: -2.5vh;
  border-radius: 10%;
}
</style>