# 网络

1. 【建议】统一使用request开头，因为get方法怕有误解，故不使用
2. 【建议】request后加的是模块名称，比如宝宝模块Baby
```objc
// 反例,鬼知道是哪个标签列表
/**
 *  标签列表
 *
 *  @param dict                参数字典
 */
+(void)tagListWithDict:(NSDictionary *)dict;
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
```