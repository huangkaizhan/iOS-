# 命名

###常规命名风格
1. 【强制】 代码中的命名均不能以下划线或美元符号开始，也不能以下划线或美元符号结束.
  * 反例： _name  /  __name  /  $object ...
  * 
2. 【强制】 代码中的命名严禁使用拼音与英文混合的方式，更不允许直接使用中文的方式。 说明：正确的英文拼写和语法可以让阅读者易于理解，避免歧义。注意，即使纯拼音命名方式也要避免采用。
  * 正例： alibaba / taobao / youku / hangzhou 等国际通用的名称，可视同英文。
  * 反例： DaZhePromotion [打折] / getPingfenByName() [评分] / int 某变量 = 3

3. 【强制】类名使用UpperCamelCase风格，必须遵从驼峰形式，特殊情况除外：UMeng(友盟)
  * 正例： Person / Pig  / UMeng
  * 反例： person / pig  / umeng
 
4. 【强制】方法名、参数名、成员变量、局部变量都统一使用lowerCamelCase风格，必须遵从驼峰形式。
 ```objc
// 正例
-(void)singSong:(NSString *)river
{
         NSLog(@"I am singing 大河向东流，天上的星星。。。");
}
```

5. 【强制】常量命名首字母大写，单词间用下划线隔开，力求语义表达完整清楚，不要嫌名字长。
 ```objc
// 正例
static NSInteger Max_Count = 100;
// 反例
static NSString *key_Photo = @"key_Photo";
```

6. 【强制】bool值属性命名要以面向对象思想为标准
```objc
// 是否选中
// 获取用is来获取，设置直接设置，符合面向对象思想
@property(nonatomic,,assign,getter=isSelected) BOOL selected;
```

7. 

###控件命名
