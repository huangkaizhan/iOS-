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

###增改（NSMutableDictionary）
1. 统一使用分类方法
```objc
-(void)testDictionary
{
        NSMutableDictionary *dictM = [NSMutableDictionary dictionary];
        id obj;
        // 反例
        //[dictM setObject:obj forKey:@"name"]; // obj不能为nil
        // dictM[@"age"] = obj; 
        
        // 正例
        [dictM setObjectSafe:@(45) forKey:@"age"];
        [dictM setObjectSafe:obj forKey:@"obj"];
}
```

###创建
1. 统一使用分类方法，这里不举太多例子
```objc
-(void)testDictionary
{
        // 反例
        // NSDictionary *failedDict = [NSDictionary dictionaryWithObject:nil forKey:@"name"];
        // 正例
        NSDictionary *dict = [NSDictionary dictionaryWithObjectSafe:nil forKey:@"name"];
}
```