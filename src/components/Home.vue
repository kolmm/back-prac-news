<template>
  <div class="container">
    <div class="row">
      <div class="col-9 bgc" v-for="prob in articles">
        <div class="tags">
          <span>Криминал</span>
          <span>Детектив</span>
          <span>еще что-то</span>
        </div>
        <div class="main-text">
          <span class="created lead">
            {{ prob.created_at }}
          </span>
          <a class="author" href="#profile">
            <img class="avatar" src="../assets/review-person.png" alt="">
            <span class="name-author">kolmm</span>
          </a>
          <div class="container">
            <div class="row">
              <div class="col-10 no-padding">
                <div class="news h3">
                  {{ prob.name }}
                </div>
                <div class="desc lead">
                  {{ prob.description }}
                </div>
              </div>
              <img class="col-2 theme-img" src="../assets/theme.jpg" alt="">
            </div>
          </div>
        </div>
        <div class="soc">
          <div class="comment float-left">
            1 коментарий
          </div>
          <div class="like float-right">
            1 лайк
          </div>
        </div>
      </div>
      <!-- <div class="col-3 new-theme-main">
        <div class="new-theme lead">
          Новые темы
        </div>
        <div class="new-tagline">
          <img class="new-theme-img" src="../assets/user.png" alt="">
          <a href="" class="author">NAME</a>
          <div class="new-theme-desc lead">
            balblalbalbalblalblabllbalbl
            blablalbalbalblabla
            balbalblalbalblalbalbalblabla
          </div>
        </div>
      </div> -->
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data: function () {
    return {
      articles: []
    }
  },
  methods: {
    fetchArticles: function () {
      axios.get('https://still-island-19629.herokuapp.com/v1/news?origin=*').then((response) => {
        this.articles = response.data
      }, (error) => {
        console.log(error)
      })
    }
  },
  mounted: function () {
    this.fetchArticles()
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .bgc {
    background-color: #fff;
    margin-top: 20px;
    padding: 0;
  }

  .no-padding {
    padding: 0;
  }

  .tags {
    padding: 15px;
    border-bottom: 2px solid #f3effc;
  }

  .main-text {
    padding: 15px;
  }

  .created {
    margin-bottom: 10px;
  }

  .author {
    margin-left: 10px;
  }

  .avatar {
    height: 30px;
    width: 30px;
  }

  .theme-img {
    height: 100%;
    border-radius: 50%;
  }

  .soc {
    border-top: 2px solid #f3effc;
  }

  .like,.comment {
    padding: 15px;
  }

  .new-theme-main {
    background-color: #fff;
  }

  .new-theme-img {
    width: 30px;
    height: 30px;
    border-radius: 50%;
  }

</style>
