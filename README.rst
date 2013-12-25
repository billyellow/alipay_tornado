介绍
============

alipay_tronado 是支付宝接口的tornado版本，提供了担保交易，即时到帐和自动发货的接口。

fork自这个版本 `alipay_python <https://github.com/fengli/alipay_python>`_.因为之前接口中的notify_verify接口不方便tornado使用，所以修改了下，方便大家使用。 

接口描述 (alipay/alipay.py)
---------

提供了即时到帐，担保交易和确认发货的接口。

* 即时到帐

  def create_direct_pay_by_user(tn, subject, body, total_fee)

  tn - 'out_trade_no', 应该是你的网站订单系统中唯一订单匹配号
  subject - 'subject', 你的订单名称
  body - 'body', 订单描述
  total_fee - 'total_fee', 订单的总金额

  返回应该跳转的支付宝链接

* 担保交易

  def create_partner_trade_by_buyer (tn, subject, body, price)

  tn - 'out_trade_no', 应该是你的网站订单系统中唯一订单匹配号
  subject - 'subject', 你的订单名称
  body - 'body', 订单描述
  price - 'price', 商品单价

  返回应该跳转的支付宝链接

  note: 物流的类型等的设置在接口內默认设置，如果你需要每次修改可以扩展这个接口。

* 确认发货

  def send_goods_confirm_by_platform (tn)

  tn - 'trade_no', 注意这个不是你站点的唯一订单号，而是支付宝返回的在支付宝系统内唯一的订单号。

  返回确认发货应该跳转的链接。

