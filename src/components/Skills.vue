<template>
  <Title :text="skillsLabel" />
  <h2>Programming Languages</h2>
  <SubTitle :text="professionalLabel" />

  <div class="skill-line" v-for="(skill, index) in skills" :key="index">
    <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-circle-fill" viewBox="0 0 16 16">
  <circle cx="8" cy="8" r="8"/>
</svg>
    <Paragraph class="contact" :text="skill" />
  </div>
  <h2>Libraries and Frameworks</h2>
   <div class="skill-line">
    <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-circle-fill" viewBox="0 0 16 16">
  <circle cx="8" cy="8" r="8"/>
</svg>
    <p class="contact">Node.js</p>
  </div>
  <div class="skill-line">
    <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-circle-fill" viewBox="0 0 16 16">
  <circle cx="8" cy="8" r="8"/>
</svg>
    <p class="contact">Vue.js</p>
  </div>
  <div class="skill-line">
    <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-circle-fill" viewBox="0 0 16 16">
  <circle cx="8" cy="8" r="8"/>
</svg>
    <p class="contact">React.js</p>
  </div>
  <div class="skill-line">
    <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-circle-fill" viewBox="0 0 16 16">
  <circle cx="8" cy="8" r="8"/>
</svg>
    <p class="contact">MongoDB</p>
  </div>
  <div class="skill-line">
    <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-circle-fill" viewBox="0 0 16 16">
  <circle cx="8" cy="8" r="8"/>
</svg>
    <p class="contact">Express.js</p>
  </div>
  
</template>

<script>
import Title from "@/components/Title.vue";
import SubTitle from "@/components/SubTitle.vue";
import Paragraph from "@/components/Paragraph.vue";

export default {
  Name: "Skills",

  components: { Title, SubTitle, Paragraph },

  computed: {
    currentLanguage() {
      return this.$store.state.currentLanguage;
    },

    resumeLabels() {
      return this.currentLanguage.resumeLabels;
    },

    skillsLabel() {
      return this.resumeLabels.skills;
    },

    // professionalLabel() {
    //   return this.resumeLabels.professional;
    // },

    skills() {
      return this.currentLanguage.data.skills;
    }
  }
};
</script>

<style scoped>
.circle {
  /* width: 8px;
  margin-left: 8px; */
}

.material-icons {
  display: inline-flex;
  align-items: center;
}

.skill-line {
  display: flex;
}

.contact {
  padding-left: calc(1em + 8px);
  margin: 0.25em;
}

svg{
  fill: #fff;
  width: 8px;
  height: 8px;
  margin-left: 8px;
  margin-top: 10px;
}

h2{
  color: #FA8072;
    margin: 0 0 1em 0;
    line-height: 22px;
    letter-spacing: 1px;
    font-size: 14px;
    font-weight: 800;
    text-transform: uppercase;
}

p{
      line-height: 22px;
    margin: 0;
    font-size: 15px;
    color: #fff;
}
</style>
