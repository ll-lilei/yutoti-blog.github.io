# 最简易的响应式系统实现

```javascript

const data = { text: "hello world!" };

const bucket = new Set();
const obj = new Proxy(data, {
  get(target, key) {
    bucket.add(effect);
    return target[key];
  },
  set(target, key, newVal) {
    target[key] = newVal;
    bucket.forEach((fn) => fn());
    return true;
  },
});

// test
const effect = () => {
  console.log(obj.text)
}

effect()

setTimeout(() => {
  obj.text = "now what?"
})
```