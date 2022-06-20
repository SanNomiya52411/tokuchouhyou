<template>
  <LikeHeaderVue></LikeHeaderVue>
  <LikeNumber @featureNumber="jobNumberChange"></LikeNumber>
  <SkillValueVue :JobSkill="JobSkill" :HobbySkill="HobbySkill"></SkillValueVue>
  <br>
  <p>当サービスは、「Chaosium Inc.」「株式会社KADOKAWA」「株式会社アークライト」が権利を有する『クトゥルフ神話TRPG サプリメント クトゥルフ2015』の二次創作物です。<br>
  (C)サンディ・ピーターセン／リン・ウィリス／中山てい子／坂本雅之／株式会社KADOKAWA<br>
  </p>
</template>

<script>
import LikeHeaderVue from './components/LikeHeader.vue'
import SkillValueVue from './components/SkillValue.vue'
import LikeNumber from './components/LikeNumber.vue'

export default {
  data(){
    return{
      JobSkill: 10,
      HobbySkill: 10
    }
  },
  emits: ['accepted'],
  components: {
    LikeHeaderVue,
    SkillValueVue,
    LikeNumber
  },
  methods: {
    jobNumberChange($event1,$event2){
      this.JobSkill = $event1
      this.HobbySkill = $event2
    }
  },
}
</script>