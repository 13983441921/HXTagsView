# HXTagsView
HXTagsView是一款支持自动布局的标签tag

特性： 

-流式展示标签 

-可以配置标签的字体大小、颜色、边框颜色、边框弧度大小、边框的宽度、高度、间隔、外边距等 

-支持Auto layout 

-支持单行 多行显示 

-可以在UITableViewCell中良好展示 

-不使用UICollectionView. 

-支持多选操作,控制字段isMultiSelect

-支持搜索关键词标签加亮

# 效果展示


![image](https://github.com/huangxuan518/HXTagsView/blob/master/HXTagsView/xiaoguo.gif)
# 适用
本标签类适用于标签长度不确定等动态计算的标签显示需求,当然固定的也是适用的,该类有2种展示方式,一种是单行展示所有的标签,当超过一屏可以滚动显示,另一种是平铺展示所有标签,可以设置标签View的高度,当高度不够展示所有标签时,会滚动展示.

#参数说明图
![image](https://github.com/huangxuan518/HXTagsView/blob/master/HXTagsView/canshu.png)

# 使用示例
    /*单行是否滚动是标签的数量决定的,当标签排列在一起的长度大于屏幕的长度,则会滚动*/

    //单行不滚动 ===
    NSArray *tagAry = @[@"英雄联盟",@"穿越火线",@"地下城与勇士"];
    
    UILabel *titleLable = [[UILabel alloc] initWithFrame:CGRectMake(10, 70, 200, 20)];
    titleLable.text = @"单行不滚动";
    [self.view addSubview:titleLable];
    
    NSDictionary *propertyDic = @{@"type":@"0"};//可添加多个属性
    float height = [HXTagsView getTagsViewHeight:tagAry dic:propertyDic];
    HXTagsView *tagsView = [[HXTagsView alloc] initWithFrame:CGRectMake(0, titleLable.frame.origin.y+titleLable.frame.size.height+10, self.view.frame.size.width, height)];
    //以下2种方式皆可或者不设置,默认为单行
    tagsView.type = 0;
    //tagsView.propertyDic = propertyDic;
    [tagsView setTagAry:tagAry delegate:self];
    [self.view addSubview:tagsView];
    
    
    //单行滚动 ===
    tagAry = @[@"魔兽世界",@"梦幻西游",@"qq飞车",@"传奇",@"逆战",@"炉石传说",@"剑灵",@"qq炫舞",@"dota2",@"300英雄",@"笑傲江湖ol",@"剑网3",@"坦克世界",@"神武",@"龙之谷"];
    
    titleLable = [[UILabel alloc] initWithFrame:CGRectMake(10, tagsView.frame.origin.y+tagsView.frame.size.height+10, 200, 20)];
    titleLable.text = @"单行滚动";
    [self.view addSubview:titleLable];
    
    propertyDic = @{@"type":@"0"};
    height = [HXTagsView getTagsViewHeight:tagAry dic:propertyDic];
    tagsView = [[HXTagsView alloc] initWithFrame:CGRectMake(0, titleLable.frame.origin.y+titleLable.frame.size.height+10, self.view.frame.size.width, height)];
    //以下2种方式皆可或者不设置,默认为单行
    //tagsView.type = 0;
    tagsView.propertyDic = propertyDic;
    [tagsView setTagAry:tagAry delegate:self];
    [self.view addSubview:tagsView];
    
    
    /*多行是否滚动是HXTagsView的高度和标签计算出的高度比较后决定的,当HXTagsView的高度小于计算出的高度则自动滚动*/
    
    //多行不滚动 ===
    tagAry = @[@"冒险岛",@"反恐精英ol",@"魔域",@"诛仙",@"火影ol",@"问道",@"天龙八部",@"枪神纪",@"英魂之刃",@"勇者大冒险",@"nba 2k",@"上古世纪",@"跑跑卡丁车",@"传奇世界",@"劲舞团",@"激战2"];
    
    titleLable = [[UILabel alloc] initWithFrame:CGRectMake(10, tagsView.frame.origin.y+tagsView.frame.size.height+10, 200, 20)];
    titleLable.text = @"多行平铺";
    [self.view addSubview:titleLable];

    propertyDic = @{@"type":@"1"};
    height = [HXTagsView getTagsViewHeight:tagAry dic:propertyDic];
    tagsView = [[HXTagsView alloc] initWithFrame:CGRectMake(0, titleLable.frame.origin.y+titleLable.frame.size.height+10, self.view.frame.size.width, height)];
    tagsView.propertyDic = propertyDic;
    [tagsView setTagAry:tagAry delegate:self];
    [self.view addSubview:tagsView];
    
    
    //多行滚动 ===
    tagAry = @[@"蜀山ol",@"天下3",@"大话西游2",@"热血江湖",@"游戏人生",@"梦三国",@"流星蝴蝶剑",@"九阴真经",@"斗战神",@"奇迹mu",@"最终幻想14",@"宠物小精灵",@"天龙八部3",@"qq三国",@"倩女幽魂ol",@"御龙在天"];
    
    titleLable = [[UILabel alloc] initWithFrame:CGRectMake(10, tagsView.frame.origin.y+tagsView.frame.size.height+10, 200, 20)];
    titleLable.text = @"多行滚动";
    [self.view addSubview:titleLable];
    
    tagsView = [[HXTagsView alloc] initWithFrame:CGRectMake(0, titleLable.frame.origin.y+titleLable.frame.size.height+10, self.view.frame.size.width, 100)];
    tagsView.type = 1;
    [tagsView setTagAry:tagAry delegate:self];
    [self.view addSubview:tagsView];
    
    #pragma mark HXTagsViewDelegate
    /**
    *  tagsView代理方法
    *
    *  @param tagsView tagsView
    *  @param sender   tag:sender.titleLabel.text index:sender.tag
    */
    - (void)tagsViewButtonAction:(HXTagsView *)tagsView button:(UIButton *)sender {
       NSLog(@"tag:%@ index:%ld",sender.titleLabel.text,(long)sender.tag);
    }
    
# 用法说明
1. 当您选择平铺展示,并且设置了HXTagsView的高度,当您设置的高度有值并且小于标签的计算高度时,则滚动显示,否则全部平铺.当您设置的高度过大时,也会将高度更改为全铺显示.
2. 根据type来设置单行滚动还是多行不滚动,type=1,是平铺,0.为单行,默认单行
3. 标签还有很多属性,比如标签边框颜色,边框宽度,圆角等等,所有都可以自己定制,详见.h文件,完全可以满足您的需要
4. 高度计算+ (float)getTagsViewHeight:(NSArray *)ary dic:(NSDictionary *)dic计算,ary为标签字符串数组,字典里面装对应的更改的属性值进去,方法会根据传人的值进行高度计算,如果传nil则用默认值进行计算

# 自动高度计算方法说明
单行:第一个标签起点Y坐标+标签高度+标签间纵向间距

多行平铺:第一个标签起点Y坐标+平铺行数*(标签高度+标签间纵向间距)

# 博客交流
 http://blog.libuqing.com/
