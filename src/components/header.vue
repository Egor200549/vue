<script>
import { RouterLink } from 'vue-router';

export default {
  components: { RouterLink }
}
</script>

<template>
  <header>
    <div className="header">
        <RouterLink class="link" to="/">Main page</RouterLink>
        <!--<RouterLink class="link" to="/page2">Page 2</RouterLink>-->
    </div>
  </header>
</template>

<style >
.header {
    background: var(--mainColor);
    color: var(--link);
    display: flex;
    flex-wrap: wrap;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    padding: 16px 5% 16px 5%;
    height: 40px;
    top: 0;
    position: sticky;
}

.link {
    padding: 8px 8px 8px 32px;
    text-decoration: none;
    font-size: 20px;
    color: var(--link);
    display: block;
    transition: 0.3s;
}

.link:hover {
    color: var(--linkHover);
}
</style>
