# 方法

###网络
1. 统一使用request开头，因为get方法怕有误解，故不使用
2. request后加的是模块名称，比如宝宝模块baby
```objc
// 正例
/**
 *  宝宝列表
 *
 *  @param dict                参数字典
 */
+(void)requestBabyListWithDict:(NSDictionary *)dict;
/**
 *  添加宝宝
 *
 *  @param dict                参数字典
 */
+(void)requestBabyAddWithDict:(NSDictionary *)dict;
// 反例,鬼知道是哪个标签列表
/**
 *  标签列表
 *
 *  @param dict                参数字典
 */
+(void)tagListWithDict:(NSDictionary *)dict;
```
3. 加载分页列表数据，下拉刷新推荐使用requestFirstPageData
```objc
// 列表下拉
-(void)pullDown
{
        // 加载第一页数据
        [self requestFirstPageData];
}
// 加载第一页数据
-(void)requestFirstPageData
{
        // 请求操作
}
```
4. 加载分页列表数据，上拉加载下一页推荐使用requestNextPageData
```objc
// 列表上拉
-(void)pullUp
{
        // 加载下一页数据
        [self requestNextPageData];
}
// 加载下一页数据
-(void)requestNextPageData
{
        // 请求操作
}
```

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
3. 通知，添加通知使用addNotifications，移除使用removeNotifications，通知方法以notify前缀开头
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
```
4. 对象初始化，对象方法使用initWith前缀，类方法使用类名前缀
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
5.
