<template>
  <Page class="page">
    <ActionBar class="action-bar">
      <Label class="action-bar-title" text="Repositórios" />
    </ActionBar>

    <ScrollView>
      <StackLayout v-for="(item, index) in repositors" :key="index">
        <Label :text="item.name" />
      </StackLayout>
    </ScrollView>
  </Page>
</template>

<script>
export default {
  data() {
    return {
      repositors: []
    };
  },
  mounted() {
    axios.get("https://api.github.com/users/JulioAugustoS/repos").then(res => {
      console.log(res.data);
      this.repositors = res.data;
    });
  }
};
</script>

<style scoped lang="scss">
// Start custom common variables
@import "../app-variables";
// End custom common variables

// Custom styles
.fa {
  color: $accent-dark;
}

.info {
  font-size: 20;
}
</style>
