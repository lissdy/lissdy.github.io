---
layout: post
title: "使用highcharts绘图"
date: 2013-12-16 19:50:07 +0800
comments: true
categories: 
---

环境准备:

Jquery库
注:Highcharts依赖于jQuery或MooTools,所以在inculde highcharts.js文件之前需要先include jQuery或者MooTools

1 下载地址:http://www.highcharts.com/download,
下载完成之后解压缩,提取highcharts.js文件,将其拷贝到项目目录/puclic/javascripts下

2 在测试页面中加入
        #/app/views/layouts/applications.html.erb
        <%= javascript_include_tag "jquery-1.4.2.min", "rails", "highcharts" %>
3 加入测试代码,最近空气较差,就模拟这个吧...
        #/app/views/layouts/applications.html.erb
        <%= javascript_include_tag "jquery-1.4.2.min", "rails", "highcharts" %>
        <div id="test_chart" style="width: 560px; height: 300px;"></div>
         <script type="text/javascript" charset="utf-8">
            $(function () {
                new Highcharts.Chart({
                    chart: { renderTo: 'test_chart' },  // 传入div id,指定chart位置
                    title: { text: '空气质量检测' },  // chart标题
                    xAxis: {
                        title: { text: '日期'},   //x轴标题
                        type: 'datetime'       //x轴数据类型
                    },
                    yAxis: {
                        title: { text: 'PM2.5'}    //y轴标题
                    },
                    series: [{
                        name: "北京",
                        pointInterval: <%= 1.day * 1000 %>,   //x轴间隔,单位是微秒
                        pointStart: <%= 1.weeks.ago.at_midnight.to_i * 1000 %>, //x轴起始
                        data: [100,200,500,700] //随便指定一个数组模拟一下
                    },
                        {
                            name: "上海",
                            pointInterval: <%= 1.day * 1000 %>,   //x轴间隔,单位是微秒
                            pointStart: <%= 1.weeks.ago.at_midnight.to_i * 1000 %>, //x轴起始
                            data: [200,100,600,300] //随便指定一个数组模拟一下
                        }
                    ]
                });
            });
</script>


4 刷新页面,查看结果
![image](file:///home/lissdy/markdown_image/test.png)



