<template>
  <!-- 首页 -->
  <div
    v-show="
      !sharedState.RedNote.activePost &&
      sharedState.phone.activeApp === 'RedNote' &&
      sharedState.RedNote.activeTab === 'home'
    "
    class="rednote-homepage"
  >
    <div class="rednote-homepage-top">
      <div
        class="user_avatar"
        style="
          width: 35px;
          height: 35px;
          border-radius: 50%;
          background-size: cover;
          background-position: top center;
          background-repeat: no-repeat;
          background-color: black;
          aspect-ratio: 1;
          min-width: 35px;
        "
        @click="sharedState.phone.activeApp = 'QQ'"
      ></div>
      <div style="display: flex; margin-bottom: -5px; flex: 1; justify-content: space-evenly">
        <div style="font-size: 16px; color: rgb(100, 100, 100) !important; white-space: nowrap !important">关注</div>
        <div
          style="
            display: flex;
            flex-direction: column;
            gap: 5px;
            align-items: center;
            color: black !important;
            white-space: nowrap !important;
          "
        >
          <div>发现</div>
          <div style="width: 3rem; height: 4px; background-color: #e73f4c; border-radius: 10px"></div>
        </div>
        <div style="font-size: 16px; color: rgb(100, 100, 100) !important; white-space: nowrap !important">同城</div>
      </div>

      <div
        style="
          width: 35px;
          height: 35px;
          border-radius: 50%;
          aspect-ratio: 1;
          min-width: 35px;
          display: flex;
          align-items: center;
          justify-content: center;
        "
      >
        <svg viewBox="0 0 1024 1024" width="20" height="20" style="margin-top: -5px">
          <path
            d="M704.448 648.768L956.48 900.736l-55.744 55.68L648.64 704.384a393.856 393.856 0 1 1 55.808-55.68z m-82.24-26.56a315.072 315.072 0 1 0-437.76-453.248 315.072 315.072 0 0 0 437.76 453.248z"
            p-id="16026"
            fill="#303030"
          ></path>
        </svg>
      </div>
    </div>
    <div class="rednote-homepage-content">
      <div style="display: flex; flex-direction: column; width: 100%">
        <div
          v-for="value of sharedState.RedNote.post.filter((_, index) => index % 2 === 0)"
          class="rednote-homepage-post"
          @click="
            sharedState.RedNote.activePost = value.id;
            console.log(value.id);
          "
        >
          <div
            class="rednote-homepage-post-img"
            :style="`background-color:${value.imgColor};color:${value.textColor};`"
          >
            {{ value.img }}
          </div>
          <div class="rednote-homepage-post-info">
            <div class="rednote-homepage-post-title">{{ value.title }}</div>
            <div class="rednote-homepage-post-author">
              <div
                :style="`background-image: url('${value.head}');
                  width: 25px;
                  height: 25px;
                  border-radius: 50%;
                  background-size: cover;
                  background-position: top center;
                  background-repeat: no-repeat;
                  background-color: black;
                  aspect-ratio: 1;
                  min-width: 25px;`"
              ></div>
              <div
                style="
                  color: rgb(100, 100, 100);
                  font-size: 14px;
                  flex: 1;
                  text-overflow: ellipsis;
                  overflow: hidden;
                  white-space: nowrap;
                "
              >
                {{ value.sender }}
              </div>
              <svg viewBox="0 0 1024 1024" width="20" height="20">
                <path
                  d="M171.712 571.648l0.352 0.32 287.904 252.8a64 64 0 0 0 82.912 1.344l296.832-244.544a215.584 215.584 0 1 0-301.824-300.576L512 316.672l-25.888-35.616a215.584 215.584 0 1 0-314.4 290.624zM32 407.584a279.584 279.584 0 0 1 480-194.944 279.584 279.584 0 0 1 480 194.944 278.144 278.144 0 0 1-113.024 224.512l-295.36 243.392a128 128 0 0 1-165.888-2.592L129.984 620.16A278.976 278.976 0 0 1 32 407.584z"
                  fill="#646464"
                  p-id="4875"
                ></path>
              </svg>
              <div style="color: #646464; font-size: 12px">{{ value.like }}</div>
            </div>
          </div>
        </div>
      </div>
      <div style="display: flex; flex-direction: column; width: 100%">
        <div
          v-for="value of sharedState.RedNote.post.filter((_, index) => index % 2 === 1)"
          class="rednote-homepage-post"
          @click="
            sharedState.RedNote.activePost = value.id;
            console.log(value.id);
          "
        >
          <div class="rednote-homepage-post-img" :style="`background-color:${value.imgColor}`">{{ value.img }}</div>
          <div class="rednote-homepage-post-info">
            <div class="rednote-homepage-post-title">{{ value.title }}</div>
            <div class="rednote-homepage-post-author">
              <div
                :style="`background-image: url('${value.head}');
                  width: 25px;
                  height: 25px;
                  border-radius: 50%;
                  background-size: cover;
                  background-position: top center;
                  background-repeat: no-repeat;
                  background-color: black;
                  aspect-ratio: 1;
                  min-width: 25px;`"
              ></div>
              <div
                style="
                  color: rgb(100, 100, 100);
                  font-size: 14px;
                  flex: 1;
                  text-overflow: ellipsis;
                  overflow: hidden;
                  white-space: nowrap;
                "
              >
                {{ value.sender }}
              </div>
              <svg viewBox="0 0 1024 1024" width="20" height="20">
                <path
                  d="M171.712 571.648l0.352 0.32 287.904 252.8a64 64 0 0 0 82.912 1.344l296.832-244.544a215.584 215.584 0 1 0-301.824-300.576L512 316.672l-25.888-35.616a215.584 215.584 0 1 0-314.4 290.624zM32 407.584a279.584 279.584 0 0 1 480-194.944 279.584 279.584 0 0 1 480 194.944 278.144 278.144 0 0 1-113.024 224.512l-295.36 243.392a128 128 0 0 1-165.888-2.592L129.984 620.16A278.976 278.976 0 0 1 32 407.584z"
                  fill="#646464"
                  p-id="4875"
                ></path>
              </svg>
              <div style="color: #646464; font-size: 12px">{{ value.like }}</div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="rednote-homepage-bottom">
      <div
        class="rednote-homepage-bottom-button"
        style="color: black; font-size: 18px"
        @click="sharedState.RedNote.activeTab = 'home'"
      >
        首页
      </div>
      <div class="rednote-homepage-bottom-button" @click="sharedState.RedNote.activeTab = 'market'">市集</div>
      <div
        style="width: 3rem; height: 40px; background-color: #ea3e4a; border-radius: 9px; position: relative"
        @click="sharedState.phone.activeApp = 'QQ'"
      >
        <div
          style="
            width: 50%;
            background-color: white;
            height: 4px;
            position: absolute;
            border-radius: 5px;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
          "
        ></div>
        <div
          style="
            width: 50%;
            background-color: white;
            height: 4px;
            position: absolute;
            border-radius: 5px;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%) rotate(90deg);
          "
        ></div>
      </div>
      <div class="rednote-homepage-bottom-button">消息</div>
      <div class="rednote-homepage-bottom-button">我的</div>
    </div>
  </div>

  <!-- 帖子详情页面 -->
  <transition name="slide-fade">
    <div
      v-show="sharedState.RedNote.activePost && sharedState.phone.activeApp === 'RedNote'"
      class="rednote-postpage-list"
      style="width: 100%; height: 100%"
    >
      <post v-for="value of sharedState.RedNote.post" :post-content="value"></post>
    </div>
  </transition>

  <!-- 市集页面 -->
  <div
    v-show="sharedState.phone.activeApp === 'RedNote' && sharedState.RedNote.activeTab === 'market'"
    class="rednote-market"
  >
    <div class="rednote-market-top">
      <div
        class="user_avatar"
        style="
          width: 35px;
          height: 35px;
          border-radius: 50%;
          background-size: cover;
          background-position: top center;
          background-repeat: no-repeat;
          background-color: black;
          aspect-ratio: 1;
          min-width: 35px;
        "
        @click="sharedState.phone.activeApp = 'QQ'"
      ></div>
      <div class="market-search">
        <div class="search-box">
          <svg viewBox="0 0 1024 1024" width="16" height="16">
            <path
              d="M704.448 648.768L956.48 900.736l-55.744 55.68L648.64 704.384a393.856 393.856 0 1 1 55.808-55.68z m-82.24-26.56a315.072 315.072 0 1 0-437.76-453.248 315.072 315.072 0 0 0 437.76 453.248z"
              p-id="16026"
              fill="#646464"
            ></path>
          </svg>
          <input type="text" placeholder="搜索商品" />
        </div>
      </div>
      <div class="market-cart" @click="sharedState.RedNote.activeTab = 'cart'">
        <svg viewBox="0 0 1024 1024" width="20" height="20">
          <path
            d="M922.9 701.9H327.4l29.9-60.9 496.8-.9c16.8 0 31.2-12 34.2-28.6l68.8-385.1c1.8-10.1-.9-20.3-7.5-28.4-6.6-8.1-16.5-12.9-26.7-12.9l-584.8-.9-12.6-61.2c-3.6-17.6-19.9-30.2-37.9-30.2L89.1 96.8c-19.9 0-36 16.1-36 36s16.1 36 36 36h128.9l155.3 756.7c3.6 17.6 19.9 30.2 37.9 30.2H901c19.9 0 36-16.1 36-36s-16.1-36.1-36-36.1zM384.8 508.9v-.1l-23-107.8h515.4l-56.6 316.8-436.8.9z"
            fill="#646464"
          ></path>
          <path d="M377.9 872.9m-48 0a48 48 0 1 0 96 0 48 48 0 1 0-96 0Z" fill="#646464"></path>
          <path d="M765.9 872.9m-48 0a48 48 0 1 0 96 0 48 48 0 1 0-96 0Z" fill="#646464"></path>
        </svg>
      </div>
    </div>

    <div class="market-categories">
      <div
        v-for="category in marketCategories"
        :key="category.id"
        class="category-item"
        :class="{ active: sharedState.RedNote.marketCategory === category.id }"
        @click="sharedState.RedNote.marketCategory = category.id"
      >
        {{ category.name }}
      </div>
    </div>

    <div class="market-content">
      <div class="product-grid">
        <div
          v-for="product in filteredProducts"
          :key="product.id"
          class="product-card"
          @click="viewProductDetail(product)"
        >
          <div class="product-image" :style="`background-image: url('${product.image}')`"></div>
          <div class="product-info">
            <div class="product-title">{{ product.title }}</div>
            <div class="product-price">{{ product.price }}</div>
            <div class="product-seller">
              <div class="seller-avatar"></div>
              <span class="seller-name">{{ product.seller }}</span>
            </div>
            <div class="product-stats">
              <span>想要 {{ product.wants }}</span>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="rednote-homepage-bottom">
      <div class="rednote-homepage-bottom-button" @click="sharedState.RedNote.activeTab = 'home'">首页</div>
      <div class="rednote-homepage-bottom-button" style="color: black; font-size: 18px">市集</div>
      <div
        style="width: 3rem; height: 40px; background-color: #ea3e4a; border-radius: 9px; position: relative"
        @click="sharedState.phone.activeApp = 'QQ'"
      >
        <div
          style="
            width: 50%;
            background-color: white;
            height: 4px;
            position: absolute;
            border-radius: 5px;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
          "
        ></div>
        <div
          style="
            width: 50%;
            background-color: white;
            height: 4px;
            position: absolute;
            border-radius: 5px;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%) rotate(90deg);
          "
        ></div>
      </div>
      <div class="rednote-homepage-bottom-button">消息</div>
      <div class="rednote-homepage-bottom-button">我的</div>
    </div>
  </div>

  <!-- 商品详情页面 -->
  <div v-show="sharedState.RedNote.activeProduct && sharedState.phone.activeApp === 'RedNote'" class="product-detail">
    <div class="detail-header">
      <div class="back-button" @click="sharedState.RedNote.activeProduct = null">
        <svg viewBox="0 0 1024 1024" width="20" height="20">
          <path d="M724 218.3L481.9 461.5l240.8 240.8-47.5 47.5L386.9 461.5 676.5 170.8z" fill="#000"></path>
        </svg>
      </div>
      <div class="header-title">商品详情</div>
      <div class="header-actions">
        <svg viewBox="0 0 1024 1024" width="20" height="20">
          <path
            d="M768 810.6c0 47.1-38.1 85.3-85.3 85.3s-85.3-38.1-85.3-85.3 38.1-85.3 85.3-85.3 85.3 38.1 85.3 85.3z m-384 0c0 47.1-38.1 85.3-85.3 85.3s-85.3-38.1-85.3-85.3 38.1-85.3 85.3-85.3 85.3 38.1 85.3 85.3zM170.7 810.6c0 47.1-38.1 85.3-85.3 85.3S0 857.7 0 810.6s38.1-85.3 85.3-85.3 85.4 38.2 85.4 85.3z"
            fill="#000"
          ></path>
        </svg>
      </div>
    </div>

    <div v-if="sharedState.RedNote.activeProduct" class="detail-content">
      <div class="product-images">
        <div class="main-image" :style="`background-image: url('${sharedState.RedNote.activeProduct.image}')`"></div>
      </div>

      <div class="product-detail-info">
        <div class="detail-price">{{ sharedState.RedNote.activeProduct.price }}</div>
        <div class="detail-title">{{ sharedState.RedNote.activeProduct.title }}</div>
        <div class="detail-desc">{{ sharedState.RedNote.activeProduct.description }}</div>

        <div class="seller-info">
          <div class="seller-avatar"></div>
          <div class="seller-details">
            <div class="seller-name">{{ sharedState.RedNote.activeProduct.seller }}</div>
            <div class="seller-rating">⭐ 4.9 (128评价)</div>
          </div>
          <button class="follow-btn" @click="followSeller">关注</button>
        </div>

        <div class="product-actions">
          <button class="cart-btn" @click="addToCart">加入购物车</button>
          <button class="buy-btn" @click="buyNow">立即购买</button>
        </div>
      </div>
    </div>
  </div>

  <!-- 购物车页面 -->
  <div v-show="sharedState.RedNote.activeTab === 'cart' && sharedState.phone.activeApp === 'RedNote'" class="cart-page">
    <div class="cart-header">
      <div class="back-button" @click="sharedState.RedNote.activeTab = 'market'">
        <svg viewBox="0 0 1024 1024" width="20" height="20">
          <path d="M724 218.3L481.9 461.5l240.8 240.8-47.5 47.5L386.9 461.5 676.5 170.8z" fill="#000"></path>
        </svg>
      </div>
      <div class="header-title">购物车</div>
      <div class="header-actions" @click="toggleCartManagement">{{ isManagingCart ? '完成' : '管理' }}</div>
    </div>

    <div class="cart-content">
      <div v-if="sharedState.RedNote.cart.length === 0" class="empty-cart">
        <div class="empty-icon">🛒</div>
        <div class="empty-text">购物车还是空的</div>
        <button class="go-shopping" @click="sharedState.RedNote.activeTab = 'market'">去逛逛</button>
      </div>

      <div v-else class="cart-items">
        <!-- 购物车商品列表 -->
        <div v-for="(item, index) in sharedState.RedNote.cart" :key="item.id" class="cart-item">
          <div v-if="isManagingCart" class="item-select">
            <input v-model="item.selected" type="checkbox" />
          </div>
          <div class="item-image" :style="`background-image: url('${item.image}')`"></div>
          <div class="item-info">
            <div class="item-title">{{ item.title }}</div>
            <div class="item-price">{{ item.price }}</div>
            <div class="item-seller">{{ item.seller }}</div>
            <div v-if="isManagingCart" class="item-actions">
              <button class="delete-btn" @click="removeFromCart(index)">删除</button>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div v-if="sharedState.RedNote.cart.length > 0 && isManagingCart" class="cart-management">
      <button class="select-all-btn" @click="selectAllItems">
        {{ isAllSelected ? '取消全选' : '全选' }}
      </button>
      <button class="buy-selected-btn" @click="buySelectedItems">购买选中</button>
      <button class="delete-selected-btn" @click="deleteSelectedItems">删除选中</button>
    </div>

    <div class="rednote-homepage-bottom">
      <div class="rednote-homepage-bottom-button" @click="sharedState.RedNote.activeTab = 'home'">首页</div>
      <div class="rednote-homepage-bottom-button" @click="sharedState.RedNote.activeTab = 'market'">市集</div>
      <div
        style="width: 3rem; height: 40px; background-color: #ea3e4a; border-radius: 9px; position: relative"
        @click="sharedState.phone.activeApp = 'QQ'"
      >
        <div
          style="
            width: 50%;
            background-color: white;
            height: 4px;
            position: absolute;
            border-radius: 5px;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
          "
        ></div>
        <div
          style="
            width: 50%;
            background-color: white;
            height: 4px;
            position: absolute;
            border-radius: 5px;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%) rotate(90deg);
          "
        ></div>
      </div>
      <div class="rednote-homepage-bottom-button">消息</div>
      <div class="rednote-homepage-bottom-button">我的</div>
    </div>
  </div>
</template>

<script setup>
import { computed, ref } from 'vue';
import { sharedState } from '../shared-state';
import post from './post.vue';

// 初始化市集相关状态
if (!sharedState.RedNote.activeTab) {
  sharedState.RedNote.activeTab = 'home';
}
if (!sharedState.RedNote.marketCategory) {
  sharedState.RedNote.marketCategory = 'all';
}
if (!sharedState.RedNote.cart) {
  sharedState.RedNote.cart = [];
}
if (!sharedState.RedNote.products) {
  sharedState.RedNote.products = [];
}

// 购物车管理状态
const isManagingCart = ref(false);

// 商品分类
const marketCategories = [
  { id: 'all', name: '全部' },
  { id: 'cultivation', name: '修炼资源' },
  { id: 'weapon', name: '法器法宝' },
  { id: 'potion', name: '丹药灵草' },
  { id: 'artifact', name: '古宝奇物' },
  { id: 'fashion', name: '仙衣霓裳' },
];

// 计算属性：根据分类筛选商品
const filteredProducts = computed(() => {
  const products = sharedState.RedNote.products || [];
  if (sharedState.RedNote.marketCategory === 'all') return products;
  return products.filter(product => product.category === sharedState.RedNote.marketCategory);
});

// 计算属性：检查是否全选
const isAllSelected = computed(() => {
  if (sharedState.RedNote.cart.length === 0) return false;
  return sharedState.RedNote.cart.every(item => item.selected);
});

// 查看商品详情
const viewProductDetail = product => {
  sharedState.RedNote.activeProduct = product;
};

// 关注商家
const followSeller = () => {
  if (sharedState.RedNote.activeProduct) {
    const seller = sharedState.RedNote.activeProduct.seller;
    alert(`已关注商家：${seller}`);
  }
};

// 加入购物车
const addToCart = () => {
  if (sharedState.RedNote.activeProduct) {
    const product = { ...sharedState.RedNote.activeProduct };
    // 添加选中状态用于管理
    product.selected = false;

    // 检查是否已经在购物车中
    const existingIndex = sharedState.RedNote.cart.findIndex(item => item.id === product.id);
    if (existingIndex === -1) {
      sharedState.RedNote.cart.push(product);

      // 生成加入购物车消息
      // const cartMessage = `将${product.seller}的${product.title}加入购物车，价格${product.price}`;

      // 切换到QQ应用
      // sharedState.phone.activeApp = 'QQ';

      // 设置到输入框
      // if (sharedState.phone.sendModel == '尾附') {
      //   const old_content = $('#send_textarea').val().trim();
      //   const new_content = old_content + cartMessage;
      //   $('#send_textarea')
      //     .val(new_content.trim() || '')[0]
      //     .dispatchEvent(new Event('input', { bubbles: true }));
      // } else {
      //   triggerSlash(`/send ${cartMessage.trim()}|/trigger`);
      // }

      // 清空缓存消息
      // sharedState.QQ.cacheMsg = [];
    } else {
      alert(`${product.title} 已在购物车中`);
    }
  }
};

// 立即购买
const buyNow = () => {
  if (sharedState.RedNote.activeProduct) {
    const product = sharedState.RedNote.activeProduct;
    const purchaseMessage = `购买了${product.seller}的商品(${product.title}),商品ID(${product.id})，花了${product.price}`;

    // 切换到QQ应用
    sharedState.phone.activeApp = 'QQ';

    // 生成购买消息并设置到输入框
    if (sharedState.phone.sendModel == '尾附') {
      const old_content = $('#send_textarea').val().trim();
      const new_content = old_content + purchaseMessage;
      $('#send_textarea')
        .val(new_content.trim() || '')[0]
        .dispatchEvent(new Event('input', { bubbles: true }));
    } else {
      triggerSlash(`/send ${purchaseMessage.trim()}|/trigger`);
    }

    // 清空缓存消息
    sharedState.QQ.cacheMsg = [];
  }
};

// 切换购物车管理状态
const toggleCartManagement = () => {
  isManagingCart.value = !isManagingCart.value;
};

// 从购物车移除商品
const removeFromCart = index => {
  sharedState.RedNote.cart.splice(index, 1);
};

// 全选/取消全选
const selectAllItems = () => {
  const newSelectedState = !isAllSelected.value;
  sharedState.RedNote.cart.forEach(item => {
    item.selected = newSelectedState;
  });
};

// 购买选中商品
const buySelectedItems = () => {
  const selectedItems = sharedState.RedNote.cart.filter(item => item.selected);
  if (selectedItems.length === 0) {
    alert('请选择要购买的商品');
    return;
  }

  let totalPrice = 0;
  let purchaseMessage = '';

  selectedItems.forEach((item, index) => {
    if (index > 0) purchaseMessage += '、';
    purchaseMessage += `购买了${item.seller}的商品(${item.title}),商品ID(${item.id})`;
    totalPrice += parseFloat(item.price.replace('灵石', ''));
  });

  purchaseMessage += `，总共花费${totalPrice}灵石`;

  // 切换到QQ应用
  sharedState.phone.activeApp = 'QQ';

  // 设置到输入框
  if (sharedState.phone.sendModel == '尾附') {
    const old_content = $('#send_textarea').val().trim();
    const new_content = old_content + purchaseMessage;
    $('#send_textarea')
      .val(new_content.trim() || '')[0]
      .dispatchEvent(new Event('input', { bubbles: true }));
  } else {
    triggerSlash(`/send ${purchaseMessage.trim()}|/trigger`);
  }

  // 从购物车移除已购买的商品
  sharedState.RedNote.cart = sharedState.RedNote.cart.filter(item => !item.selected);
  // 清空缓存消息
  sharedState.QQ.cacheMsg = [];
};

// 删除选中商品
const deleteSelectedItems = () => {
  sharedState.RedNote.cart = sharedState.RedNote.cart.filter(item => !item.selected);
};
</script>

<style>
/* 原有样式保持不变 */
.rednote-postpage-bottom {
  display: flex;
  align-items: center;
  width: 100%;
  height: 45px;
  padding: 0px 10px;
  border-top: 1px solid #f6f6f6;
  gap: 3px;
}
.rednote-postpage-comment {
  display: flex;
  align-items: start;
  gap: 8px;
  /* margin-bottom: 25px; */
}
.rednote-postpage-content::-webkit-scrollbar {
  display: none !important;
}
.rednote-postpage-content {
  display: flex;
  flex: 1;
  flex-direction: column;
  width: 100%;
  overflow-y: auto;
  scrollbar-width: none !important;
  -ms-overflow-style: none !important;
}
.rednote-postpage-top {
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 0 10px 10px;
  border-bottom: 1px solid #eaedf2;
}
.rednote-postpage {
  background-color: white;
  width: 100%;
  height: 100%;
  padding-top: 30px;
  display: flex;
  flex-direction: column;
}
.rednote-homepage-bottom-button {
  color: #939393;
  width: 3rem;
  font-size: 16px;
  text-align: center;
  cursor: pointer;
}
/* 修改所有页面的底部导航栏样式 */
.rednote-homepage-bottom {
  width: 100%;
  height: 50px;
  display: flex;
  justify-content: space-evenly;
  align-items: center;
  background-color: #ffffff;
  border-top: 1px solid #e4e4e4;
  /* 确保底部导航栏固定在底部 */
  position: relative;
  margin-top: auto; /* 在flex布局中推到最底部 */
}
.rednote-homepage-post-title {
  font-size: 16px;
  text-align: start;
  color: black !important;
}
.rednote-homepage-post-author {
  display: flex;
  align-items: center;
  gap: 5px;
  margin-top: 10px;
}
.rednote-homepage-post-info {
  padding: 10px;
}
.post-img-blue {
  background-color: #ebe8f9;
}
.post-img-pink {
  background-color: #fbe7f0;
}
.post-img-green {
  background-color: #edefc8;
}
.post-img-purple {
  background-color: #d9c0ff;
}
.rednote-homepage-post-img {
  font-size: 20px;
  padding: 2.5rem 1.5rem;
  border-radius: 5px;
  text-align: center;
}
.rednote-homepage-post {
  width: 100%;
  margin-top: 5px;
  background-color: #ffffff;
  border-radius: 5px;
  height: fit-content;
  cursor: pointer;
  /* box-shadow: 2px 2px 2px rgba(15, 15, 15, 0.3); */
}
.rednote-homepage-content::-webkit-scrollbar {
  display: none !important;
}
.rednote-homepage-content {
  width: 100%;
  height: auto;
  flex: 1;
  display: grid;
  grid-template-columns: 50% 50%;
  gap: 5px;
  padding: 5px;
  overflow-y: auto;
  scrollbar-width: none !important;
  -ms-overflow-style: none !important;
}
.rednote-homepage {
  width: 100%;
  height: 100%;
  padding-top: 35px;
  display: flex;
  flex-direction: column;
  background-color: #f8fcfd;
}
.rednote-homepage-top {
  display: flex;
  font-size: 18px;
  align-items: center;
  justify-content: space-between;
  padding: 0px 15px 10px;
  /* gap: 30px; */
  border-bottom: 1px solid #e4e4e4;
}
.rednote-homepage {
  letter-spacing: 1px;
  line-height: 1.4;
}

/* 市集页面样式 */
.rednote-market {
  width: 100%;
  height: 100%;
  padding-top: 35px;
  display: flex;
  flex-direction: column;
  background-color: #f8fcfd;
}

.rednote-market-top {
  display: flex;
  align-items: center;
  padding: 0px 15px 10px;
  border-bottom: 1px solid #e4e4e4;
  gap: 10px;
}

.market-search {
  flex: 1;
}

.search-box {
  display: flex;
  align-items: center;
  background: #f5f5f5;
  border-radius: 20px;
  padding: 8px 15px;
  gap: 8px;
}

.search-box input {
  border: none;
  background: transparent;
  outline: none;
  flex: 1;
  font-size: 14px;
}

.market-cart {
  cursor: pointer;
}

.market-categories {
  display: flex;
  padding: 10px 15px;
  gap: 15px;
  overflow-x: auto;
  border-bottom: 1px solid #e4e4e4;
}

.category-item {
  white-space: nowrap;
  padding: 5px 12px;
  border-radius: 15px;
  background: #f5f5f5;
  font-size: 14px;
  color: #646464;
  cursor: pointer;
}

.category-item.active {
  background: #ff2e63;
  color: white;
}

.market-content {
  flex: 1;
  overflow-y: auto;
}

.product-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 10px;
  padding: 10px;
}

.product-card {
  background: white;
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
  cursor: pointer;
}

.product-image {
  width: 100%;
  height: 150px;
  background-size: cover;
  background-position: center;
  background-color: #f5f5f5;
}

.product-info {
  padding: 10px;
}

.product-title {
  font-size: 14px;
  color: #333;
  margin-bottom: 5px;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
}

.product-price {
  font-size: 16px;
  color: #ff2e63;
  font-weight: bold;
  margin-bottom: 8px;
}

.product-seller {
  display: flex;
  align-items: center;
  gap: 5px;
  margin-bottom: 5px;
}

.seller-avatar {
  width: 20px;
  height: 20px;
  border-radius: 50%;
  background: #e4e4e4;
}

.seller-name {
  font-size: 12px;
  color: #646464;
}

.product-stats {
  font-size: 12px;
  color: #646464;
}

/* 商品详情页面样式 */
.product-detail {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: white;
  z-index: 100;
  padding-top: 35px; /* 添加这个，与主页保持一致 */
}

.detail-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 10px 15px;
  border-bottom: 1px solid #e4e4e4;
  background: white;
  /* 移除或调整 margin-top，因为已经有了 padding-top */
}

.back-button,
.header-actions {
  width: 30px;
  cursor: pointer;
}

.header-title {
  flex: 1;
  text-align: center;
  font-weight: bold;
}
/* 确保页面容器使用flex布局 */
.product-detail,
.cart-page {
  display: flex;
  flex-direction: column;
}
.detail-content {
  flex: 1;
  overflow-y: auto;
}

.product-images {
  width: 100%;
  height: 300px;
}

.main-image {
  width: 100%;
  height: 100%;
  background-size: cover;
  background-position: center;
}

.product-detail-info {
  padding: 15px;
}

.detail-price {
  font-size: 24px;
  color: #ff2e63;
  font-weight: bold;
  margin-bottom: 10px;
}

.detail-title {
  font-size: 18px;
  font-weight: bold;
  margin-bottom: 10px;
}

.detail-desc {
  font-size: 14px;
  color: #646464;
  line-height: 1.5;
  margin-bottom: 20px;
}

.seller-info {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 15px 0;
  border-top: 1px solid #e4e4e4;
  border-bottom: 1px solid #e4e4e4;
}

.seller-avatar {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  background: #e4e4e4;
}

.seller-details {
  flex: 1;
}

.seller-name {
  font-weight: bold;
  margin-bottom: 2px;
}

.seller-rating {
  font-size: 12px;
  color: #646464;
}

.follow-btn {
  padding: 6px 12px;
  border: 1px solid #ff2e63;
  color: #ff2e63;
  border-radius: 15px;
  background: white;
  cursor: pointer;
  font-size: 12px;
}

.product-actions {
  display: flex;
  gap: 10px;
  padding: 15px 0;
  position: sticky;
  bottom: 0;
  background: white;
}

.cart-btn,
.buy-btn {
  flex: 1;
  padding: 10px;
  border-radius: 20px;
  font-weight: bold;
  cursor: pointer;
  font-size: 14px;
}

.cart-btn {
  border: 1px solid #ff2e63;
  background: white;
  color: #ff2e63;
}

.buy-btn {
  background: #ff2e63;
  color: white;
  border: none;
}

/* 购物车页面样式 */
.buy-selected-btn {
  padding: 8px 16px;
  background: #ff2e63;
  color: white;
  border: none;
  border-radius: 15px;
  cursor: pointer;
  font-size: 14px;
}
/* 购物车页面样式 */
.cart-page {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: white;
  z-index: 100;
  padding-top: 35px; /* 添加这个，与主页保持一致 */
  display: flex;
  flex-direction: column;
}
.cart-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 10px 15px;
  border-bottom: 1px solid #e4e4e4;
  background: white;
  /* 移除或调整 margin-top */
}

.header-actions {
  color: #ff2e63;
  font-size: 14px;
  cursor: pointer;
}

.cart-content {
  flex: 1;
  overflow-y: auto;
  /* 确保内容区域可以正常滚动 */
}

.empty-cart {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100%;
  gap: 15px;
}

.empty-icon {
  font-size: 60px;
}

.empty-text {
  color: #646464;
}

.go-shopping {
  padding: 10px 30px;
  background: #ff2e63;
  color: white;
  border: none;
  border-radius: 20px;
  cursor: pointer;
}

.cart-item {
  display: flex;
  padding: 15px;
  border-bottom: 1px solid #e4e4e4;
  gap: 10px;
}

.item-select {
  display: flex;
  align-items: center;
}

.item-image {
  width: 80px;
  height: 80px;
  background-size: cover;
  background-position: center;
  border-radius: 8px;
}

.item-info {
  flex: 1;
}

.item-title {
  font-weight: bold;
  margin-bottom: 5px;
}

.item-price {
  color: #ff2e63;
  font-weight: bold;
  margin-bottom: 5px;
}

.item-seller {
  font-size: 12px;
  color: #646464;
  margin-bottom: 10px;
}

.item-actions {
  display: flex;
  justify-content: flex-end;
}

.delete-btn {
  padding: 4px 8px;
  border: 1px solid #e4e4e4;
  background: white;
  border-radius: 4px;
  font-size: 12px;
  cursor: pointer;
  color: #ff2e63;
}

.cart-management {
  display: flex;
  justify-content: space-between;
  padding: 10px 15px;
  border-top: 1px solid #e4e4e4;
  background: white;
}

.select-all-btn,
.delete-selected-btn {
  padding: 8px 16px;
  border: 1px solid #ff2e63;
  background: white;
  color: #ff2e63;
  border-radius: 15px;
  cursor: pointer;
  font-size: 14px;
}

.delete-selected-btn {
  background: #ff2e63;
  color: white;
}

/* 过渡动画 */
.slide-fade-enter-active {
  transition: all 0.3s ease-out;
}

.slide-fade-leave-active {
  transition: all 0.3s cubic-bezier(1, 0.5, 0.8, 1);
}

.slide-fade-enter-from,
.slide-fade-leave-to {
  transform: translateX(20px);
  opacity: 0;
}
</style>
