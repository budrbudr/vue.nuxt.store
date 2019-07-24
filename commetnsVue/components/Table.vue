<template>

    <div class="container">
      <b-table bordered striped  :fields="fields" :items="news" >

      </b-table>
    </div>
</template>

<script>

  export default {
    data() {
      return {
        fields: [
          {
            key: 'title',
            sortable: true
          },
          {
            key: 'content',
            sortable: true
          },
          {
            key: 'comments',
            sortable: true
          },
          {
            key: 'Actions',
            sortable: true
          },
        ],
      }
    },

        async asyncData({$axios}) {
          let news = [];
          try {
            news = await $axios.$get('/comments.json');
          } catch (e) {
            console.warn(e)
          }
          return {
            news
          }
        }


  }
</script>

<style scoped>

</style>
