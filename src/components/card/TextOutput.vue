<template>
    <div>
        <p>{{displayText}}</p>
    </div>
</template>

<script>
export default {
  props: ["displayText"]
};
</script>

<style scoped>
p {
  font-family: "Tangerine", cursive;
}
</style>
