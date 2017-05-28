# 代码格式

###大括号
规则 : 
* 左大括号前不换行。
* 左大括号后换行。 
* 右大括号前换行。 
* 右大括号后还有else等代码则不换行；表示终止的右大括号后必须换行。


1. 方法 ： 左右大括号到独占一行（不管是不是系统方法）
```objc
// 跳舞，由于下面void前面打空格会有问题，所以去掉，真实代码比如加上
-(void)dance
{
        // 我要跳舞，我要上天
}
```
2. 代码块，控制语句，循环语句等等，左大括号加空格尾随其后，最后右大括号独占一行
```objc
-(NSArray *)calerdarArray
{
        if (!_calerdarArray) { // 我在这里哦
            _calerdarArray = [NSArray array];
        }
        return _calerdarArray;
}
NSInteger age = 18;
    if (age >= 18) {
        // 老了，下面右大括号不换行
    } else {
        // 嫩，结尾换行
    }
```
3. 字典初始化，超过四个需要换行，没超过四个可以不换行
```objc
// 不换行
NSDictionary *dict = @{};
// 小于四个不换行
NSDictionary *dict1 = @{ @"name" : @"黄凯展", @"age" : @"100", @"single" : @YES, @"sb" : @(0)};
// 大于等于四个右大括号换行
NSDictionary *dict2 = @{  @"name" : @"黄凯展",
                             @"age" : @"100",
                             @"single" : @YES,
                             @"sb" : @(0),
                             @"height" : @"185"};
```
4. switch, while等等的大括号遵循规则
```objc
NSInteger age = 18;
   switch (age) { // 不换行
        case 18:{ // 不换行
            NSInteger num = 10;
        } // 独占一行
            break;
        case 20:
            NSLog(@"your sister");
            break;
        default:
            NSAssert(1 == 2, @"没有满足的条件");
            break;
    }
while (age > 10) {
        age--;
    }
```

###空格
1. 【强制】 左小括号和字符之间不出现空格；同样，右小括号和字符之间也不出现空格
```objc
// 跳舞，由于下面void前面打空格会有问题，所以去掉，真实代码比如加上
-(void)dance
{
        // 我要跳舞，我要上天
}
```