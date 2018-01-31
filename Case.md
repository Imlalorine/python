# python
# python 学习中的练习


#! /usr/bin/env python
# coding: utf-8
import urllib2, json, sys

web = "https://api.douban.com/v2/movie/in_theaters"
content= urllib2.urlopen(web).read()
content = content.encode('utf-8').decode('unicode_escape')
data = json.loads(content)
number = int (data ['count'])
print number
movies = data['subjects']
movie = {} #初始化一个空字典
result = ''
for i in range(0, number):
    score = str(movies[i]['rating']['average'])
    movie[i] = [movies[i]['title'].encode('utf-8'), str(score)] 
    line = str(i+1) + '. ' + ' '.join(movie[i]) + '\n'
    result += line

f = open ("movie.txt", 'w')
f.write(result)
f.close()

print "\n"


# 从n个数字里抓取m个数值
from random import randint
n = 100
list_1 = range (0, n)
print list_1
for i in range (0, 23):
    j = randint (0, n)
    print list_1 [j]
    del list_1[j]
    n -= 1
    
    
#抽取随机数后，输出列表
from random import randint
n = 100
list_1 = range (0, n)
result = []
f = open('随机数.txt','w')
for i in range (0, 23):
    j = randint (0, n)
    print list_1 [j]
    n -= 1
    c = str(list_1 [j])
    result.append(c)
    f.write (c + ' ')
    del list_1[j]
f.close



from random import randint
#数据的排列
list_1 = [4, 7, 3, 4, 1, 9, 8, 3, 7] #
print sorted(list_1)#按从小到大排列
print sorted(set(list_1)) #排除重复
print sorted(set(list_1), key=list_1.index) #去除重复后按从小到达排列


#从字串中找出数字,并以字符串输出
import re
test = 'aAsmr3idd4bgs7Dlsf9eAF'
print ''.join(re.findall('\d',test))
print ''.join(i for i in test if i.isdigit())
print filter(lambda x: x.isdigit(), test)


#抓取某文件夹（和子文件夹）中的.txt文件
import fnmatch
import os
path = '/Users/zhengshucheng/Documents/python/python'
text_list = []
for parent, dirnames, filename in os.walk(path):#parent 是文件或者文件夹的上一层， dirnames指遍历到文件夹，则内容放到dirnames里；

# 如果遍历到文件，则文件名字放到filename里
    print filename
    for filenames in filename:
        text_list.append(filenames)
    list_1 =  fnmatch.filter(text_list, '*.txt')
print '\n'
lsit_2 = sorted(set(list_1), reverse=True)
print lsit_2


#输入一个数字，输出相应数量的斐波那契数列
#coding=utf-8
print "你想要斐波那契数列的前几项(不得小于3)"
n = input()
if n < 3:
print 1
if n == 2:
print 1
if n > 2:
print 1
print 1
x = 1
y = 1
i = 2
while i < n:
z = x + y
y = x
x = z
i += 1
print z


#但是它输入的是等腰直角三角形，而不是顶点在中间的那类我们习惯的等腰三角形。
print '输入你要的等腰三角形的高度'
x = input()
for i in range (0,x):
    for j in range (0, i+1):
        print '*  ',
    print '\n'
#需要进一步改善

#改进后的程序
#coding=utf-8
print '输入你要的等腰三角形的高度'
x = input()
for i in range (0,x):
    for k in range (0, x-i-1):  #为保持一个*时在中间，需要在前面加入相应的space。加入空格的个数为 高度的一半。为了使高度为 偶数是无法输入半个空格，将其空格数加倍。
        print ' ',
    for j in range (0, i+1):
        print '*  ',
        print '\n'
        
        
#输出乘法表
for i in range(1,10):
    for j in range (1, i+1):
        print j, '*', i, '=', i *j

