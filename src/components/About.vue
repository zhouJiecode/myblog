<template>
  <el-row
    type="flex"
    justify="center"
    class="post-content"
  >
    <el-col
      :xs="{span: 24}"
      :sm="{span: 23}"
      :md="{span: 23}"
      :lg="{span: 23}"
      class="post-card"
      id="post-card"
    >
      <Content :domContent="domContent"></Content>
      <span id="footerPost"></span>
    </el-col>
  </el-row>
</template>
<script>
import { parseFrontmatter, markdown, defaultMD } from "@/plugins/markdown"
const md = `一家人工智能公司~:tada::tada:`

export default {
  name: "About",
  title: '自我介绍',
  props: {
    content: {
      type: Array,
      default: () => []
    }
  },
  data() {
    return {
      domContent: ''
    }
  },
  mounted() {
    const { content, data: { title, tags, date } } = parseFrontmatter(md)

    this.domContent = markdown.render(content)
  }
};
</script>
<style lang="stylus" scoped>
.post-content {
  margin-top: -34px;
  padding-bottom: 40px;
}

.post-card {
  padding: 35px;
  background: #fff;
  transition: 0.2s all ease-in-out;
  border-radius: 9px;
  box-shadow: 0 8px 10px -5px rgba(0, 0, 0, 0.2), 0 16px 24px 2px rgba(0, 0, 0, 0.14), 0 6px 30px 5px rgba(0, 0, 0, 0.12);
}

@media (max-width: 1190px) {
  .post-card {
    margin-right: 0;
    padding: 13px;
  }
}

@media (max-width: 768px) {
  .post-card {
    border-radius: 0;
    box-shadow: none;
  }
}
</style>