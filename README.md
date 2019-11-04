# saleor_teamwork
saleor开发小组

# **解决了bug：本地化地址解析出错**
解决方案：
--/saleor/saleor/dashboard/menu/utils.py--
```
def get_menu_item_as_dict(menu_item):
    data = {}
    if menu_item.linked_object:
        data["url"] = menu_item.linked_object.get_absolute_url()
    else:
        data["url"] = menu_item.url
    data["url"] = '/' + data["url"].split("/",2)[2]
    data["name"] = menu_item.name
    data["translations"] = {
        translated.language_code: {"name": translated.name}
        for translated in menu_item.translations.all()
    }
    return data
```

# 待解决问题
1. 加入购物车实现两种情况：跳转新页面/弹出框
2. 实现支付功能
3. 去掉非登录用户

