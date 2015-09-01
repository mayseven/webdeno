将蓝缘maven版本修改为普通web版本。ide:myeclipse
说明：项目已经部署好。以下记录仅作为想如何转换练习童鞋的参考。其中又遗漏的而运行不起来的，请自行百度解决。
1.将蓝缘中下载得到的maven各模块中src/main/java目录下自com包移入myeclipse web项目的src下；将lanyuan-web下webapp目录下除web-inf的项移入到webroot下；将lanyuan-webwebapp下的web-inf下的项移入到web-inf。注：lanyuan-web下的resources移入到新项目中的src下
2.jar来源
	使用maven部署不成功，使用myeclipse使用 run as 运行部署失败的maven项目 ->maven install 得到的war包，jar包就是从里面提取的
3.去掉lib目录下的servelet的jar，jstl的jar
4.添加myeclipse系统自带的jstljar
5.添加jdk中md5的编码依赖。该包为jdk的 jre/lib/rt.jar
6.去掉所有jsp中关于 public及""中的内容，只保留!DOCTYPE html
7.去掉所有jsp中关于命名空间的声明，只保留 <html>
8.xml:修改web.xml等xml文件中涉及classpath等的地方，添加上resources/；在web.xml中声明log4j的使用；修改web.xml中关于servelet dtd引用，由2.5改为3.0
9.sql:添加res_roles中对于root的权限，将所有资源都赋予root。原包中只有系统基础管理一项，无法使用root进行更多的操作
10.以上操作完部署并运行还报错，请重新编译项目。选中项目->project,勾选build auto项，然后clean(该操作是本人在项目部署完后mybatis代理查询找不到accountMapper从base中的继承来的queryAll方法进行的操作)
