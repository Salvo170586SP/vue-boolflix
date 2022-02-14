<template>
  <div>
      <ul>
          <li>{{originalTitle}}</li>
          <li>{{title}}</li>
          <li>{{lenguage}}</li>
          <li>{{vote}}</li>
      </ul>
  </div>
</template>

<script>

export default {
    name: 'MovieCard',
    props:['originalTitles', 'title', 'lenguage', 'vote'],
}
</script>

<style>

</style>