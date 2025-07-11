### 项目背景：

        随着互联网与通信技术的高速发展，学习资源的建设与共享呈现出新的发展趋势，各种网课、直播课等层出不穷，各种在线教育平台和学习应用纷纷涌现。受新冠疫情影响，网络平台成为“互联网+教育”成果的重要展示阵地。因此，如何根据教育平台的线上用户信息和学习信息，通过数据分析为教育平台和用户提供精准的课程推荐服务就成为线上教育的热点问题。 根据已有数据，为平台制定综合的线上课程推荐策略，以便更好地服务线上用户。

### 数据源

        数据来自于公开数据

### 数据说明

        共 三 张 数 据 表 ， 分 别 为 users.csv （ 用 户 信 息 表 ）、study_information.csv（学习详情表）和 login.csv（登录详情表），分别如表 1、表 2和表 3所示。

        表 1 users.csv 字段说明

| 字段名                    | 描述      |
|:----------------------:|:-------:|
| user_id                | 用户 id   |
| registration_time      | 注册时间    |
| recently_logged        | 最近访问时间  |
| learn_time             | 学习时长（分） |
| number_of_classes_join | 加入班级数   |
| number_of_classes_out  | 退出班级数   |
| school                 | 用户所属学校  |

        表 2 study_information.csv 字段说明

| 字段名              | 描述      |
|:----------------:|:-------:|
| user_id          | 用户 id   |
| course_id        | 课程 id   |
| course_join_time | 加入课程的时间 |
| learn_process    | 学习进度    |
| price            | 课程单价    |

        表 3 login.csv 字段说明

| 字段名         | 描述    |
|:-----------:|:-----:|
| user_id     | 用户 id |
| login_time  | 登录时间  |
| login_place | 登录地址  |

# 

### 分析任务及思路

        一、数据预处理

        1、理解各字段的含义， 进行缺失值、重复值等方面的必要处理。

        2、对用户信息表中 recently_logged 字段的“--”值进行必要的处理。

        二、平台用户活跃度分析

        1、绘制各省份与各城市平台登录次数热力地图，并分析用户分布情况。

        2、绘制工作日与非工作日各时段的用户登录次数柱状图，并分析用户活跃的主要

              时间段。

        3、计算平台用户的流失率

              𝑇<sub>end</sub>为数据观察窗口截止时间， 𝑇<sub>𝑖</sub>为用户 i 的最近访问时间， 𝜎<sub>𝑖 </sub>= 𝑇<sub>end</sub> - 𝑇<sub>𝑖</sub>，

             若𝜎<sub>𝑖</sub> > 90 天，则称用户 i 为流失用户。

        4、分析平台用户的活跃度，为该教育平台的线上管理决策提供建议。

        三、线上课程推荐

        1、根据用户参与学习的记录，统计每门课程的参与人数，计算每门课程的受欢迎程

              度，列出最受欢迎的前 10 门课程，并绘制相应的柱状图。

                                                                $\gamma_i = \frac{Q_i - Q_{\min}}{Q_{\max} - Q_{\min}}$    

              其中， 𝛾<sub>𝑖</sub>为第 i 门课程的受欢迎程度， 𝑄<sub>𝑖</sub>为参与第 i 门课程学习的人数，

              𝑄<sub>max</sub>和𝑄<sub>min</sub>分别为所有课程中参与人数最多和最少的课程所对应的人数

        2、根据用户选择课程情况，构建用户和课程的关系表（二元矩阵），

              使用基于物品的协同过滤算法计算课程之间的相似度，并结合用户已选课程的记

              录，为总学习进度最高的 5 名用户推荐 3 门课程

### 代码及结果

基于协同过滤算法的课程推荐.html
