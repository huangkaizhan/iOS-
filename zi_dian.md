# 字典

###命名
1.  【建议】NSDictionary使用dict后缀
2.  【建议】NSMutableDictionary使用dictM后缀
4.  【建议】数组元素类型如果一致，建议带上类型标识符
```objc
    NSDictionary *dict = [NSDictionary dictionary];
    NSMutableDictionary *dictM = [NSMutableDictionary dictionary];
    NSMutableDictionary <NSString *, NSString *>*dictM = [NSMutableDictionary dictionary];
```

###增（NSMtableArray）
1. 统一使用分类方法
```objc
-(void)testArrayM
{
        NSMutableArray *arrayM = [NSMutableArray array];
        id obj;
        // 反例 ：obj不能为nil, 下标越界
    //    [arrayM addObject:obj];
    //    [arrayM insertObject:obj atIndex:3];
    
        // 正例 ：使用分类方法
        [arrayM addObjectSafe:obj];
        [arrayM insertObjectSafe:obj atIndex:3];
}
```