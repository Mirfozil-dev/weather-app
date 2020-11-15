<template>
  <div class="main">
    <label>
      <input
        :searchQuery="searchQuery"
        @change="$emit('type', $event.target.value)"
        type="text"
        class="search-bar"
        placeholder="Search..."
      >
    </label>
  </div>
</template>

<script>
export default {
  name: "SearchBox",
  model: {
    prop: 'searchQuery',
    event: 'type'
  },
  props: {
    searchQuery: {
      type: String,
      isRequired: true
    }
  }
}
</script>

<style scoped>

.search-bar {
  display: block;
  width: 100%;
  padding: 15px;

  color: #313131;
  font-size: 20px;
  appearance: none;
  outline: none;
  border: none;
  background: none;
  box-shadow: 0px 0px 8px rgba(255, 255, 255, 0.25);
  background: rgba(255, 255, 255, 0.5);
  border-radius: 0px 16px 0px 16px;
  transition: 0.4s;
}
.search-bar:focus{
  background: rgba(255, 255, 255, 0.75);
  box-shadow: 0px 0px 16px rgba(255, 255, 255, 0.25);
  border-radius: 16px 0px 16px 0px;
}

</style>