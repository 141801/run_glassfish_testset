## 背景
在对glassfish的源码进行修正（比如jdk11移植）之后，需要通过glassfish自带的最基本的测试集<p>
glassfish团队给出了一个基本的测试集，源码在glassfish/appserver/test里面。<p>
[glassfish源码](https://github.com/eclipse-ee4j/jakartaee-tck)

## 测试集
[测试用例一览 ](https://github.com/eclipse-ee4j/glassfish/blob/master/Jenkinsfile)
 
## 步骤

## /glassfish项目build
    $git clone https://github.com/javaee/glassfish.git
    $cd glassfish
    $export JAVA_HOME=/jh/jdk1.8.0_211  (JAVA HOMNE 设定)
    $export PATH=$JAVA_HOME/bin:$PATH  
    $mvn clean install -Dmaven.test.skip=true

## ant 安装
    $yum install ant #version 1.10.5
    $export ANT_HOME=/usr/share/ant
    $export PATH=$ANT_HOME/bin:$PATH
    
## 环境变量 
    $export APS_HOME=/root/glassfish/appserver/tests/appserv-tests  （演示中glassfish安装在root下面）
    $export WORKSPACE=/root/glassfish/workspace
    $export S1AS_HOME=/root/glassfish/appserver/distributions/glassfish/target/stage/glassfish5/glassfish
    $export TEST_RUN_LOG=/root/glassfish/workspace/tests_run.log
## glassfish.zip copy
    $cp glassfish.zip  /root/glassfish/workspace/bundles/  （在glassfish下面新建 workspace/bundles 文件夹）

## 测试开始
    $cd /glassfish
    $./appserver/tests/gftest.sh run_test connector_group_2 （本次演示只对connector_group_2测试）
    
##测试结果
 结果在/root/glassfish/workspace/results里面表示 <p>
 ![additional](https://i.ibb.co/fX4f941/glassfishtest1.png "")　<p>

 
##查看测试报告
可以用浏览器打开\test_results.html文件查看报告内容（下面截图是在jdk11上做移植的报告，所以只有8个测试pass）<p>
 ![additional](https://i.ibb.co/sgcZVMJ/glassfishtest2.png "")　<p>
※在jdk11上做testsuite时，因为derby的问题要添加classpath，本次演示不涉及jdk11的内容。

