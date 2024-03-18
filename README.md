# lzzs-tabs

element-ui 的 Tabs 组件

```sh
npm install lzzs-tabs
```

```js
import Lzzs-Tabs from "lzzs-tabs";

const tabs = ref([{
  name: "标签1"
},{
  name: "标签1"
}])
const tabIndex = ref(0)
```

## example

```vue
<Lzzs-Tabs v-model="tabIndex" :tabs="tabs"></Lzzs-Tabs>
```
