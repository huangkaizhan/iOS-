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
6. 强类型变量，*号统一加载变量名前面，禁止不换行
 ```objc
// 正例
NSString *content = @"铲屎君";
// 反例
NSString*title = @"养猫";
NSString* text = @"不养了";
```



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




###通知命名
1. 通知名
  * 首字母大写
  * 单词以_分开
  * Notify_ + 模块 + 动作（不是功能） + 其他
```objc
// 正例, 切换宝宝
#define Notify_Baby_Switch                  @"Notify_Baby_Switch" 
// 反例, 切换宝宝
#define Notify_Switch_Baby                  @"Notify_Switch_Baby" 
// 反例，日历隐藏显示通知
#define Notify_showCalendar                 @"Notify_showCalendar"
```
2. 接收通知方法名
  * notify开头，注意是小写
  * 最好以通知名延续下来，别写要做的功能名
```objc
// 反例 ： 老子切换宝宝通知你，你直接刷新宝宝数据，万一后面还要处理缓存等等操作，这样就不符合单一原则了
[[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(refreshHomeBabyInfo) name:Notify_Baby_Switch object:nil];
// 正例 ： 明确告诉这是通知，里面想做什么事自己处理
[[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(notifyBabySwitch:) name:Notify_Baby_Switch object:nil];
// 正例
-(void)notifyBabySwitch:(NSNotification *)notify
{
        // 刷新宝宝详情
        // 缓存处理
        // 滚动
}
// 做了什么鬼东西，不好
-(void)refreshHomeBabyInfo
{
        [self resetUploadViewStatus];
        [self getGeneralize];
        [self loadBabyDetailData];
        [self.dataArray removeAllObjects];
        [self.tableView reloadData];
        [self loadHomeDataBase:@""];
        // 回滚第一条
        [self.tableView setContentOffset:CGPointMake(0,0) animated:NO];
}
```


###控制器命名
1. 前缀BB + 功能名称 + Controller
   * BBLoginController -> UIViewConroller (BB + Login + Conroller)
   * BBBuyWebController -> 非买不可网页控制器
   * BBTabController -> tabbar控制器
   * BBNavController -> nav控制器
   
2. 如果是基类,则加上前缀换成BBBase, 功能看需要添加
   * BBBaseWebConroller -> web控制器基类
   * BBBaseTableController -> 列表基类
   * BBBaseCollectionController -> 集合流基类

3. 如果功能名太长，可取单词首字母
  * BBPhotoGalleryListController -> BBPGListController  -> 小影记列表控制器
4. 如果是列表控制器，需要带table或者col
  * BBHomeListTableController -> 首页列表控制器
  * BBHomeListColController -> 首页列表流控制器

###ViewModel命名
1. 类统一使用ViewModel后缀
```objc
@interface BBBabyAddViewModel : BaseViewModel_lib
@end
```

###属性命名
1. 基本属性命名，对齐
2. 强类型的，*号跟在变量名前
```objc
// 总数
@property (nonatomic, assign) NSInteger allCount;
// 跳舞
@property (nonatomic, strong) UIButton *danceButton;
```
2. 布局命名 ：后缀需要加上Layout（强制）
```objc
// 点赞按钮左边约束
@property (weak, nonatomic) IBOutlet NSLayoutConstraint *likeButtonLeftLayout;
```
3. bool值命名 ：以面向对象思想为标准
```objc
// 是否选中
// 获取用is来获取，设置直接设置，符合面向对象思想
@property (nonatomic, assign, getter=isSelected) BOOL selected;
```
4. 接口返回的JSON数据，模型里属性命名最好加JSON空宏，证明是接口返回
```objc
// 头像
@property (nonatomic, copy) JSON_bb NSString *avatar;
```
5. KVO接听的属性，最好加上KVO空宏
```objc
// 相册是否加载成功
@property (nonatomic, assign, getter=isAlbumLoaded) KVO_bb BOOL albumLoaded;
```
6. 模型数组，最好指定数组元素类型
```objc
// 评论数组,每一个元素都是BBRecordCommentModel类型
@property (nonatomic, strong) JSON_bb NSMutableArray <BBRecordCommentModel *>*comments;
```
7. 代码块属性，以Block结尾
```objc
// 预览代码块
@property (nonatomic, copy) BlockWithTwoObject_bb previewBlock;
```
8. 数组命名，以array结尾，可变以arrayM结尾
9. 字典命名，以dict结尾，可变以dictM结尾


###枚举命名
1. 统一使用typedef enum关键字，枚举元素必须要用枚举名称开头
2. 没有特殊需求，默认从0开始
3. 如果怕跟第三方库冲突，可以加后缀区分
```objc
// 正例 ：性别
typedef enum {
    SexTypeUnknow, // 未知
    SexTypeMan,    // 男人
    SexTypeWoman,  // 女人
}SexType_bb; // 加了_bb区分，bb为项目统一前缀、后缀
// 反例 ：出生类型
typedef enum {
    BabyTypeUnBorn = 2,     // 未出生
    BabyTypeBorn = 1,       // 一出生
}BabyType_bb;
```

###宏定义
1. 遵守首字母大写，下划线区分单词的标准，除非特殊
```objc
// 反例 ：删除成长发育
#define Notify_deleteGrowUp                @"Notify_deleteGrowUp"
// 正例 ：删除成长发育
#define Notify_GrowUp_Delete               @"Notify_GrowUp_Delete"
// 正例 ：默认分割线颜色
#define Color_Default_SepLine              RGB(167.0, 160.0, 157.0)
// 正例 ：取色值相关的方法（特殊）
#define RGB_bb(r,g,b)                      [UIColor colorWithRed:(r)/255.f green:(g)/255.f blue:(b)/255.f alpha:1.f]
```

2. 密匙定义：以Key_开头
```objc
// 正例 ：跳转本app url schemes
#define Key_App_Url_Schemes                @"rdf200a0c37c3c3d53"
// 反例 ：修改宝宝名字Key，NameKey ? 写的是什么鬼
#define NameKey                            @"NameKey"
```

3. 友盟，全体大写，以BB__EVENT_开头
```objc
//分享到QQ空间
#define BB_EVENT_SHARE_QZONE               @"share_qzone"
```

4. 其他，看根据自己雪球目的定义，无需强制


###继承命名
1. 父类需要加base，加在哪里，具体看情况
```objc
// base加在中间是为了更明显的敲出来，提示
// 父头像
@property(nonatomic, weak) BBAvatarBaseImageView *avatarBaseImageView;
// 子头像
@property(nonatomic, weak) BBAvatarImageView *avatarImageView;
```

2. 方法名，也需要加base区分，如果需要强制重写，那么需要再加override
 ```objc
// 正例 ：布局基本UI
-(void)prepareBaseUI
{
     // 布局头部视图
     [self prepareOverrideBaseHeaderView];
}
// 正例
-(void)prepareOverrideBaseHeaderView
{
     // 子类必须重写
}
```


###代理命名
1. 代理以delegate后缀结尾，数据源以dataSource后缀结尾，其他视情况而定
1. 要求写全，最好的例子是UITableView代理
2. 默认为强制实现，如果可以不实现，必须加@optional
```objc
@protocol UITableViewDataSource<NSObject>
// 默认强制写
-(NSInteger)tableView:(UITableView *)tableView numberOfRowsInSection:(NSInteger)section;
// 可选要关键字标明
@optional
-(NSInteger)numberOfSectionsInTableView:(UITableView *)tableView;
@end
```