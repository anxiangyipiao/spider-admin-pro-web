<template>
  <el-popconfirm
    title="确定删除？"
    @confirm="handleDelete"
  >

    <el-button
      slot="reference"
      v-bind="$attrs"
      size="mini"
      icon="el-icon-delete"
       type="text"
      class="color--danger"
    >删除</el-button>
  </el-popconfirm>

</template>

<script>
export default {
  name: '',

  props: {
    project: { type: String },
    scrapydServerId: { type: String | Number, default: null },
  },

  components: {},

  data() {
    return {};
  },

  computed: {},

  methods: {
    async handleDelete() {
      const res = await this.$Http.scrapydDeleteProject({
        project: this.project,
        scrapydServerId: this.scrapydServerId,
      });

      if (res.code == 0) {
        this.$message.success('删除成功');
        this.$emit('success');
      } else {
        this.$message.error(res.msg);
      }
    },
  },

  created() {},
};
</script>

<style lang="scss" scoped>
</style>