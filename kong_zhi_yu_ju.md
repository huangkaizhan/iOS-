# 控制语句


#if
1. 【强制】在if/else/for/while/do语句中必须使用大括号。即使只有一行代码，避免使用单行的形式：if (condition) statements;
```objc
// 反例
if (age == 18)
      NSLog(@"一朵花");
```
2. 【推荐】表达异常的分支时，少用if-else方式，推荐使用卫语句。卫语句示例如下：
```objc
-(void)getGrilFriendWithHeight:(CGFloat)height weight:(CGFloat)weight
{
        if (height < 150) {
            NSLog(@"太矮了");
            return;
        }
        if (weight > 250) {
            NSLog(@"太重了");
            return;
        }
        NSLog(@"刚刚好");
}
```
3. 【建议】不用使用字符串做判断，字符串容易出错，而且有些字符串是变动的
```objc
// 打印球队名称
-(void)printTeamNameWithNBA:(NSString *)NBA
{
        // 这他妈改名字就尴尬了😓
        if ([NBA isEqualToString:@"黄蜂队"]) {
            NSLog(@"黄蜂队");
        } else if ([NBA isEqualToString:@"骑士队"]) {
            NSLog(@"骑士队");
        } else {
            NSLog(@"无名队");
        }
}
```

###Switch
1. 每个case要么通过break/return等来终止
2. 必须包含一个default语句并且放在最后，即使它什么代码也没有
3. default中如果没有特别的操作，那么建议补上NSAssert断言，比如新增一个枚举类型，需要判断类型做操作，可能会遗漏，这是断言会提醒，当然是debug模式中
4. 如果case中要做的操作属于一个功能，建议抽取出来（可惜没热修复了）
```objc
SexType_bb type = SexTypeMan;
    switch (type) {
        case SexTypeMan:
            NSLog(@"我是男人");
            break;
        case SexTypeWoman:
            // 跳舞
            [self dance];
            break;
        case SexTypeUnknow:
            NSLog(@"我是不知道我是什么");
            break;
        default:
            NSAssert(1 == 2, @"看一下是否有问题哦"); // 视情况而定
            break;
    }
```

###其他
1. 【推荐】循环体中的语句要考量性能，以下操作尽量移至循环体外处理，如定义对象、变量、获取数据库连接，进行不必要的try-catch操作（这个try-catch是否可以移至循环体外）
2. 【推荐】接口入参保护，这种场景常见的是用于做批量操作的接口