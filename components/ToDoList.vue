<template>
  <div class="to-do-container">
    <div class="create-container">
      <!-- <button @click="create">
        Add
      </button> -->

      <div id="video_box">
          
          <div id="lightOne" @click="toggleLight(1)">1</div>
          <div id="lightTwo" @click="toggleLight(2)">2</div>
          <div id="lightThree" @click="toggleLight(3)">3</div>
          <div id="video">
              <img style="-webkit-user-select: none;margin: auto;" 
                src="http://dawn.ii.uam.es/mjpg/video.mjpg" width="411" height="308">
          </div>
      </div>
    </div>
    <div class="to-do-list-container">
    </div>
  </div>

</template>

<script>
import ToDoListItem from "~/components/ToDoListItem.vue";
import axios from 'axios'

export default {
  components: {
    ToDoListItem
  },
  props: {
    todos: {
      type: Array,
      default() {
        return [];
      }
    }
  },
  data() {
    return {};
  },
  methods: {
    toggleLight(light) {

      axios.get(`https://us-central1-touchlightbr.cloudfunctions.net/app/api/v1/light/${light}/status`)
        .then((res) => {
          console.log("passo 1", res.data.status)
          let status = 0;
          if (res.data.status === "0") {
            status = 1
          }
          return status
        })
        .then((status) => {
          console.log("passo 2", status)
          axios.post(`https://us-central1-touchlightbr.cloudfunctions.net/app/api/v1/light/${light}/value/${status}`)
            .then((res) => {
              //console.log(res)
              return
            })
            .catch((err) => {
              console.log(err)
            })
        })
        .catch((err) => {
          console.log(err)
        })



    }
  },
  asyncData ({ light, value }) {

  }
};
</script>

<style lang="scss">
#video {
  margin-top: 2em;
}

#video_box{
    float:left;
}
#lightOne {
  border-style: dashed;
  border-width: thin;
  border-color: red;
  position:absolute;
  float:left;
  width:40px;
  min-height:40px;
  background-color: #0000ff61;
  z-index:300000;
  top: 308px;
  left: 100px;
}

#lightTwo {
  border-style: dashed;
  border-width: thin;
  border-color: red;
  position:absolute;
  float:left;
  width:40px;
  min-height:40px;
  background-color: #0000ff61;
  z-index:300000;
  top: 308px;
  left: 240px;
}

#lightThree {
  border-style: dashed;
  border-width: thin;
  border-color: red;
  position:absolute;
  float:left;
  width:40px;
  min-height:40px;
  background-color: #0000ff61;
  z-index:300000;
  top: 308px;
  left: 160px;
}
</style>
