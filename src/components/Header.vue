<template>
  <section class="actions-section">
    <LanguageSwitcher class="language-switcher" style="display: none;" />
    <button class="print-button" @click="openPrintPage" style="margin-left:10px">
      <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-printer-fill" viewBox="0 0 16 16">
  <path d="M5 1a2 2 0 0 0-2 2v1h10V3a2 2 0 0 0-2-2H5zm6 8H5a1 1 0 0 0-1 1v3a1 1 0 0 0 1 1h6a1 1 0 0 0 1-1v-3a1 1 0 0 0-1-1z"/>
  <path d="M0 7a2 2 0 0 1 2-2h12a2 2 0 0 1 2 2v3a2 2 0 0 1-2 2h-1v-2a2 2 0 0 0-2-2H5a2 2 0 0 0-2 2v2H2a2 2 0 0 1-2-2V7zm2.5 1a.5.5 0 1 0 0-1 .5.5 0 0 0 0 1z"/>
</svg>
    </button>
    <a class="print-button" href="https://github.com/kwaibey">
      <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-github" viewBox="0 0 16 16">
  <path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.012 8.012 0 0 0 16 8c0-4.42-3.58-8-8-8z"/>
</svg>
    </a>
  </section>

  <div class="box">
    <div class="person-info">
      <Title class="person-info-name" :text="fullName" />
      <SubTitle class="person-info-position" :text="position" />
    </div>
    <div class="person-photo">
      <img class="person-photo-image" src="~@/assets/photo1.jpg" />
    </div>
  </div>
</template>

<script>
import LanguageSwitcher from "@/components/LanguageSwitcher.vue";
import Title from "@/components/Title.vue";
import SubTitle from "@/components/SubTitle.vue";

export default {
  Name: "Header",

  components: { LanguageSwitcher, Title, SubTitle },

  computed: {
    currentResumeData() {
      return this.$store.state.currentLanguage.data;
    },

    fullName() {
      const data = this.currentResumeData;
      const firstName = data.name["first"];
      const lastName = data.name["last"];
      return `${firstName} ${lastName}`;
    },

    position() {
      return this.currentResumeData.position;
    },
  },

  methods: {
    openPrintPage() {
      window.print();
    },
  },
};
</script>

<style scoped>
.actions-section {
  display: flex;
  position: absolute;
  align-items: center;
}

.language-switcher {
  padding: 10px;
}

.print-button {
  padding: 10px;
  margin: 10px 10px 10px -10px;
  width: auto;
  height: auto;
  border: none !important;
  cursor: pointer;
  background-color: transparent;
  -webkit-tap-highlight-color: transparent;
}

.print-button:hover {
  background-color: #FA8072	;
  transition: all 0.5s ease-out;
}

.person-info {
  display: flex;
  flex-direction: column;
}

.person-info-name {
  margin: 0;
  font-weight: 800;
  font-size: 1.8em;
}

.person-info-position {
  margin: 0px;
}

.box {
  padding-top: 40px !important;
  padding: 45px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 100%;
}

.person-photo {
}

.person-photo-image {
  height: 130px;
  width: 130px;
}

@media (max-width: 21cm) {
  .box {
    padding-top: 20px;
    flex-direction: column-reverse;
  }

  .person-info {
    align-items: center;
    justify-content: center;
  }

  .person-photo {
    padding-bottom: 20px;
  }



  .person-info-name,
  .person-info-position {
    text-align: center;
    padding-bottom: 12px;
  }

  .actions-section {
    width: 100%;
    justify-content: space-between;
  }
}

@media print {
  .actions-section {
    display: none;
  }

  .box {
    padding-top: 0px;
    flex-direction: column-reverse;
  }
}

svg{
  fill: #fff;
  width: 20px;
  height: 20px;
}

</style>
