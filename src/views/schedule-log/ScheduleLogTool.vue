<template>
  <div class="">
    <el-radio-group
      v-model="_status"
      size="small"
    >
      <el-radio-button label="total"
        >全部 {{ statusInfo.total }}</el-radio-button
      >
      <el-radio-button label="success"
        >成功 {{ statusInfo.success }}</el-radio-button
      >
      <el-radio-button label="error"
        >失败 {{ statusInfo.error }}</el-radio-button
      >
    </el-radio-group>

    <SelectScrapydServer
      class="ml-md"
      :value="_scrapydServerId"
      clearable
      @on-init="handleSelectScrapydServerInit"
      @change="handleScrapydServerChange"
    ></SelectScrapydServer>

    <ProjectSelect
      ref="ProjectSelect"
      v-if="scrapydServerId"
      :key="scrapydServerId"
      class="ml-sm"
      size="small"
      :scrapydServerId="scrapydServerId"
      :value.sync="_project"
      :clearable="true"
      :filterable="true"
      :allow-create="true"
    />

    <SpiderSearch
      class="ml-sm"
      size="small"
      :scrapydServerId="scrapydServerId"
      :project="_project"
      :value.sync="_spider"
      :clearable="true"
      @change="handleSpiderChange"
    />

    <ScheduleLogRemove
      class="ml-md"
      :status="status"
      :project="project"
      :spider="spider"
      :schedule_job_id="schedule_job_id"
      :scrapydServerId="scrapydServerId"
      @success="$emit('success')"
    />
    <!-- <ScheduleAdd @success="$emit('success')"/>
      
      <ScheduleState style="margin-left:20px" @success="$emit('success')"/>
      
      <ScheduleRemoveAllJob style="margin-left:20px" @success="$emit('success')"/> -->
    <AutoRefresh
      class="ml-sm"
      :frequency="5000"
      @refresh="$emit('success')"
    />
  </div>
</template>

<script>
// import ScheduleAdd from './ScheduleAdd.vue';
// import ScheduleState from './ScheduleState.vue';
// import ScheduleRemoveAllJob from './ScheduleRemoveAllJob.vue';
import ProjectSelect from '@/components/SelectProject.vue'
import SpiderSearch from '@/views/spider/SpiderSearch.vue'
import ScheduleLogRemove from './ScheduleLogRemove.vue'
import AutoRefresh from '@/views/commom/AutoRefresh.vue'
import SelectScrapydServer from '@/components/SelectScrapydServer.vue'
export default {
  name: '',

  props: {
    status: { type: String },
    project: { type: String, default: '' },
    spider: { type: String, default: '' },
    scrapydServerId: { type: String, default: '' },
    schedule_job_id: { type: String, default: '' },

    // {total、success、error}
    statusInfo: {
      type: Object,
      default: () => {
        return {}
      },
    },
  },

  components: {
    ProjectSelect,
    SpiderSearch,
    ScheduleLogRemove,
    AutoRefresh,
    SelectScrapydServer,

    // ScheduleAdd,
    // ScheduleState,
    // ScheduleRemoveAllJob
  },

  data() {
    return {
      hasScrapydServerIdInit: false,
    }
  },

  computed: {
    _status: {
      get() {
        return this.status
      },

      set(val) {
        this.$emit('update:status', val)
        this.$emit('status-change', val)
      },
    },

    _project: {
      get() {
        return this.project
      },

      set(val) {
        this.$emit('update:project', val)
        this.$emit('project-change', val)
      },
    },

    _spider: {
      get() {
        return this.spider
      },
      set(val) {
        this.$emit('update:spider', val)
      },
    },

    _scrapydServerId: {
      get() {
        return this.scrapydServerId
      },
      set(val) {
        this.$emit('update:scrapydServerId', val)
      },
    },
  },

  methods: {
    async getData() {},

    handleSpiderChange(val) {
      this.$emit('spider-change', val)
    },

    handleSelectScrapydServerInit(data) {
      // if (!this.scrapydServerId) {
      //   if (data.list && data.list.length > 0) {
      //     this.scrapydServerId = data.list[0].value
      //   }
      // }
      // this.hasScrapydServerIdInit = true
    },

    handleScrapydServerChange(val) {
      console.log(val);
      
      this._scrapydServerId = val
      this._project = null

      // this.$nextTick(() => {
      //   if (this.$refs.ProjectSelect) {
      //     this.$refs.ProjectSelect.resetData()
      //   }
      // })
    },
  },

  created() {
    this.getData()
  },
}
</script>

<style lang="scss" scoped></style>
