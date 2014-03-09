---
layout: post
title: "NSArray"
date: 2014-03-08 21:50:18 +0800
comments: true
categories: 
---
{% codeblock lang:objc %}
NSArray的两个限制
1.只能存储Objective-C的对象
2.不能存储nil (对象的零值或NULL值)
		 
//创建数组 的两种方式, 后一种不必以nil结尾
NSArray* array = [NSArray arrayWithObjects:@"one",@"two",@"Three",nil];
//添加nil代表列表结束,这就是为什么不能在数组中存储nil的一个原因
NSArray* array2 =@[@"one",@"two",@"three"];
//循环输出数组中元素内容两种方式
for(NSInteger i =0; i< [array count]; i++) 
{
	NSLog(@"%@",array2[i]);
}
//[array arrayByAddingObject:@"FOURR"];   //实际无法添加,NSArray不可改变
//array[0]=@"four";   //不可改变
		
NSArray创建的是不可变对象的数组,它是固定的,既不能添加任何元素也不能删元素.
		
for(NSInteger i =0; i< [array count]; i++) 
{
	NSLog(@"%@",[array objectAtIndex:i]);
}
//切分数组
NSString*string =@"c:c++:java:objective-c:php";
NSArray*chunks = [string componentsSeparatedByString:@":"];
		
for(NSInteger i =0; i< [chunks count]; i++) 
{
	NSLog(@"%@",chunks[i]);
}
		
//合并数组为字符串
string = [chunks componentsJoinedByString:@":-("];
NSLog(@"%@",string);
		
//可变数组NSMutableArray通过类方法arrayWithCapacity来创建新的可变数组
//+(id) arrayWithCapacity: (NSInteger) numItems
NSMutableArray* array4 = [NSMutableArray arrayWithCapacity:20];
//添加数组对象
[array4 addObject:@"hello"];  //索引为0
[array4 addObject:@"world"];  //索引为1
[array4 addObject:@"你好世界"]; //索引为2
for(NSInteger i =0; i<[array4 count]; i++) 
{
NSLog(@"%@",array4[i]);
}
//删除数组对象
[array4 removeObject:@"hello"];
//删除hello后,数组索引会自动更新,world的索引将为0你好世界的索引为1
[array4 removeObjectAtIndex:0];
for(NSInteger i =0; i<[array4 count]; i++)
{
	NSLog(@"%@",array4[i]);
}
//值得注意的是:可变数组没有快速创建数组的方法,类似
//NSArray * array2 = @[@"one",@"two",@"three"];
{% endcodeblock %}