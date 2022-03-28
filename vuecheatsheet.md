# Vue Cheatsheet

## If-Else-Show

```html
<p v-if='InStock'>In Stock</p>
<p v-else>Out of Stock Stock</p>
<!-- <p v-else-if>Out of Stock Stock</p> -->

<p v-show='InStock'>In Stock</p>
```

InStock pulls from exposed data() on main.js (global)

When to use v-if and v-show? 

As a general rule for performance, v-if has higher toggle costs (whenever the conditional changes) and v-show has higher initial render costs. So if you need to toggle something frequently, use v-show

## v-for

```html
<ul>
  <li v-for="(detail, index) in details">{{ detail }}</li>
</ul>

<div v-for="variant in variants" :key="variant.id">{{ variant.color }}</div>
```

Including key is more performant, as is including index when no keys available. Note the :assignment, this is shorthand for attribute binding in Vue, aka v-bind

## Event Handling

```html
<button class="button" @click="addToCart">Add to Cart</button>
```

@assignment is shorthand for v-on, and can be used for any event assignment such as hover etc


## Class & Style Binding

```html
<div 
      v-for="variant in variants" 
      :key="variant.id" 
      @mouseover="updateImage(variant.image)" 
      class="color-circle"
      :style="{ backgroundColor: variant.color }">
      {{ variant.color }}
</div>
```

This in-line styling, but we could also expose a style object on data() and reference the styles in a cleaner manner:

```javascript
data() {
  return {
    styles: {
      color: 'red',
      fontSize: '14px',
    }
  }
}
```

```html
<div 
      v-for="variant in variants" 
      :key="variant.id" 
      @mouseover="updateImage(variant.image)" 
      class="color-circle"
      :style="styles">
      {{ variant.color }}
</div>
```

### Multiple Class Binding

```javascript
data() {
  return {
    activeClass = true,
  }
}
```

```html
<div
     class='color-circle'
     :class='{ active: activeClass}'>
</div>
```

If activeClass evaluates to true, then the new div class becomes color-circle activeClass; they are essentially combined

```html
<div :class='[activeClass ? activeClass : '' ]'>
</div>
```

We can also make use of inline ternarys 
