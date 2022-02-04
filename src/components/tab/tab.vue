<template>
  <div class="tab">
    <cube-tab-bar v-model="selectedLabel" :data="tabs" ref="tabBar"> </cube-tab-bar>
    <div class="slide-wrapper">
      <cube-slide
        ref="slide"
        :loop="false"
        :auto-play="false"
        :initial-index="index"
        :show-dots="false"
        @change="onChange"
      >
        <cube-slide-item v-for="(tab, index) in tabs" :key="index">
          <component
            ref="component"
            :is="tab.component"
            :data="tab.data"
          ></component>
        </cube-slide-item>
      </cube-slide>
    </div>
  </div>
</template>

<script>
export default {
  name: 'tab',
  props: {
    tabs: {
      type: Array,
      default() {
        return []
      }
    },
    initialIndex: {
      type: Number,
      default: 0
    }
  },
  data() {
    return {
      index: this.initialIndex
    }
  },
  computed: {
    selectedLabel: {
      get() {
        return this.tabs[this.index].label
      },
      set(newVal) {
        this.index = this.tabs.findIndex((value) => {
          return value.label === newVal
        })
      }
    }
  },
  methods: {
    onChange(current) {
      console.log('onChange:', current)
      this.index = current
      const component = this.$refs.component[current]
      component.fetch && component.fetch()
    }
  }
}
</script>
