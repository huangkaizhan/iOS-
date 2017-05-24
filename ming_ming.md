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

###控件命名（统一强制）

1. View ： View结尾
```objc
// 背景
@property(nonatomic, weak) UIView *backView;
```
2. 图片 ： ImageView结尾
```objc
// 头像
@property(nonatomic, weak) UIView *avatarImageView;
```
3. 文字 ： Label结尾
```objc
// 姓名
@property(nonatomic, weak) UILabel *nameLabel;
```
4. 按钮 ： Button结尾, 不要缩略为btn
```objc
// 正例 ：跳舞
@property(nonatomic, strong) UIButton *danceButton;
// 反例 ：唱歌
@property(nonatomic, strong) UIButton *singBtn;
```
5. 输入框 ：TextField结尾
```objc
// 密码输入框
@property(nonatomic, strong) UITextField *passwordTextField;
```
6. 列表 ： TableView结尾，注，如果一个页面只有一个列表，那么可以命名为tableView
```objc
// 列表
@property(nonatomic, strong) UITableView *tableView;
```
7. 集合列表 ： CollectionView结尾，注，如果一个页面只有一个列表，那么可以命名为collectionView
```objc
// 集合列表
@property(nonatomic, strong) UICollectionView *collectionView;
```
8. 列表单元格 ：以Cell结尾
```objc
// 自定义cell
BBFirstTimeListCell *cell = [[BBFirstTimeListCell alloc] init];
```
9. 集合列表单元格 ：以ColCell结尾
```objc
// 自定义cell
BBFirstTimeListColCell *cell = [[BBFirstTimeListColCell alloc] init];
```
10. 滚动 ： 以ScrollView结尾，注，如果有特殊情况，那么可以命名为scrollView
```objc
// 轮播滚动视图
@property(nonatomic, strong) UIScrollView *bannerScrollView;
```
11. 其他 ： 跟上面类似，一般以控件名结尾


###通知
1. 通知名
  * 首字母大写
  * 单词以_分开
  * Notify_ + 模块 + 动作（不是功能） + 其他
```objc
// 正例
#define Notify_Switch_Baby                  @"Notify_Switch_Baby" 
```