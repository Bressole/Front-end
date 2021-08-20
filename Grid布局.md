# Grid布局

Flex布局是轴线布局，可以看作是一维布局；Grid布局是将容器分成“行”和“列”，产生单元格，可以看作是二维布局。

## 1.容器和项目

容器：采用网格布局的区域；

项目：容器的顶层子元素；

Grid布局只对项目生效。

## 2.行和列，网格线

水平网格线划分出行，垂直网格线划分出列。

## 3.display属性

设为网格布局以后，容器子元素的float将失效。

## 4.行列设置属性

grid-template-columns：定义每一列的列宽；

grid-template-rows：定义每一行的行高；

grid-row-gap：设置行距

grid-column-gap：设置列距

grid-gap：是grid-row-gap和grid-column-gap的合并简写方式。

方括号[]可以指定每一根网格线的名称，允许同一根线有多个名字。

```
.container{
	display:grid;
	grid-template-columns:[c1]100px [c2]100px [c3]100px; //33.33% 33.33% 33.33%;
	grid-template-rows:100px 100px 100px; //33.33% 33.33% 33.33%;
}
```

### repeat()

repeat()接收两个参数，第一个参数是重复的次数，第二个参数是所要重复的值。

### auto-fill

可以使每一行或每一列容纳尽可能多的单元格，auto-fill关键字表示自动填充，直到容器不能放置更多的列。

### fr

表示比例关系，如果两列的宽度分别为1fr和2fr，则表示后者是前者的两倍。

### minmax

定义了一个范围，接受两个参数，即最小值和最大值。

### auto

表示浏览器自己决定长度

## 5.grid-template-areas

该属性用于定义区域。

```
.container{
	display:grid;
	grid-template-areas: 'a b c'
                         'd e f'
                         'g h i';
}
```

该代码表示划分了9个单元格，并分别命名a~i。

```
grid-template-areas: 'a a a'
                      'b b b'
                      'c c c';
```

该代码表示将9个单元格分成a、b、c三个区域，即合并单元格。

如果某些区域不需要利用，则使用“点”（.）表示。







