<template>
      <div @click="chooseImg" class="add-img">
        <a>
          <input id="imgUpload" type="file" @change="onUpload" accept="image/*" hidden>
          <svg class="ic-camera">
            <use xlink:href="./../assets/icons.svg#ic-camera"></use>
          </svg>
        </a>
      </div>
</template>

<script>
import firebase from 'firebase';

export default {
  name: 'ButtonUpload',
  data(){
    return {
      img: null,
      storageRef: firebase.storage()
    }
  },
  methods: {
    chooseImg(){
      document.getElementById("imgUpload").click();
    },
    onUpload(evt){
      this.img = evt.target.files[0];
      const storage = this.storageRef.ref(`${this.img.name}`).put(this.img);
      storage.on(`state_changed`, resp => {
        const completed = (resp.bytesTransferred/resp.totalBytes)*100;
        if(completed !== 0) {
          alert(`${completed}% complete uploaded`);
          window.location.reload();
        }
      }, err => {
        alert(err.message);
      });
    }
  }
}
</script>

<style>
.add-img {
  cursor: pointer;
  position: absolute;
  right: 0px;
  bottom: 50px;
  display: inline-block;
  width: 60px;
  height: 60px;
  background: #03A9F4;
  border-radius: 100%;
  text-align: center;
  line-height: 60px;
  margin-bottom: 20px;
  margin-right: 20px;
  -webkit-box-shadow: 0px 2px 20px rgba(0, 0, 0, 0.2);
  -moz-box-shadow: 0px 2px 20px rgba(0, 0, 0, 0.2);
  box-shadow: 0px 2px 20px rgba(0, 0, 0, 0.2);
}
.add-img svg {
  display: inline-block;
  vertical-align: middle;
} .ic-camera {
  width: 21px;
  height: 21px;
}
</style>