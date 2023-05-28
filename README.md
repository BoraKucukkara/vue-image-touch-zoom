# vue-image-touch-zoom

image zoom application with touch interactions

basically tracking the distance between two fingers and use that information to scale image

demo: https://vue-image-zoom.netlify.app (only touch devices)

External props passed to the component:

```
<template>
  <img-touch-zoom v-for="image in images" :img="image" :key="image.src"/>
</template>

data() {
    return {
      images: [
        {src:"001.jpg",alt:"Lorem ipsum dolor"},
        {src:"002.jpg",alt:"Consectetur adipiscing elit, sed do eiusmod tempor"},
        {src:"003.jpg",alt:"Incididunt ut labore et dolore magna aliqua."},
        {src:"004.jpg",alt:"Ut enim ad minim veniam."},
        {src:"005.jpg",alt:"Excepteur sint occaecat cupidatat"},
      ]
    }
  }
```

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
