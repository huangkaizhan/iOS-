# 数组
###懒加载
    多个数组，有时创建用错了属性名，建议使用宏来懒加载数组，快捷安全
    
1. 宏定义
```objc
/* 
快捷创建NSMutableArray
用法一 ：在get方法里面直接使用宏ArrayM_Create
-(NSMutableArray *)array
{ 
        ArrayM_Create(_array);
}*/
#define ArrayM_Create(A)                       if (!A) {\
A = [NSMutableArray array];\
}\
return A;
/*
 用法二：传两个参数，一个为get方法名，一个为下划线变量名
 注意：这种方法调用时建议先敲中括号[],然后在中括号敲方法
 ArrayM_Create_Two(array1,_array1);
 */
#define ArrayM_Create_Two(A,B)                        - (NSMutableArray *)A\
{\
ArrayM_Create(B)\
}
```
2. 创建
```objc
// 用法一
-(NSMutableArray *)dataArray
{
        ArrayM_Create(_dataArray);
}
// 用法二
ArrayM_Create_Two(dataArray, _dataArray)
```
3. 没有对比就没有伤害
 ![](数组创建（老）.png)
 ![](数组创建（宏）.png)
 

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

###删（NSMtableArray）
1. 普通删除
```objc
-(void)testArrayM
{
        NSMutableArray *arrayM = [NSMutableArray array];
        [arrayM addObject:@"1"];
        id obj;
        // 反例
    //    [arrayM removeObject:obj]; // 不崩溃
    //    [arrayM removeObjectAtIndex:3]; // 索引越界
    
        // 正例
        [arrayM removeObjectSafe:obj];
        [arrayM removeObjectAtIndexSafe:3];
}
```
2. 遍历删除
```objc
-(void)testArrayMRemove
{
        NSMutableArray *arrayM = [NSMutableArray arrayWithObjects:@"1", @"1", @"1", @"4", nil];
        // 反例
        // 遍历取值不对
    //    for (NSInteger i = 0; i < arrayM.count; i++) {
    //        NSString *val = [arrayM objectAtIndex:i];
    //        NSLog(@"val = %@", val); // ---> 1,1
    //        if ([val isEqualToString:@"1"]) {
    //            [arrayM removeObjectAtIndex:i];
    //        }
    //    }
    
        // 崩溃 ：Collection <__NSArrayM> was mutated while being enumerated.
    //    for (NSString *val in arrayM) {
    //        NSLog(@"val = %@", val); // ---> 1
    //        if ([val isEqualToString:@"1"]) {
    //            [arrayM removeObject:val];
    //        }
    //    }
    
        // 正例 ：反序遍历
        for (NSInteger i = arrayM.count - 1; i >= 0; i--) {
            NSString *val = [arrayM objectAtIndex:i];
            NSLog(@"val = %@", val); // ---> 4,1,2,1
            if ([val isEqualToString:@"1"]) {
                [arrayM removeObjectAtIndex:i]; //最好使用分类方法
            }
        }
}
```

###改（NSMtableArray）
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

###查
1. 建议不要使用arr[4]这种方式取值，如果要，那么最好重写它的方法
2. 【强制】使用数组分类的objectAtIndexSafe:方法来取值，该方法实现做了一些崩溃处理，具体源码请看分类
```objc
-(void)testArray
{
        NSArray *array = @[];
        // 反例 ：数组越界闪退
    //    id failedObj = [array objectAtIndex:4];
    
        // 正例，统一使用分类方法，以safe后缀区分
        // obj为nil
        id obj = [array objectAtIndexSafe:-1];
        obj = [array objectAtIndexSafe:3];
    
        // 重写了方法,不建议
        obj = array[3];
    
        // 初始化
        array = [NSArray arrayWithObjectSafe:nil];
        array = [NSArray arrayWithArraySafe:nil];
}
```