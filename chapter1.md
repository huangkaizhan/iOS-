# 控件规范

### 公用控件
* 命名：遵守本身控件的命名规则，其后加_lib --> AvatarImageView_lib


### View
* 命名：View结尾，如BackView
* 事件：控件名 + 事件名，如 BackViewDidTap:, 注意：事件描述的是动作名，而不是做的功能名称，比如这个事件名有可能命名为changeAvatar这样的名称，这样并不符合面向对象思想

### 图片
* 命名：imageView结尾，如BBAvatarImageView
* 事件：控件名 + 事件名，如 avatarImageViewDidTap:

### 文字
* 命名：Label结尾，如nameLabel
* 颜色：通过宏设置，不写RGB（），有可能以后会换肤
* 字体：跟颜色一样，有可能更换字体，通过宏设置

### 按钮
* 命名：Button结尾，如backButton
* 事件：控件名 + 事件名，如 backButtonDidClicked:


### 输入框
* 命名：TextField结尾，如nameTextField


### 输入框
* 命名：TextField结尾，如nameTextField


###其他控件
* 命名基本上面一直，结尾统一加控件后缀