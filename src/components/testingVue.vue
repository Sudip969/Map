<template>
  <div>
    <h1>My Object List</h1>
    <ul>
      <li v-for="(urlObj, index) in myObject.urlObj" :key="index">
        <span>{{ urlObj.urlname }}</span>
        <input v-model="urlObj.url"    />
      </li>
    </ul>
    <h1>Copied Object</h1>
    <ul>
      <li v-for="(urlObj, index) in copiedObject.urlObj" :key="index">
        <span>{{ urlObj.urlname }}</span>
        <input v-model="urlObj.url" />
      </li>
    </ul>
    <button @click="copyObject" :disabled="!isAllUrlsChanged">
      Copy Object
    </button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      myObject: {
        name: 'Example',
        urlObj: [
          { urlname: 'Google', url: 'https://www.google.com' },
          { urlname: 'Facebook', url: 'https://www.facebook.com' },
          { urlname: 'Twitter', url: 'https://www.twitter.com' }
        ]
      },
      copiedObject: {
        name: 'Copied Object',
        urlObj: [
          { urlname: 'Google', url: 'https://www.google.com' },
          { urlname: 'Facebook', url: 'https://www.facebook.com' },
          { urlname: 'Twitter', url: 'https://www.twitter.com' }
        ]
      }
    };
  },
  computed: {
    isAllUrlsChanged() {
      return this.myObject.urlObj.every(
        (urlObj, index) => urlObj.url !== this.copiedObject.urlObj[index].url
      );
    }
  },
  methods: {

    copyObject() {
      this.copiedObject = JSON.parse(JSON.stringify(this.myObject));
    }
  }
};
</script>

<style scoped>
ul {
  list-style: none;
}
li {
  display: flex;
  align-items: center;
  margin-bottom: 10px;
}
input {
  margin-left: 10px;
}
button {
  margin-left: 10px;
}
</style>
