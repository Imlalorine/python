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


