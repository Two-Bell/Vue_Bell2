<template>
  <div>
    <div>Hellow World</div>
    <div>
      title ---> <input class="title" type="text" v-model="form.title" />
    </div>
    <div>
      contnet ---> <input class="content" type="text" v-model="form.content" />
    </div>
    <div>
      <button ref="button" class="button">추가</button>
      <button ref="button" class="button" @click="reset()">Reset</button>
    </div>
    <List :list="list" />
    <div>총 개수 {{ listLength }}</div>
  </div>
</template>

<script lang="ts">
import { Component, Vue, Watch } from "vue-property-decorator";
import { data } from "../util/dump";
import List from "./List.vue";

interface From {
  title: string;
  content: string;
}
interface Item {
  key: number;
  title: string;
  content: string;
}

@Component({
  components: {
    List,
  },
})
export default class HelloWorld extends Vue {
  list: Item[] = [{ key: 1, title: "1", content: "1" }];
  form: From = {
    title: "",
    content: "",
  };
  //count: number = 7;

  created() {
    this.list = data;
    console.log("created", this.list);
  }

  mounted() {
    console.log("mounted", this.list);
  }

  updated() {
    console.log("updated");
  }

  get listLength() {
    return this.list.length;
  }

  @Watch("form.title", { immediate: true, deep: true })
  public changeTitle(value: string) {
    console.log("change title", value);
  }

  @Watch("form.content", { immediate: true, deep: true })
  public chagneContent(value: string) {
    console.log("change content", value);
  }

  reset() {
    this.form.title = "";
    this.form.content = "";
  }

  // add() {
  //   this.count = this.count + 1;
  // }
}
</script>

<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
