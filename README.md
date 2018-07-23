# wxpay-app

微信APP支付

## 说明文档

* [微信支付官方文档](https://pay.weixin.qq.com/wiki/doc/api/native.php?chapter=9_1)


## 安装

```shell
npm install wxpay-app
```

## 使用

```shell
  const fs = require('fs');
  const WeChatPay = require('wxpay-app').WeChatPay;

  const wpay = new WeChatPay({
    appid: 'xxx',
    mch_id: 'xxx',
    partner_key: 'xxx',
    pfx: fs.readFileSync('./apiclient_cert.p12')
  });
 
  wpay.createUnifiedOrder({
    body: 'Product Name',
    out_trade_no: new Date().getTime() + Math.random().toString().substr(2, 6),
    total_fee: 100,   // 1 yuan
    spbill_create_ip: '8.8.8.8',
    notify_url: 'http://8.8.8.8',
    trade_type: 'NATIVE',
    product_id: '1234567890'
  }, function(err, result){
    console.log(result);
  });

 
  wpay.createUnifiedOrder({
    body: 'Product Name',
    out_trade_no: new Date().getTime() + Math.random().toString().substr(2, 6),
    total_fee: 100,   // 1 yuan
    spbill_create_ip: '8.8.8.8',
    notify_url: 'http://8.8.8.8',
    trade_type: 'NATIVE',
    product_id: '1234567890',
    code_svg: true
  }, function(err, result){
    console.log(result);  // result.code_svg - QR SVG string
  });

 
  wpay.createUnifiedOrder({
    body: 'Product Name',
    out_trade_no: new Date().getTime() + Math.random().toString().substr(2, 6),
    total_fee: 100,   // 1 yuan
    spbill_create_ip: '8.8.8.8',
    notify_url: 'http://8.8.8.8',
    trade_type: 'APP',
    product_id: '1234567890'
  }, function(err, result){
    console.log(result);  // result.app_sign - sign string with prepay_id for WeChat App
                          // result.timestamp - signing timestamp for above app_sign
  });

 
  wpay.queryOrder({
    out_trade_no: 'xxx'
  }, function(err, result){
    console.log(result);
  });

 
  wpay.closeOrder({
    out_trade_no: 'xxx'
  }, function(err, result){
    console.log(result);
  });

 
  wpay.refund({
    out_trade_no: 'xxx',
    out_refund_no: 'yyy',
    total_fee: 100,
    refund_fee: 100,
    op_user_id: 'zzz'
  }, function(err, result){
    console.log(result);
  });

 
  wpay.transfer({
    partner_trade_no: 'xxx',
    openid: 'yyy',
    check_name: 'NO_CHECK',
    amount: 100,
    desc: 'memo',
    spbill_create_ip: '8.8.8.8'
  }, function(err, result){
    console.log(result);
  });

 
  wpay.refundQuery({
    out_refund_no: 'xxx',
  }, function(err, result){
    console.log(result);
  });


  wpay.validate(xml,function(err,result) {
     console.log(result);
  })

```

# wxpay-app
# wxpay-app
