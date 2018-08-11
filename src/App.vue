<template>
  <div class="container">
    <div class="row">
      <div class="col-sm-12">
        <Header @pageWasChanged="currentPage = $event"></Header>
        <div id="instructions" class="text-center italice">
          <div class="row">
            <div class="col-sm-6">
              <p>
                <em>&larr; Make changes in the edit area below</em>
              </p>
            </div>
            <div class="col-sm-6">
              <p>
                <em>And the will show on the card! &rarr;</em>
              </p>
            </div>
          </div>
        </div>
        <transition name="fade" mode="out-in" @enter="enter">
          <keep-alive>
            <component :is="currentPage"></component>
          </keep-alive>
        </transition>
        <Footer>
          <p class="text-center" slot="app-name">&copy; Creative Cards</p>
          <nav slot="footer-menu">
            <ul class="nav justify-content-center">
              <li class="nav-item">
                <a href="#" class="nav-link">Home</a>
              </li>
              <li class="nav-item">
                <a href="#" class="nav-link">About</a>
              </li>
              <li class="nav-item">
                <a href="#" class="nav-link">Contact</a>
              </li>
            </ul>
          </nav>
        </Footer>
      </div>
    </div>
  </div>
</template>

<script>
import FirebaseConfig from "./firebaseConfig";
import Header from "./components/Header";
import Footer from "./components/Footer";
import CardFront from "./components/card/CardFront";
import CardInsideLeft from "./components/card/CardInsideLeft";
import CardInsideRight from "./components/card/CardInsideRight";
import CardBack from "./components/card/CardBack";

export default {
  data() {
    return {
      currentPage: "cardFront"
    };
  },
  methods: {
    enter(el, done) {
      document.getElementById("instructions").style.display = "none";
      done();
    }
  },
  components: {
    Header,
    Footer,
    CardFront,
    CardInsideLeft,
    CardInsideRight,
    CardBack
  }
};
</script>

<style>
body {
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  color: #333;
}

.fade-enter,
.fade-leave-to {
  opacity: 0;
}
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}
</style>
