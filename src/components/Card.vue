<template>
    <div class = "card">
        <a href="#" target = "_blank">
            <img src="" alt="Anime Image">
            <h3>Bleach</h3>
        </a>
    </div>
</template>


<style lang="scss" scoped>

  .card {
    flex: 1 1 33%;
    width: 33%;
    max-width: 33%;
    padding: 0px 8px;
    margin-bottom: 16px;

    img {
        width: 100%;
        height: 300px;
        object-fit: cover;
        border-radius: 16px;
        box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.15);
        transition: 0.4s;
    }
    h3 {
        padding: 16px;
        color: #313131;
        transition: 0.4s;
    }
    &:hover {
        img {
            transform: scale(1.05);
        }
        h3 {
            color: maroon;
        }
    }
  }
</style>