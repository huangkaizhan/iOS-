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

###增（NSMutableDictionary）
1. 统一使用分类方法
```objc
-(void)testDictionary
{
        NSMutableDictionary *dictM = [NSMutableDictionary dictionary];
        id obj;
        // 反例
        //[dictM setObject:obj forKey:@"name"]; // obj不能为nil
    
        // 正例
        [dictM setObjectSafe:@(45) forKey:@"age"];
        [dictM setObjectSafe:nil forKey:@"obj"];
}
```

###改（NSMutableDictionary）
1. 建议使用分类的replace方法而不是通过下标修改
```objc
-(void)testArrayM
{
        NSMutableArray *arrayM = [NSMutableArray array];
        [arrayM addObject:@"1"];
        id obj;
        // 反例
        //[arrayM replaceObjectAtIndex:1 withObject:@"aaa"]; //下标越界
        //[arrayM replaceObjectAtIndex:0 withObject:obj]; //obj不能为nil
    
        // 正例
        arrayM[1] = @"换了"; //使用了黑魔法重写，不建议
        arrayM[1] = obj; //同上
        // 使用分类方法
        [arrayM replaceObjectAtIndexSafe:2 withObject:@"2"];
        [arrayM replaceObjectAtIndexSafe:0 withObject:nil];
}
```