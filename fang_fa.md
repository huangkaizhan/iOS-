# 方法

### UI

1. 初始化UI，建议使用setup前缀或者是prepare前缀，统一
```objc
-(void)setupUI
{
        // 导航
        [self setupNavigation];
        // 头部
        [self setupHeaderView];
}
// 导航
-(void)setupNavigation
{
        self.navigationItem.title = @"标题";
}
// 头部
-(void)setupHeaderView
{
        NSLog(@"");
}
```
2. 上拉使用pullUp，下拉使用pullDown，而不是直接命名功能名
```objc
// 上拉
-(void)pullUp
{
        // 加载更更多
        [self loadMoreData];
}
// 下拉
-(void)pullDown
{
        // 刷新数据
        [self refreshData];
}
```

###通知
1. 添加通知使用addNotifications
2. 移除使用removeNotifications
3. 通知接收方法以notify前缀开头，有参数，参数名为notify变量
```objc
// 添加通知
-(void)addNotifications
{
        [[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(notifySwitchBaby:) name:@"Notify_Switch_Baby" object:nil];
}
// 移除通知
-(void)removeNotifications
{
        [[NSNotificationCenter defaultCenter] removeObserver:self];
}
// 通知方法
-(void)notifySwitchBaby:(NSNotification *)notify
{
        // 操作
}
```

###数据库
1. 数据库工具类以SqliteTool结尾命名，不适用CacheTool后缀
2. 方法采用和sql语句一样的命名方法（增删改查建表）


###其他
1. 对象初始化，对象方法使用initWith前缀，类方法使用类名前缀
```objc
/**
 根据名称初始化

 @param name 名称
 @return 对象
 */
-(instancetype)initWithName:(NSString *)name;
/**
 初始化

 @param name 名称
 @param age 年龄
 @return 对象
 */
-(instancetype)initWithName:(NSString *)name age:(NSInteger)age;
/**
 根据名称初始化

 @param name 名称
 @return 对象
 */
+(instancetype)godWithName:(NSString *)name;
```

