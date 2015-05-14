# weixin-enterprisepay
修改自 weixin-redpack (https://github.com/tvrcgo/weixin-redpack)
微信发企业钱 for node.js

### Installation
```
npm install weixin-enterprisepay
```

### Usage

先创建一个付款实例 Payment，再调用 send() 发送付款，减少每次发付款的参数。
```js
var Payment = require('weixin-enterprisepay').Payment;

var payment = Payment({
	mchid: 'xxx',
	partner_key: 'xxxxxx',
	pfx: fs.readFileSync('./wxpay_cert.p12'),
	mch_appid: 'wxxxxxxx'
});

payment.send({
	partner_trade_no: '123426900220150325',
	openid: '接收人openid',
	check_name: 'NO_CHECK',
	amount: 100,
	spbill_create_ip: '14.23.102.146',
	desc: 'remark'
}, function(err, result){
	console.log(result);
})
```

直接调用 sendPayment() 输入所有参数。
```js
var entpayment = require('weixin-enterprisepay');

entpayment.sendPayment({
  mchid: 'xxx',
  partner_key: 'xxxxxxx',
  pfx: fs.readFileSync('./application_cert.p12'),
  mch_appid: 'wxxxxxx',
  partner_trade_no: '1234567890201503251234567890',
  openid: '接收人openid',
  check_name: 'NO_CHECK',
  amount: 100,
  spbill_create_ip: '14.23.102.146',
  desc: 'remark'
}, function(err, result){
  console.log(result);
});
```
