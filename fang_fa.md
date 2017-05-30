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