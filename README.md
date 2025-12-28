<!DOCTYPE html>
<html lang="fa">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>ادرین گیمز</title>
<style>
body{margin:0;font-family:tahoma;background:#0b0b12;color:#fff;text-align:center;overflow-x:hidden;}
header{background:linear-gradient(45deg,#000,#6a0dad);padding:25px;font-size:32px;font-weight:bold;text-shadow:0 0 12px #9d4edd;}
nav{display:flex;flex-wrap:wrap;justify-content:center;gap:10px;padding:10px;}
nav button,.btn{margin:6px;padding:12px 20px;border:none;border-radius:20px;background:linear-gradient(45deg,#7b2cbf,#5a189a);color:white;font-size:15px;cursor:pointer;transition:.3s;box-shadow:0 0 10px #6a0dad;}
nav button:hover,.btn:hover{transform:scale(1.08);box-shadow:0 0 25px #d0bfff;}
nav button:active,.btn:active{transform:scale(0.95);}
.section{display:none;padding:20px;animation:fadein 0.5s;}
@keyframes fadein{from{opacity:0;transform:translateY(20px);}to{opacity:1;transform:translateY(0);}}
.product{background:#1a1a24;padding:15px;border-radius:20px;margin:10px;display:inline-block;width:150px;box-shadow:0 0 18px #6a0dad;transition:.3s;vertical-align:top;}
.product:hover{transform:scale(1.08);box-shadow:0 0 28px #d0bfff;}
.product img{width:50px;margin-bottom:5px;}
.product button{margin-top:5px;width:40px;height:35px;border-radius:12px;font-weight:bold;}
input,textarea{width:90%;padding:10px;border-radius:14px;border:none;margin:6px;font-size:14px;background:#15151f;color:white;}
.chatBox{background:#1a1a24;border-radius:18px;padding:12px;margin:6px;text-align:left;max-height:250px;overflow-y:auto;box-shadow:0 0 15px #6a0dad;}
.chatInput{width:80%;padding:10px;border-radius:12px;border:none;margin:6px;background:#15151f;color:white;}
#supportBtn{position:fixed;bottom:25px;right:25px;width:65px;height:65px;border-radius:50%;background:linear-gradient(45deg,#7b2cbf,#5a189a);color:white;border:none;font-size:18px;cursor:pointer;box-shadow:0 0 15px #6a0dad;}
#supportBtn:hover{transform:scale(1.12);box-shadow:0 0 28px #d0bfff;}
#supportChatPage{display:none;position:fixed;top:0;left:0;width:100%;height:100%;background:#0b0b12;z-index:9999;flex-direction:column;display:flex;}
.box{background:#15151f;padding:10px;border-radius:14px;margin:6px;box-shadow:0 0 12px #6a0dad;text-align:left;}
img.icon{width:20px;vertical-align:middle;margin-right:8px;}
</style>
</head>
<body>

<header>ادرین گیمز</header>

<nav>
<button onclick="show('home')">خانه</button>
<button onclick="show('products')">محصولات</button>
<button onclick="show('cart')">سبد خرید</button>
<button onclick="show('register')">ثبت نام</button>
<button onclick="show('comments')">نظرات</button>
<button onclick="openTelegram()" class="btn">
<img src="https://upload.wikimedia.org/wikipedia/commons/8/82/Telegram_logo.svg" alt="Telegram" class="icon">کانال تلگرام
</button>
</nav>

<div id="home" class="section" style="display:block">
<h2>خوش آمدید 👋</h2>
<p>برای ادامه لطفا ثبت نام کنید یا محصولات را مشاهده کنید</p>
</div>

<div id="products" class="section">
<h2>محصولات</h2>
<div class="product">
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/8/85/Call_of_Duty_Warzone_icon.png/64px-Call_of_Duty_Warzone_icon.png" alt="80CP">
<div>80 CP</div>
<button class="btn" onclick="addCart(80)">+</button>
</div>
<div class="product">
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/8/85/Call_of_Duty_Warzone_icon.png/64px-Call_of_Duty_Warzone_icon.png" alt="160CP">
<div>160 CP</div>
<button class="btn" onclick="addCart(160)">+</button>
</div>
<div class="product">
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/8/85/Call_of_Duty_Warzone_icon.png/64px-Call_of_Duty_Warzone_icon.png" alt="320CP">
<div>320 CP</div>
<button class="btn" onclick="addCart(320)">+</button>
</div>
<br><button class="btn" onclick="show('home')">برگشت</button>
</div>

<div id="cart" class="section">
<h2>سبد خرید</h2>
<div id="cartItems"></div>
<h3 id="totalPrice"></h3>
<button class="btn" onclick="completeOrderForm()">تکمیل سفارش</button>
<br><button class="btn" onclick="show('home')">برگشت</button>
</div>

<div id="orderForm" class="section">
<h2>فرم تکمیل سفارش</h2>
<input id="fullName" placeholder="نام و نام خانوادگی"><br>
<input id="email" placeholder="ایمیل"><br>
<input id="phoneOrder" placeholder="شماره موبایل"><br>
<input id="account" placeholder="اکانت"><br>
<input id="passwordOrder" placeholder="رمز اکانت"><br>
<button class="btn" onclick="submitOrder()">تکمیل سفارش</button>
<br><button class="btn" onclick="show('cart')">برگشت</button>
</div>

<div id="register" class="section">
<h2>ثبت نام با شماره موبایل</h2>
<input id="regPhone" placeholder="شماره موبایل"><br>
<button class="btn" onclick="sendRegisterCode()">دریافت کد</button><br><br>
<input id="regCode" placeholder="کد تایید"><br>
<button class="btn" onclick="verifyRegister()">تایید و ثبت نام</button>
</div>

<div id="userDashboard" class="section">
<h2>داشبورد کاربری</h2>
<p>خوش آمدید کاربر!</p>
<button class="btn" onclick="openSupportChat()">💬 پشتیبانی</button><br>
<button class="btn" onclick="logout()">خروج</button>
<div id="userChat" class="chatBox" style="display:none;"></div>
<input id="userMsg" class="chatInput" placeholder="پیام شما" style="display:none;">
<button id="sendUserMsg" class="btn" style="display:none;" onclick="sendUserMessage()">ارسال پیام</button>
</div>

<div id="admin" class="section">
<h2>👑 داشبورد رئیس</h2>
<div id="usersList" class="box"></div>
<div id="ordersList" class="box"></div>
<div id="adminChat" class="chatBox"></div>
<input id="adminMsg" class="chatInput" placeholder="پاسخ شما">
<button class="btn" onclick="sendAdminMessage()">ارسال پاسخ</button>
<button class="btn" onclick="logout()">خروج</button>
</div>

<div id="comments" class="section">
<textarea id="commentText" placeholder="نظر بنویس"></textarea><br>
<button class="btn" onclick="sendComment()">ارسال</button>
<div id="commentList"></div>
</div>

<button id="supportBtn" onclick="openSupportChat()">💬</button>
<div id="supportChatPage">
  <div style="background:linear-gradient(45deg,#7b2cbf,#5a189a);padding:15px;font-weight:bold;text-align:center;">💬 پشتیبانی</div>
  <div id="supportChatBody" style="flex:1;padding:10px;overflow-y:auto;display:flex;flex-direction:column;"></div>
  <div style="display:flex;padding:10px;background:#15151f;">
    <input id="supportMsgInput" placeholder="پیام خود را بنویسید..." style="flex:1;padding:10px;border-radius:10px;border:none;background:#222;color:white;">
    <button class="btn" onclick="sendSupportMessage()">ارسال</button>
  </div>
  <button class="btn" style="margin:10px;" onclick="closeSupportChat()">برگشت</button>
</div>

<script>
// داده‌ها
const ADMIN_PHONE="09376292805";
let users=JSON.parse(localStorage.getItem("users")||"[]");
let codes=JSON.parse(localStorage.getItem("codes")||"{}");
let cart=JSON.parse(localStorage.getItem("cart")||"[]");
let orders=JSON.parse(localStorage.getItem("orders")||"[]");
let messages=JSON.parse(localStorage.getItem("messages")||"[]");
let logged=localStorage.getItem("logged")==="true";
let userPhone=localStorage.getItem("userPhone")||"";

// نمایش بخش‌ها
function show(id){document.querySelectorAll(".section").forEach(s=>s.style.display="none");document.getElementById(id).style.display="block";}

// ثبت نام
function sendRegisterCode(){
  const phone=regPhone.value.trim();
  if(!phone) return alert("شماره وارد کن");
  const code=Math.floor(1000+Math.random()*9000);
  codes[phone]=code;
  localStorage.setItem("codes",JSON.stringify(codes));
  alert("کد شما: "+code);
}

function verifyRegister(){
  const phone=regPhone.value.trim();
  const code=regCode.value.trim();
  if(codes[phone]!=code) return alert("کد اشتباه");
  if(!users.includes(phone)) users.push(phone);
  localStorage.setItem("users",JSON.stringify(users));
  localStorage.setItem("logged","true");
  localStorage.setItem("userPhone",phone);
  logged=true; userPhone=phone;
  if(phone===ADMIN_PHONE){ loadAdmin(); show("admin"); }
  else{ show("userDashboard"); }
}

// محصولات
function addCart(item){
  if(!logged) return alert("اول ثبت نام کن");
  cart.push(item);
  localStorage.setItem("cart",JSON.stringify(cart));
  renderCart();
}
function renderCart(){
  let sum=cart.reduce((a,b)=>a+b,0);
  cartItems.innerHTML=cart.length?cart.map(i=>i+" CP").join("<br>"):"خالی";
  totalPrice.innerText="مجموع: "+sum+" CP";
}

// فرم تکمیل سفارش
function completeOrderForm(){
  if(cart.length===0) return alert("سبد خرید خالی است");
  show("orderForm");
}
function submitOrder(){
  const fullName=document.getElementById("fullName").value;
  const email=document.getElementById("email").value;
  const phoneOrder=document.getElementById("phoneOrder").value;
  const account=document.getElementById("account").value;
  const passwordOrder=document.getElementById("passwordOrder").value;
  if(!fullName || !email || !phoneOrder || !account || !passwordOrder) return alert("تمام فیلدها را پر کنید");
  orders.push({phone:userPhone,items:cart.slice(),fullName,email,phoneOrder,account,passwordOrder});
  localStorage.setItem("orders",JSON.stringify(orders));
  cart=[]; localStorage.setItem("cart",JSON.stringify(cart));
  alert("سفارش با موفقیت ثبت شد ✅");
  renderCart();
  show(logged?(userPhone===ADMIN_PHONE?"admin":"userDashboard"):"home");
}

// داشبورد رئیس
function loadAdmin(){
  document.getElementById("usersList").innerHTML="👥 کاربران ثبت نام شده:<br>"+users.map(u=>"📱 "+u).join("<br>");
  ordersList.innerHTML="📦 سفارش‌ها:<br>"+orders.map(o=>`نام: ${o.fullName} | ایمیل: ${o.email} | شماره: ${o.phoneOrder} | اکانت: ${o.account} | رمز: ${o.passwordOrder} | آیتم‌ها: ${o.items.join(", ")}`).join("<br><hr>");
  renderSupportMessages();
}

// نظرات
let comments=JSON.parse(localStorage.getItem("comments")||"[]");
function sendComment(){
  if(!commentText.value.trim()) return;
  comments.push(commentText.value);
  localStorage.setItem("comments",JSON.stringify(comments));
  commentText.value="";
  loadComments();
}
function loadComments(){
  commentList.innerHTML=comments.map(c=>"<div class='box'>"+c+"</div>").join("");
}
loadComments();

// پشتیبانی
function openSupportChat(){
  document.querySelectorAll(".section").forEach(s=>s.style.display="none");
  document.getElementById("supportChatPage").style.display="flex";
  renderSupportMessages();
}
function closeSupportChat(){
  document.getElementById("supportChatPage").style.display="none";
  show(logged?(userPhone===ADMIN_PHONE?"admin":"userDashboard"):"home");
}
function sendSupportMessage(){
  const msg=document.getElementById("supportMsgInput").value.trim();
  if(!msg) return;
  messages.push({from:userPhone,to:ADMIN_PHONE,msg});
  localStorage.setItem("messages",JSON.stringify(messages));
  document.getElementById("supportMsgInput").value="";
  renderSupportMessages();
}
function sendUserMessage(){sendSupportMessage();}
function sendAdminMessage(){
  const msg=document.getElementById("adminMsg").value.trim();
  if(!msg) return;
  messages.push({from:ADMIN_PHONE,to:userPhone,msg});
  localStorage.setItem("messages",JSON.stringify(messages));
  document.getElementById("adminMsg").value="";
  renderSupportMessages();
}
function renderSupportMessages(){
  const chatBody=document.getElementById("supportChatBody");
  chatBody.innerHTML=messages.filter(m=>m.from===userPhone||m.to===userPhone)
    .map(m=>"<div class='box'><b>"+m.from+"</b>: "+m.msg+"</div>").join("");
  chatBody.scrollTop=chatBody.scrollHeight;
}

// کانال تلگرام
function openTelegram(){window.open("https://t.me/AMIRgimz","_blank");}

// خروج
function logout(){
  localStorage.setItem("logged","false");
  localStorage.removeItem("userPhone");
  logged=false; userPhone="";
  show("home");
}

renderCart();
</script>

</body>
</html>
