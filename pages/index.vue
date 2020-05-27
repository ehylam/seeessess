<template>
  <div class="container">
    <div
      class="content"
    >Hello, World Lorem ipsum dolor sit amet consectetur adipisicing elit. Delectus quae repellendus doloremque eos quod libero consectetur aperiam quo perferendis esse facere inventore ipsum.</div>
  </div>
</template>

<script>
export default {
  mounted() {
    var content = document.querySelector(".content");
    var value = content.textContent;
    // value = value.split("").map(item => item.trim());

    var result = value.replace(/(?![^<]*>)[^<]/g, c => {
      if (c !== " ") {
        return `<span class="mask">${c}</span>\n`;
      } else {
        return `<span>&nbsp;</span>\n`;
      }
    });
    content.innerHTML = result;
    // for (let i = 0; i < value.length; i++) {
    //   const element = value[i];
    //   if (element !== " ") {
    //     content.innerHTML += "<span>" + element + "</span>";
    //   }
    // }

    var mask = document.querySelectorAll(".mask");
    for (let i = 0; i < mask.length; i++) {
      // const element = mask[i];
      var toggleText = addActiveClass(i);
      setTimeout(() => (toggleText, i * 100));
    }

    function addActiveClass(i) {
      var item = mask[i];
      return function() {
        item.classList.toggle("active");
      };
    }
  }
};
</script>

<style lang="scss">
.container {
  height: 100vh;
  .content {
    display: flex;
    flex-wrap: wrap;
    span {
      transition: all 0.4s ease;
      // mask-position: 100% 100%;
      opacity: 0;
      font-size: 30px;
      letter-spacing: 0px;
      display: inline-block;
      // mask-size: 3400% 100%;

      &.active {
        opacity: 1;
      }
    }
  }
}
</style>
