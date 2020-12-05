<template>
  <div class="home">
    <ListItem name="Menu List">
      <Item value="Chinh">
        <Item value="Chinh thứ 2">
          <Item value="Chinh thứ 4" :is-leaf="true"></Item>
        </Item>
        <Item value="Chinh thứ 3" :is-leaf="true"></Item>
      </Item>
    </ListItem>
  </div>
</template>

<script>
// @ is an alias to /src
import ListItem from "@/components/ListItem";
import Item from "@/components/Item";

export default {
  name: "Home",
  components: {
    ListItem,
    Item
  }
};
</script>
