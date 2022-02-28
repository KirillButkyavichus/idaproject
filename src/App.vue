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
      <div>
        <div class="section__form">
          <div class="section__form-wrapper">
            <h3 class="section__form-title section__form-title_obligatory">
              Наименование товара
            </h3>
            <input
              v-model="form.name"
              class="input"
              type="text"
              placeholder="Введите наименование товара"
            />
          </div>
          <div class="section__form-wrapper">
            <h3 class="section__form-title">Описание товара</h3>
            <textarea
              v-model="form.description"
              class="textarea"
              placeholder="Введите описание товара"
            ></textarea>
          </div>
          <div class="section__form-wrapper">
            <h3 class="section__form-title section__form-title_obligatory">
              Ссылка на изображение товара
            </h3>
            <input
              v-model="form.link"
              class="input"
              type="text"
              placeholder="Введите ссылку"
            />
          </div>
          <div class="section__form-wrapper">
            <h3 class="section__form-title section__form-title_obligatory">
              Цена товара
            </h3>
            <input
              v-model="form.price"
              class="input"
              type="text"
              placeholder="Введите цену"
            />
          </div>
          <button @click="add" class="btn">Добавить товар</button>
        </div>
      </div>
      <div>
        <div class="section__grid">
          <div
            v-for="(product, idx) in products"
            :key="idx"
            class="section__grid-card"
          >
            <div
              @click="productToDelete(product)"
              class="section__grid-card__basket"
            ></div>
            <img :src="product.link" class="section__grid-card_img" alt="" />
            <div class="section__grid-card-info">
              <h3 class="section__grid-card-title">{{ product.name }}</h3>
              <span class="section__grid-card-text">{{
                product.description
              }}</span>
              <div class="section__grid-card-price">{{ product.price }}</div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",

  data() {
    return {
      form: {
        name: "",
        description: "",
        link: "",
        price: "",
      },
      products: [],
    };
  },

  methods: {
    add() {
      this.products.push(this.form);
      this.clearForm();
    },

    clearForm() {
      this.form = {
        name: "",
        description: "",
        link: "",
        price: "",
      };
    },

    productToDelete(productToRemove) {
      this.products = this.products.filter(
        (product) => product != productToRemove
      );
    },
  },
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
    cursor: pointer;
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
  grid-template-columns: minmax(0, 332px) minmax(0, 1fr);
  gap: 16px;
}

.section__form {
  background: #fffefb;
  box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04),
    0px 6px 10px rgba(0, 0, 0, 0.02);
  border-radius: 4px;
  padding: 29px 24px 19px;
  position: sticky;
  top: 0;
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
  outline: none;
  resize: none;
  min-width: 100%;
  padding: 10px 16px 0;
  font-size: 12px;
  line-height: 15px;
  min-height: 108px;
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
  outline: none;
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
  grid-template-columns: repeat(auto-fit, minmax(0, 332px));
  gap: 16px;
  &-card {
    background: #fffefb;
    box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04),
      0px 6px 10px rgba(0, 0, 0, 0.02);
    border-radius: 4px;
    cursor: pointer;
    position: relative;
    user-select: none;
    &:hover {
      .section__grid-card__basket {
        display: block;
      }
    }
    &_img {
      object-fit: cover;
      height: 200px;
      width: 100%;
    }
    &__basket {
      content: url("./assets/img/bascetForCard.svg");
      width: 32px;
      height: 32px;
      box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.1);
      border-radius: 10px;
      padding: 8px 9px;
      background-color: #ff8484;
      position: absolute;
      top: -8px;
      right: -8px;
      display: flex;
      align-items: center;
      justify-content: center;
      display: none;
    }
    &-info {
      padding: 16px 16px 24px;
    }
    &-title {
      font-weight: 600;
      font-size: 20px;
      line-height: 25px;
      margin-bottom: 16px;
      overflow: hidden;
      text-overflow: ellipsis;
      display: block;
    }
    &-text {
      font-size: 16px;
      line-height: 20px;
      overflow: hidden;
      text-overflow: ellipsis;
      display: block;
    }
    &-price {
      margin-top: 32px;
      font-weight: 600;
      font-size: 24px;
      line-height: 30px;
    }
  }
}
@media (max-width: 1439px) {
  .section__grid {
    grid-template-columns: repeat(auto-fit, minmax(332px, 0.5fr));
  }
}

@media (max-width: 1199px) {
  .section__grid {
    grid-template-columns: 1fr 1fr;
  }
}

@media (max-width: 991px) {
  .section__grid {
    grid-template-columns: 1fr;
  }
}

@media (max-width: 768px) {
  .section__product {
    grid-template-columns: 1fr;
  }
}

@media (max-width: 480px) {
  .section__info {
    flex-direction: column;
    align-items: flex-start;
    &-title {
      margin-bottom: 10px;
      font-size: 26px;
    }
  }
  .section__grid {
    grid-template-columns: minmax(0, 1fr);
  }
}
</style>
