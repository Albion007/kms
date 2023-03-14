<template>
  <div class="hello">
<h1>Welcome to Homepage!</h1>
  <a v-on:click="logout" href="#/login">Logout</a>
  <br>
  <br>
      <VueUploadMultipleImage
        align="center"
        @upload-success="uploadImageSuccess"
        @edit-image="editImage"
        @mark-is-primary="markIsPrimary"
        @limit-exceeded="limitExceeded"
        @before-remove="beforeRemove"
        idUpload="myIdUpload"
        editUpload="myIdEdit"
        :max-image=20
        primary-text="Default"
        browse-text="Browse picture(s)"
        drag-text="Drag pictures"
        mark-is-primary-text="Set as default"
        popup-text="This image will be displayed as default"
        :multiple=true
        :show-edit=true
        :show-delete=true
        :show-add=true
      ></VueUploadMultipleImage>
  </div>
</template>

<script>
import VueUploadMultipleImage from 'vue-upload-multiple-image'
export default {
  name: 'HelloWorld',
    components: {
    VueUploadMultipleImage
  },
  methods: {
    logout () {
      localStorage.clear()
      this.$router.push({name: 'Login'})
    },
    uploadImageSuccess (formData, index, fileList) {
      console.log('data', formData, index, fileList)
      // Upload image api
      // axios.post('http://your-url-upload', formData).then(response => {
      //   console.log(response)
      // })
    },
    beforeRemove (index, removeCallBack) {
      console.log('index', index)
      var r = confirm('remove image')
      // eslint-disable-next-line eqeqeq
      if (r == true) {
        removeCallBack()
      }
    },
    editImage (formData, index, fileList) {
      console.log('edit data', formData, index, fileList)
    },
    markIsPrimary (index, fileList) {
      console.log('markIsPrimary data', index, fileList)
    },
    limitExceeded (amount) {
      console.log('limitExceeded data', amount)
    }
  }
}
</script>
