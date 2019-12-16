<template>
  <v-card>
      <v-flex xs12 sm10>
        <v-tree url="/item/category/list"
                :isEdit="isEdit"
                @handleAdd="handleAdd"
                @handleEdit="handleEdit"
                @handleDelete="handleDelete"
                @handleClick="handleClick"
        />
      </v-flex>
  </v-card>
</template>

<script>
  export default {
    name: "category",
    data() {
      return {
        isEdit:true
      }
    },
    methods: {
      handleAdd(node) {
        console.log("add .... ");
        console.log(node);
      },
      handleEdit(id, name) {
        const node = {
          id:id,
          name:name
        };
        this.$http({
          method:'put',
          url:'/item/category',
          data:this.$qs.stringify(node)
        }).then(() => {
          this.$message.info("修改成功！");
        }).catch(() => {
          this.$message.info("修改失败！");
        });
        console.log("edit... id: " + id + ", name: " + name);
      },
      handleDelete(id) {
        console.log("delete ... " + id);
      },
      handleClick(node) {
        console.log(node);
      }
    }
  };
</script>

<style scoped>

</style>
