<template>
  <div class="">

    <ProjectSelect
      size="small"
      :value.sync="_project"
      :clearable="true"
      :filterable="true"
      :allow-create="true"
    />

    <SpiderSearch
      style="margin-left:20px"
      size="small"
      :project="_project"
      :value.sync="_spider"
      :clearable="true"
      @change="handleSpiderChange"
    />

    <StatsRemove
      style="margin-left:20px"
      :status="status"
      :project="project"
      :spider="spider"
      :schedule_job_id="schedule_job_id"
      @success="$emit('success')"
    />
    <!-- <ScheduleAdd @success="$emit('success')"/>
      
      <ScheduleState style="margin-left:20px" @success="$emit('success')"/>
      
      <ScheduleRemoveAllJob style="margin-left:20px" @success="$emit('success')"/> -->
    <AutoRefresh
      style="margin-left:20px;"
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
import SpiderSearch from '@/views/spider/SpiderSearch.vue';
import StatsRemove from './StatsRemove.vue';
import AutoRefresh from '@/views/commom/AutoRefresh.vue';

export default {
  name: '',

  props: {
    status: { type: String },
    project: { type: String, default: '' },
    spider: { type: String, default: '' },
    schedule_job_id: { type: String, default: '' },

    // {total、success、error}
    statusInfo: {
      type: Object,
      default: () => {
        return {};
      },
    },
  },

  components: {
    ProjectSelect,
    SpiderSearch,
    StatsRemove,
    AutoRefresh,

    // ScheduleAdd,
    // ScheduleState,
    // ScheduleRemoveAllJob
  },

  data() {
    return {};
  },

  computed: {
    _status: {
      get() {
        return this.status;
      },
      set(val) {
        this.$emit('update:status', val);
        this.$emit('status-change', val);
      },
    },

    _project: {
      get() {
        return this.project;
      },

      set(val) {
        this.$emit('update:project', val);
        this.$emit('project-change', val);
      },
    },
    _spider: {
      get() {
        return this.spider;
      },
      set(val) {
        this.$emit('update:spider', val);
      },
    },
  },

  methods: {
    async getData() {},

    handleSpiderChange(val) {
      this.$emit('spider-change', val);
    },
  },

  created() {
    this.getData();
  },
};
</script>

<style lang="scss" scoped>
</style>