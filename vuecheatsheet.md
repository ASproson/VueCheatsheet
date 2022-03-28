# Vue Cheatsheet

```javascript
<p v-if='InStock'>In Stock</p>
<p v-else>Out of Stock Stock</p>
// <p v-else-if>Out of Stock Stock</p>

<p v-show='InStock'>In Stock</p>
```

When to use v-if and v-show? 

As a general rule for performance, v-if has higher toggle costs (whenever the conditional changes) and v-show has higher initial render costs. So if you need to toggle something frequently, use v-show
