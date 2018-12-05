---
layout: post
title: "paypal对接流程"
date: 2017-07-17 17:37
category : tech
---
            

## 概述

国内的支付接口相对一致，文档也很丰富。相比来说，paypal的接口复杂很多，并且文档大部分都是英文的。这次对接paypal基本的调研用了将近两天，才搞出个demo。简单记录下流程。


## 帮助地址
* paypal php sdk on github [地址](https://github.com/paypal/PayPal-PHP-SDK)
* 开发者中心 [地址](https://developer.paypal.com)

## 流程
1. 注册普通账号。
2. 升级为企业帐号。（国内版和国际版有区别，跟客服电话沟通，确认已经取消个人的高级账号，只保留企业帐号，但是可以通融，个人申请企业版，客服不会禁止。这一点，国外相对宽松，个人帐号能正常升级。国内一般几个小时就能正常使用） [地址：个人首页，左侧有帐号升级入口]
3. 生成api认证。完成后会提供 live版的帐号、密码和签名。 [地址](https://www.paypal.com/businessprofile/mytools/apiaccess)
4. 进入开发者中心 [地址](https://developer.paypal.com)
5. 添加应用，成功后，会提供client id和client secret，第三方支付基于此。 [地址](https://developer.paypal.com/developer/applications/)
6. paypal很人性化，提供了一套沙盒，可以使用live帐号，申请多个测试的沙盒帐号（包括用户和商户），金额随便充。[地址](https://developer.paypal.com/developer/accounts/)
7. 参考github samples。创建demo，使用沙盒帐号测试支付和付款的完整流程。[地址：根据需要选择demo](https://github.com/paypal/PayPal-PHP-SDK/tree/master/sample)
8. 对接网站，使用创建订单时paypal返回的 pay-id 来绑定 order-id，用于支付成功的回调更新order信息。

## 备注
* 创建订单后的请求、响应信息

```
Request Object

{
    "intent": "sale",
    "payer": {
        "payment_method": "paypal"
    },
    "redirect_urls": {
        "return_url": "http://simo/index/test/payback?success=1",
        "cancel_url": "http://simo/index/test/payback?success=0"
    },
    "transactions": [
        {
            "amount": {
                "currency": "USD",
                "total": "20",
                "details": {
                    "shipping": "1.20",
                    "tax": "1.30",
                    "subtotal": "17.50"
                }
            },
            "item_list": {
                "items": [
                    {
                        "name": "Ground Coffee 40 oz",
                        "currency": "USD",
                        "quantity": 1,
                        "sku": "123123",
                        "price": "7.50"
                    },
                    {
                        "name": "Granola bars",
                        "currency": "USD",
                        "quantity": 5,
                        "sku": "321321",
                        "price": "2"
                    }
                ]
            },
            "description": "Payment description",
            "payee": {
                "email": "stevendcoffey-facilitator@gmail.com"
            },
            "invoice_number": "596c752bc29bb"
        }
    ]
}

-------------------------------------
Response Object

{
    "intent": "sale",
    "payer": {
        "payment_method": "paypal"
    },
    "redirect_urls": {
        "return_url": "http://simo/index/test/payback?success=1",
        "cancel_url": "http://simo/index/test/payback?success=0"
    },
    "transactions": [
        {
            "amount": {
                "total": "20.00",
                "currency": "USD",
                "details": {
                    "subtotal": "17.50",
                    "tax": "1.30",
                    "shipping": "1.20"
                }
            },
            "payee": {
                "email": "stevendcoffey-facilitator@gmail.com"
            },
            "description": "Payment description",
            "invoice_number": "596c752bc29bb",
            "item_list": {
                "items": [
                    {
                        "name": "Ground Coffee 40 oz",
                        "sku": "123123",
                        "price": "7.50",
                        "currency": "USD",
                        "quantity": 1
                    },
                    {
                        "name": "Granola bars",
                        "sku": "321321",
                        "price": "2.00",
                        "currency": "USD",
                        "quantity": 5
                    }
                ]
            },
            "related_resources": []
        }
    ],
    "id": "PAY-975312049S097400MLFWHKLQ",
    "state": "created",
    "create_time": "2017-07-17T08:28:30Z",
    "links": [
        {
            "href": "https://api.sandbox.paypal.com/v1/payments/payment/PAY-975312049S097400MLFWHKLQ",
            "rel": "self",
            "method": "GET"
        },
        {
            "href": "https://www.sandbox.paypal.com/cgi-bin/webscr?cmd=_express-checkout&token=EC-8FH85352RH759293F",
            "rel": "approval_url",
            "method": "REDIRECT"
        },
        {
            "href": "https://api.sandbox.paypal.com/v1/payments/payment/PAY-975312049S097400MLFWHKLQ/execute",
            "rel": "execute",
            "method": "POST"
        }
    ]
}
```


* 支付成功后返回信息[get]

```
http://simo/index/test/payback?success=1&paymentId=PAY-975312049S097400MLFWHKLQ&token=EC-8FH85352RH759293F&PayerID=FJBS89BCKNBFY

data::
Array
(
    [success] => 1
    [paymentId] => PAY-6090569607833744ALFWHCRQ
    [token] => EC-3TN58531YN2607908
    [PayerID] => FJBS89BCKNBFY
)
```


