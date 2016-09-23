# Snapshot
========
ThoughtWorks 作业
--------


###项目整体结构

   * 注意：该项目的输入数据的格式是基于不同时刻的唯一id所代表的用例之间要空一行，事例文件在根路径 resource/input.txt

#####整个项目共分为四个包

* 实体层（包括三个实体）： 
```
    * class Point:定义了坐标的结构,包含两个变量<x,y>
    * class Position:对Point的封装，包括上次的位置和当前的位置
    * class Snapshot:记录快照信息，包括（id, date, Map<String,Position> animalMap）
```
* 数据访问（I/O）层：
```
    * InputReader:读取 resource/input.txt 文件中的数据保存在historyData中。
```
* 处理层（入口）:
```
    * private static List<Snapshot> retreatment(String historyData,Set<String> nameSets):对输入的字符串做预处理，
并保存在bean实体中
    * private static String validate(List<Snapshot> snapshots, String id, List<String> names)：验证传入的输入数
据内容是否前后矛盾
    * public static String getSnapShot(String historyData, String id)：处理函数，负责获取动物的分布快照
```
* 单元测试层:
```
    * SnapshotTest：对每个接口进行测试（每个方法的测试是基于resource/input.txt文件）
```
    
###测试

####单元测试

#####接口功能测试
* 用来保证接口功能的正确性

#####边界条件测试
* 1.输入没有赋值（如为NULL）
* 2.输入应该为字符串:空字符串;
* 3.时间格式错误，提示错误：Invalid format;
* 4.位置数据前后矛盾，提示错误：Conflict found at id

#####所有独立执行通路测试：保证每一条代码，每个分支都经过测试
* 代码覆盖率
    * 语句覆盖：保证每条语句都执行了<br>
    * 判定覆盖：保证每一个分支都执行到<br>
    * 条件覆盖：保证每一个条件都覆盖到true和false（即if、while中的条件语句）<br>
    * 路径覆盖：保证每一个路径都覆盖到<br>

####系统整体测试
* 1、构造正确的测试用例：输出预期结果
* 2、构造格式错误的用例：提示不合法
* 3、构造矛盾的测试用例：提示冲突

