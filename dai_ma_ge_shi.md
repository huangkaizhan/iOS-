# 代码格式

###大括号
1. 方法 ： 左右大括号到独占一行
```objc
// 跳舞，由于下面void前面打空格会有问题，所以去掉，真实代码比如加上
-(void)dance
{
        // 我要跳舞，我要上天
}
```
2. 代码块，控制语句，循环语句等等，左大括号加空格尾随其后，右大括号独占一行
```objc
-(NSArray *)calerdarArray
{
        if (!_calerdarArray) { // 我在这里哦
            _calerdarArray = [NSArray array];
        }
        return _calerdarArray;
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