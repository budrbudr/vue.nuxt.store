<template>
<div class="container">
  <h3 class="vue-title ">Articles</h3>



  <div class="container">
    <b-table bordered striped  :fields="fields" :items="news" >

    </b-table>
  </div>
</div>
</template>

<script>


import Table from "../components/Table";
export default {
  components: {
    Table
  },
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
       news.map((data, index) => {
        news[index].quantityOfComments = data.comments.length;
      })
    } catch (e) {
      console.warn(e)
    }
    return {
      news
    }
  }
}
methods: {

}
</script>

