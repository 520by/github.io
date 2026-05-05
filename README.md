# 超自然行动组专属商城

这是一个由 GitHub Pages 托管的在线商城网站。

## 功能特性

- 🛒 动态商品展示
- 🎨 紫色渐变主题设计
- 💳 购物车系统
- 📋 订单表单
- 💰 支付流程演示

## 访问地址

[https://520by.github.io](https://520by.github.io)

## 文件说明

- `index.html` - 主网页
- `README.md` - 项目说明文档
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: "Microsoft YaHei", sans-serif;
    }
    body {
      background-color: #0f0f1a;
      color: #f0f0f0;
      line-height: 1.6;
    }
    header {
      background: linear-gradient(90deg, #1a1a2e, #6a0dad);
      padding: 20px;
      text-align: center;
      position: sticky;
      top: 0;
      z-index: 99;
      box-shadow: 0 2px 15px rgba(106, 13, 173, 0.5);
    }
    header h1 {
      color: #e0c3fc;
      font-size: 28px;
      margin-bottom: 8px;
    }
    header p {
      color: #d1c4e9;
      font-size: 14px;
    }
    .cart-btn {
      position: absolute;
      right: 25px;
      top: 25px;
      background: #ff4d6d;
      color: #fff;
      padding: 8px 15px;
      border-radius: 20px;
      cursor: pointer;
      font-size: 14px;
      border: none;
    }
    .cart-count {
      background: #fff;
      color: #ff4d6d;
      border-radius: 50%;
      padding: 2px 6px;
      margin-left: 5px;
    }
    .container {
      max-width: 1200px;
      margin: 40px auto;
      padding: 0 20px;
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
      gap: 25px;
    }
    .goods-card {
      background: #1e1e30;
      border-radius: 15px;
      overflow: hidden;
      border: 1px solid #6a0dad;
      transition: all 0.3s ease;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
    }
    .goods-card:hover {
      transform: translateY(-8px);
      box-shadow: 0 5px 20px rgba(106, 13, 173, 0.6);
    }
    .goods-img {
      width: 100%;
      height: 200px;
      object-fit: cover;
      background: #2d2d44;
    }
    .goods-info {
      padding: 20px;
      flex: 1;
    }
    .goods-title {
      color: #e0c3fc;
      font-size: 20px;
      margin-bottom: 10px;
    }
    .goods-desc {
      color: #b3b3cc;
      font-size: 14px;
      margin-bottom: 12px;
      min-height: 40px;
    }
    .goods-price {
      color: #ff4d6d;
      font-size: 22px;
      font-weight: bold;
      margin-bottom: 15px;
    }
    .add-cart {
      width: 100%;
      padding: 10px;
      background: #6a0dad;
      color: #fff;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      font-size: 15px;
      transition: 0.3s;
    }
    .add-cart:hover {
      background: #7b2cbf;
    }
    .cart-modal {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0,0,0,0.8);
      z-index: 100;
      padding: 50px 20px;
      overflow-y: auto;
    }
    .cart-content {
      max-width: 600px;
      background: #1e1e30;
      margin: 0 auto;
      padding: 30px;
      border-radius: 15px;
      border: 1px solid #6a0dad;
    }
    .cart-item {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 12px 0;
      border-bottom: 1px solid #333;
    }
    .cart-total {
      text-align: right;
      font-size: 20px;
      color: #ff4d6d;
      margin: 20px 0;
    }
    .order-btn {
      width: 100%;
      padding: 12px;
      background: #ff4d6d;
      color: #fff;
      border: none;
      border-radius: 8px;
      font-size: 16px;
      cursor: pointer;
      margin-bottom: 12px;
    }
    .order-btn:disabled {
      opacity: 0.6;
      cursor: not-allowed;
    }
    .close-cart {
      text-align: right;
      cursor: pointer;
      color: #fff;
      font-size: 20px;
      margin-bottom: 15px;
      float: right;
    }
    .order-form {
      margin-top: 30px;
      display: none;
    }
    .form-item {
      margin-bottom: 18px;
    }
    .form-item label {
      display: block;
      margin-bottom: 8px;
      color: #e0c3fc;
    }
    .form-item input, .form-item textarea {
      width: 100%;
      padding: 10px;
      background: #2d2d44;
      border: 1px solid #6a0dad;
      border-radius: 8px;
      color: #fff;
      outline: none;
    }
    .pay-area {
      margin-top: 25px;
      text-align: center;
      display: none;
    }
    .pay-img {
      width: 200px;
      height: 200px;
      margin: 15px 0;
      background: #222;
    }
    footer {
      text-align: center;
      padding: 25px;
      background: #1a1a2e;
      color: #999;
      margin-top: 50px;
    }
  </style>
