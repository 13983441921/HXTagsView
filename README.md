# HXTagsView
HXTagsView是一款支持自动布局的标签tag

特性： 

-流式展示标签 

-可以配置标签的字体大小、颜色、边框颜色、边框弧度大小、边框的宽度、高度、间隔、外边距、标签内部左右间距等 

-支持单行 多行滚动显示 多行不滚动显示 

-支持多选操作,控制字段isMultiSelect

-支持搜索关键词标签加亮以及关键词颜色自定义,设置key字段的值即可

-标签样式更改tagAttribute

-标签布局计算属性更改layout,即更改HXTagCollectionViewFlowLayout的属性，包括.scrollDirection .itemSize .minimumInteritemSpacing .minimumLineSpacing .sectionInset等属性，用法同UICollectionViewFlowLayout;

# 效果展示


![image](https://github.com/huangxuan518/HXTagsView/blob/master/HXTagsView/xiaoguo.gif)
# 适用
本标签类适用于标签长度不确定等动态计算的标签显示需求

# 使用示例

    //单行不滚动 ===
    NSArray *tagAry = @[@"英雄联盟",@"穿越火线",@"地下城与勇士"];


    HXTagsView *tagsView = [[HXTagsView alloc] initWithFrame:CGRectMake(0, 300, self.view.frame.size.width, 52)];
    tagsView.tags = tagAry;
    [self.view addSubview:tagsView];

![image](https://github.com/huangxuan518/HXTagsView/blob/master/HXTagsView/danhangbugundongxiaoguo.gif)
    
    //单行滚动 ===
    NSArray *tagAry = @[@"魔兽世界",@"梦幻西游",@"qq飞车",@"传奇",@"逆战",@"炉石传说",@"剑灵",@"qq炫舞",@"dota2",@"300英雄",@"笑傲江湖ol",@"剑网3",@"坦克世界",@"神武",@"龙之谷"];
    
    HXTagsView *tagsView = [[HXTagsView alloc] initWithFrame:CGRectMake(0, 300, self.view.frame.size.width, 52)];
    tagsView.tags = tagAry;
    [self.view addSubview:tagsView];

![image](https://github.com/huangxuan518/HXTagsView/blob/master/HXTagsView/danhanggundongxiaoguo.gif)
    
    //多行不滚动单选 ===
    NSArray *tagAry = @[@"冒险岛",@"反恐精英ol",@"魔域",@"诛仙",@"火影ol",@"问道",@"天龙八部",@"枪神纪",@"英魂之刃",@"勇者大冒险",@"nba 2k",@"上古世纪",@"跑跑卡丁车",@"传奇世界",@"劲舞团",@"激战2"];
    
    HXTagsView *tagsView = [[HXTagsView alloc] initWithFrame:CGRectMake(0, 300, self.view.frame.size.width, 52)];
    tagsView.tags = tagAry;
    tagsView.layout.scrollDirection = UICollectionViewScrollDirectionVertical;
    [self.view addSubview:tagsView];

![image](https://github.com/huangxuan518/HXTagsView/blob/master/HXTagsView/duohangpingpudan1xiaoguo.gif)
    
    //多行滚动单选 ===
    NSArray *tagAry = @[@"蜀山ol",@"天下3",@"大话西游2",@"热血江湖",@"游戏人生",@"梦三国",@"流星蝴蝶剑",@"九阴真经",@"斗战神",@"奇迹mu",@"最终幻想14",@"宠物小精灵",@"天龙八部3",@"qq三国",@"倩女幽魂ol",@"御龙在天"];
    
    HXTagsView *tagsView = [[HXTagsView alloc] initWithFrame:CGRectMake(0, 300, self.view.frame.size.width, 52)];
    tagsView.tags = tagAry;
    tagsView.layout.scrollDirection = UICollectionViewScrollDirectionVertical;
    tagsView.layout.isMultiLineRoll = YES;
    [self.view addSubview:tagsView];

![image](https://github.com/huangxuan518/HXTagsView/blob/master/HXTagsView/duohanggundongxiaoguo.gif)

    //多行不滚动多选
    NSArray *tagAry = @[@"冒险岛游戏",@"反恐精英ol游戏",@"游戏魔域",@"诛游戏仙",@"火游戏影ol游戏",@"问游戏道",@"天游戏龙游戏八游戏部",@"枪神纪游戏",@"英魂之游戏刃",@"勇者游戏大冒险",@"nba 游戏2k",@"上古世纪游戏",@"游戏跑跑卡游戏丁车",@"传奇世界游戏",@"劲舞游戏团",@"激游戏战2"];
    
    HXTagsView *tagsView = [[HXTagsView alloc] initWithFrame:CGRectMake(0, 300, self.view.frame.size.width, 52)];
    tagsView.tags = tagAry;
    tagsView.layout.scrollDirection = UICollectionViewScrollDirectionVertical;
    tagsView.isMultiSelect = YES;
    [self.view addSubview:tagsView];

![image](https://github.com/huangxuan518/HXTagsView/blob/master/HXTagsView/duohangpingpudanxiaoguo.gif)

    //多行不滚动有关键字多选
    NSArray *tagAry = @[@"冒险岛游戏",@"反恐精英ol游戏",@"游戏魔域",@"诛游戏仙",@"火游戏影ol游戏",@"问游戏道",@"天游戏龙游戏八游戏部",@"枪神纪游戏",@"英魂之游戏刃",@"勇者游戏大冒险",@"nba 游戏2k",@"上古世纪游戏",@"游戏跑跑卡游戏丁车",@"传奇世界游戏",@"劲舞游戏团",@"激游戏战2"];

    HXTagsView *tagsView = [[HXTagsView alloc] initWithFrame:CGRectMake(0, 300, self.view.frame.size.width, 52)];
    tagsView.tags = tagAry;
    tagsView.layout.scrollDirection = UICollectionViewScrollDirectionVertical;
    tagsView.isMultiSelect = YES;
    tagsView.key = @"游戏";
    [self.view addSubview:tagsView];

![image](https://github.com/huangxuan518/HXTagsView/blob/master/HXTagsView/duohangpingpuxiaoguo.gif)
    
# 选择回调方法
    
    self.tagsView.completion = ^(NSArray *selectTags,NSInteger currentIndex) {
        NSLog(@"selectTags:%@ currentIndex:%ld",selectTags, (long)currentIndex);
    };
    
# 刷新方法

- (void)reloadData;

更改参数后，请执行reloadData

# 博客交流
 http://blog.libuqing.com/
