<template>
  <div class="container">
    <div class="section__info">
      <div class="section__info-title">Добавление товара</div>
      <div class="section__info-select">
        <div class="section__info-select-text">По умолчанию</div>
        <img src="./assets/img/arrowDown.svg" alt="" />
      </div>
    </div>
    <div class="section__product">
      <div class="section__form">
        <div class="section__form-wrapper">
          <h3 class="section__form-title section__form-title_obligatory">
            Наименование товара
          </h3>
          <input
            class="input"
            type="text"
            placeholder="Введите наименование товара"
          />
        </div>
        <div class="section__form-wrapper">
          <h3 class="section__form-title">Описание товара</h3>
          <textarea
            class="textarea"
            cols="30"
            rows="7"
            placeholder="Введите описание товара"
          ></textarea>
        </div>
        <div class="section__form-wrapper">
          <h3 class="section__form-title section__form-title_obligatory">
            Ссылка на изображение товара
          </h3>
          <input class="input" type="text" placeholder="Введите ссылку" />
        </div>
        <div class="section__form-wrapper">
          <h3 class="section__form-title section__form-title_obligatory">
            Цена товара
          </h3>
          <input class="input" type="text" placeholder="Введите цену" />
        </div>
        <button class="btn">Добавить товар</button>
      </div>
      <div class="section__grid">
        <div class="section__grid-card">
          <img src="./assets/img/cardImg.jpg" alt="" />
          <div class="section__grid-card-info">
            <h3 class="section__grid-card-title">Наименование товара</h3>
            <span class="section__grid-card-text"
              >Довольно-таки интересное описание товара в несколько строк.
              Довольно-таки интересное описание товара в несколько строк</span
            >
            <div class="section__grid-card-price">10 000 руб.</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
};
</script>

<style lang="scss">
.section__info {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 16px;
  &-title {
    font-weight: 600;
    font-size: 28px;
    line-height: 35px;
  }
  &-select {
    background: #fffefb;
    box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
    border-radius: 4px;
    padding: 10px 16px;
    display: inline-flex;
    align-items: baseline;
    &-text {
      color: #b4b4b4;
      font-size: 12px;
      line-height: 15px;
      margin-right: 5px;
    }
  }
}

.section__product {
  display: grid;
  grid-template-columns: 1fr 3fr;
  gap: 16px;
}

.section__form {
  background: #fffefb;
  box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04),
    0px 6px 10px rgba(0, 0, 0, 0.02);
  border-radius: 4px;
  padding: 29px 24px 19px;
  &-wrapper {
    padding-bottom: 16px;
    &:last-of-type {
      margin-bottom: 8px;
    }
  }
  &-title {
    color: #49485e;
    font-size: 10px;
    line-height: 13px;
    letter-spacing: -0.02em;
    margin-bottom: 4px;
    width: fit-content;
    &_obligatory {
      position: relative;
      &::before {
        content: "";
        width: 4px;
        height: 4px;
        border-radius: 4px;
        background-color: #ff8484;
        position: absolute;
        top: 0;
        left: 100%;
      }
    }
  }
}

.textarea {
  background-color: #fffefb;
  box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
  border-radius: 4px;
  border: none;
  min-width: 100%;
  padding: 10px 16px 0;
  font-size: 12px;
  line-height: 15px;
  &::placeholder {
    color: #b4b4b4;
  }
}

.input {
  background-color: #fffefb;
  box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
  border-radius: 4px;
  border: none;
  min-width: 100%;
  padding: 10px 16px;
  font-size: 12px;
  line-height: 15px;
  &::placeholder {
    color: #b4b4b4;
  }
}

.btn {
  border: none;
  padding: 10px 0px;
  border-radius: 10px;
  font-weight: 600;
  font-size: 12px;
  line-height: 15px;
  text-align: center;
  letter-spacing: -0.02em;
  min-width: 100%;
  color: #ffffff;
  background-color: #7bae73;
  box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.1);
  cursor: pointer;
}

.section__grid {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  gap: 16px;
  &-card {
    background: #fffefb;
    box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04),
      0px 6px 10px rgba(0, 0, 0, 0.02);
    border-radius: 4px;
    cursor: pointer;
    position: relative;
    &:hover {
      &::before {
        content: url("./assets/img/bascetForCard.svg");
        width: 32px;
        height: 32px;
        box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.1);
        border-radius: 10px;
        background-color: #ff8484;
        position: absolute;
        top: -8px;
        right: -8px;
        display: flex;
        align-items: center;
        justify-content: center;
      }
    }
    &-info {
      padding: 16px 16px 24px;
    }
    &-title {
      font-weight: 600;
      font-size: 20px;
      line-height: 25px;
      margin-bottom: 16px;
    }
    &-text {
      font-size: 16px;
      line-height: 20px;
    }
    &-price {
      margin-top: 32px;
      font-weight: 600;
      font-size: 24px;
      line-height: 30px;
    }
  }
}
</style>