</head>
<body>
  <header>
    <h1>超自然行动组专属商城</h1>
    <p>官方唯一指定商城，安全高效，欢迎选购</p>
    <button class="cart-btn" onclick="openCart()">
      🛒 购物车 <span class="cart-count" id="cartCount">0</span>
    </button>
  </header>

  <div class="container" id="goodsContainer">
    <!-- 商品列表，填充于JS -->
  </div>

  <!-- 购物车弹窗 -->
  <div class="cart-modal" id="cartModal">
    <div class="cart-content">
      <div class="close-cart" onclick="closeCart()">✖</div>
      <h2 style="color:#e0c3fc;">🛒 我的购物车</h2>
      <div id="cartList"></div>
      <div class="cart-total">合计 <span id="cartTotal">0.00</span> 元</div>
      <button class="order-btn" onclick="showOrderForm()" id="toOrderBtn">提交订单</button>
      <!-- 订单表单 -->
      <form id="orderForm" class="order-form" onsubmit="submitOrder(event)">
        <div class="form-item">
          <label for="orderNote">备注信息（选填）</label>
          <textarea id="orderNote" rows="2"></textarea>
        </div>
        <button class="order-btn" type="submit">确认下单</button>
      </form>
      <!-- 支付区域 -->
      <div class="pay-area" id="payArea">
        <h3 style="color:#ff4d6d;">扫码支付收款码</h3>
        <img class="pay-img" src="https://dummyimage.com/200x200/6a0dad/fff&text=PAY" alt="收款码" />
        <div style="color:#e0c3fc;margin-top:10px;">支付完成后添加微信：xxxxxx<br>备注订单号：<span id="orderId"></span></div>
      </div>
    </div>
  </div>

  <footer>
    &copy; 2026 超自然行动组专属商城 | QQ/微信联系：xxxxxx
  </footer>

  <script>
    // 示例商品列表
    const goods = [
      {
        title: "超自然彩签定制",
        desc: "渐变/彩色/花式签名，一对一设计",
        price: 6.66,
        img: "https://dummyimage.com/300x200/6a0dad/fff&text=%E5%BD%A9%E7%AD%BE"
      },
      {
        title: "摸金脚本（优化版）",
        desc: "图像识别+真人模拟，防检测",
        price: 18,
        img: "https://dummyimage.com/300x200/333/fff&text=%E6%91%B8%E9%87%91%E8%84%9A%E6%9C%AC"
      },
      {
        title: "纯手动代肝服务",
        desc: "摸金/等级/任务/日常，安全高效不封号",
        price: 25,
        img: "https://dummyimage.com/300x200/222/fff&text=%E4%BB%A3%E8%82%9D"
      },
      {
        title: "全站定制服务",
        desc: "脚本/彩签/网页/教程，按需定制",
        price: 12.88,
        img: "https://dummyimage.com/300x200/444/fff&text=%E5%AE%9A%E5%88%B6"
      }
    ];

    // 填充商品到页面
    function renderGoods() {
      const container = document.getElementById('goodsContainer');
      container.innerHTML = '';
      goods.forEach(good => {
        container.innerHTML += `
        <div class="goods-card">
          <img src="${good.img}" class="goods-img" alt="${good.title}" />
          <div class="goods-info">
            <div class="goods-title">${good.title}</div>
            <div class="goods-desc">${good.desc}</div>
            <div class="goods-price">¥${good.price}</div>
            <button class="add-cart" onclick="addToCart('${good.title}', ${good.price})">加入购物车</button>
          </div>
        </div>
        `;
      });
    }

    let cart = [];

    function addToCart(name, price) {
      cart.push({ name, price });
      updateCart();
      alert("已加入购物车！");
    }

    function updateCart() {
      document.getElementById("cartCount").innerText = cart.length;
      let total = 0;
      const cartList = document.getElementById("cartList");
      cartList.innerHTML = "";
      cart.forEach((item, index) => {
        total += item.price;
        cartList.innerHTML += `
          <div class="cart-item">
            <span>${item.name} </span>
            <span>¥${item.price.toFixed(2)}</span>
            <button style="background:none;border:none;color:#ff4d6d;cursor:pointer;font-size:16px;" title="移除" onclick="removeCartItem(${index})">×</button>
          </div>
        `;
      });
      document.getElementById("cartTotal").innerText = total.toFixed(2);
      document.getElementById("toOrderBtn").disabled = cart.length === 0;
    }

    function removeCartItem(index) {
      cart.splice(index, 1);
      updateCart();
    }

    function openCart() {
      document.getElementById("cartModal").style.display = "block";
      updateCart();
      document.getElementById("orderForm").style.display = "none";
      document.getElementById("payArea").style.display = "none";
    }

    function closeCart() {
      document.getElementById("cartModal").style.display = "none";
      document.getElementById("orderForm").style.display = "none";
      document.getElementById("payArea").style.display = "none";
    }

    function showOrderForm() {
      if (cart.length === 0) {
        alert("购物车为空！");
        return;
      }
      document.getElementById("orderForm").style.display = "block";
      document.getElementById("payArea").style.display = "none";
    }

    // 模拟订单ID
    function genOrderId() {
      return 'OD' + Date.now().toString().slice(-7);
    }

    function submitOrder(e) {
      e.preventDefault();
      // 此处仅前端演示
      document.getElementById("orderForm").style.display = "none";
      document.getElementById("payArea").style.display = "block";
      const orderId = genOrderId();
      document.getElementById("orderId").innerText = orderId;
      // 清空购物车
      cart = [];
      updateCart();
    }

    // 初始化
    renderGoods();
    updateCart();

  </script>
</body>
</html>