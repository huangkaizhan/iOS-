# 代码格式

###大括号
规则 : 
* 左大括号前不换行。
* 左大括号后换行。 
* 右大括号前换行。 
* 右大括号后还有else等代码则不换行；表示终止的右大括号后必须换行。


1. 【强制】方法 ： 左右大括号到独占一行（不管是不是系统方法）
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
// 正例
if (1 == 2) {
        NSLog(@"见鬼了。。。");
 }
// 反例
// 1 == 2 多了空格
   if ( 1 == 2 ) {
       NSLog(@"见鬼了。。。");
   }
   // 1==2 没空格
   if (1==2) {
       NSLog(@"见鬼了。。。");
   }
   // if 和 { 没空格
   if(i == 2){
       NSLog(@"见鬼了。。。");
   }
```
2. 【强制】if/for/while/switch/do等保留字与括号之间都必须加空格
3. 【强制】任何二目、三目运算符的左右两边都需要加一个空格。 说明：运算符包括赋值运算符=、逻辑运算符&&、加减乘除符号等
```objc
NSString *text = age == 18 ? @"一朵花" : @"一朵花";
self.view.hidden = self.dataArray.count;
```
4. 【推荐】字典, 左右大括号不空格，冒号左右空格，逗号后要加空格
```objc
NSDictionary *dict = @{@"name" : @"KK", @"height" : @"185"};
```
5. 【推荐】数组, 左右中括号不空格，每一元素逗号空格
```objc
NSArray *array = @[@"1", @"2", @"3"];
NSMutableArray *arrayM = [NSMutableArray arrayWithObjects:@"1", @"2", @"3", nil];
```
6. 方法，标识符（-\+）和返回值有空格，传参不空格，调用方法需要空格
```objc
// 调用传参不空格
[self sayWord:@"" toPeople:@"name"];
// 注意：这里的-和返回值是有空格的，这里格式不支持
-(void)sayWord:(NSString *)word toPeople:(NSString *)name
{
        NSLog(@"说唱");
}
// 正例
UIView *view = [[UIView alloc] init];
// 反例
// 调用方法没空格
UIView *view = [[UIView alloc]init];
// =号后没空格
UIView *view1 =[[UIView alloc] init];
```
7. 多个空格，请用tab健对齐
```objc
// 添加记录成功
#define Notify_Record_Add_Successed                 @"Notify_Record_Add_Successed"
// 添加记录失败
#define Notify_Record_Add_Failed                    @"Notify_Record_Add_Failed"
```
