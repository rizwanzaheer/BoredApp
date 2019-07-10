<script>
import appConfig from '@src/app.config'
import Layout from '@layouts/main'
import MyList from '@components/MyList'
import CurrentActivities from '@components/CurrentActivities'

export default {
  page: {
    title: 'Home',
    meta: [{ name: 'description', content: appConfig.description }],
  },
  components: { Layout, CurrentActivities, MyList },
  data() {
    return {
      currentTab: 'CurrentActivities',
      tabs: [
        { title: 'Activities', component: 'CurrentActivities' },
        { title: 'My List', component: 'MyList' },
      ],
    }
  },
  computed: {
    currentTabComponent: function() {
      return this.currentTab
    },
  },

  methods: {
    onTabChange(val) {
      return (this.currentTab = val)
    },
  },
}
</script>

<template>
  <Layout>
    <VContainer class="my-0">
      <VLayout row wrap align-center justify-center>
        <VFlex xs12 sm12 md10 lg6>
          <VCard flat class="elevation-1">
            <VTabs centered color="#1c6496" dark icons-and-text height="55">
              <VTabsSlider color="white" />
              <VTab
                v-for="tab in tabs"
                :key="tab.title"
                @click="onTabChange(tab.component)"
              >
                {{ tab.title }}
              </VTab>
            </VTabs>
            <keep-alive>
              <component :is="currentTabComponent" class="tab" />
            </keep-alive>
          </VCard>
        </VFlex>
      </VLayout>
    </VContainer>
  </Layout>
</template>
