<template>
    <div class="showcase" itemscope itemtype="https://schema.org/WebPage">
        <!-- for each client -->
        <div v-for="(client, index) in content" :key="index">
            <!-- for each showcase -->
            <section v-for="(showcase, index) in client" :key="index">
                <div v-for="(teaser, index, val) in showcase" v-if="teaser.homepage" :key="val">
                    <Teaser :content="teaser.teaser" :val="val"></teaser>
                </div>
            </section>
        </div>
    </div>
</template>
<script lang="ts">
import Vue from "vue";
import Teaser from "@/components/shared/Teaser.vue";
export default Vue.extend({
  name: "Showcase",
  components: {
    Teaser
  },
  props: {
    content: Object
  }
});
</script>
<style lang="sass">
@import '../../assets/css/variables'
.showcase
    &.full-width .container > * 
        width: 100%
    .container
        > *
            width: 50%
        .figure
            img
                margin-left: calc(-960px/2)
                @media screen and (max-width: $breakpoint-medium)
                  width: calc(100% + 60px)
                  margin-left: calc(-60px/2)
                  max-width: none
                  float: none
        &.reverse
            .figure
                margin-right: calc(-960px/2)
                margin-left: auto
        .figure, .content, &.reverse .figure, &.reverse .content
            @media screen and (max-width: $breakpoint-medium)
                margin-left: 0
                margin-right: 0
                width: 100%
</style>