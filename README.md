![CLEVER DATA GIT REPO](https://raw.githubusercontent.com/LiCongMingDeShujuku/git-resources/master/0-clever-data-github.png "李聪明的数据库")

# 查找兼容性级别和SQL版本支持
#### Find Compatibility Levels And SQL Version Support
**发布-日期: 2017年06月23日 (评论)**

![#](images/find-compatibility-leveles-and-sql-version-support-a.png?raw=true "#")

## Contents

- [中文](#中文)
- [English](#English)
- [SQL Logic](#Logic)
- [Build Info](#Build-Info)
- [Author](#Author)
- [License](#License) 


## 中文
这是一些显示了兼容性级别（Compatibility_Level）以及不同SQL版本的支持类型的快速的SQL逻辑（logic）。

## English
Here’s some quick SQL logic that shows the Compatibility_Level with the type of support from the different SQL Versions out there.

---
## Logic
```SQL
--find all compatibility levels per database and see what other SQL versions support it.
查找每个数据库的所有兼容级别，并查看其他SQL版本是否支持它。
 
use master;
set nocount on
 
select
    'server_name'       = @@servername
,   'database_name'     = upper(sd.name)
,   'compatability_level'   =
                case cast(sd.compatibility_level as varchar(255))
                    when 60     then '60 (SQL 6.0)      Works only on SQL 6'
                    when 65     then '65 (SQL 6.5)      Works only on SQL 6.5'
                    when 70     then '70 (SQL 7.0)      Works only on SQL 7'
                    when 80     then '80 (SQL 2000)     Works only on SQL 2000'
                    when 90     then '90 (SQL 2005)     Works on SQL 2005, 2000'
                    when 100    then '100 (SQL 2008)    Works on SQL 2008R2, 2005'
                    when 110    then '110 (SQL 2012)    Works on SQL 2012, 2008R2, 2005'
                    when 120    then '120 (SQL 2014)    Works on SQL 2014, 2012, 2008R2'
                    when 130    then '130 (SQL 2016)    Works on SQL 2016, 2014, 2012, 2008R2'
                    when 140    then '140 (SQL 2017)    Works on SQL 2017, 2016, 2014, 2012, 2008R2'
                end
from
    sys.databases sd
where
    database_id <> 2
order by
    sd.name
,   sd.compatibility_level desc


```
请查看Microsoft文档以来验证：
https://docs.microsoft.com/en-us/sql/t-sql/statements/alter-database-transact-sql-compatibility-level

Feel free to check Microsoft Documentation to verify found here: https://docs.microsoft.com/en-us/sql/t-sql/statements/alter-database-transact-sql-compatibility-level

[![WorksEveryTime](https://forthebadge.com/images/badges/60-percent-of-the-time-works-every-time.svg)](https://shitday.de/)

## Build-Info

| Build Quality | Build History |
|--|--|
|<table><tr><td>[![Build-Status](https://ci.appveyor.com/api/projects/status/pjxh5g91jpbh7t84?svg?style=flat-square)](#)</td></tr><tr><td>[![Coverage](https://coveralls.io/repos/github/tygerbytes/ResourceFitness/badge.svg?style=flat-square)](#)</td></tr><tr><td>[![Nuget](https://img.shields.io/nuget/v/TW.Resfit.Core.svg?style=flat-square)](#)</td></tr></table>|<table><tr><td>[![Build history](https://buildstats.info/appveyor/chart/tygerbytes/resourcefitness)](#)</td></tr></table>|

## Author

- **李聪明的数据库 Lee's Clever Data**
- **Mike的数据库宝典 Mikes Database Collection**
- **李聪明的数据库** "Lee Songming"

[![Gist](https://img.shields.io/badge/Gist-李聪明的数据库-<COLOR>.svg)](https://gist.github.com/congmingshuju)
[![Twitter](https://img.shields.io/badge/Twitter-mike的数据库宝典-<COLOR>.svg)](https://twitter.com/mikesdatawork?lang=en)
[![Wordpress](https://img.shields.io/badge/Wordpress-mike的数据库宝典-<COLOR>.svg)](https://mikesdatawork.wordpress.com/)

---
## License
[![LicenseCCSA](https://img.shields.io/badge/License-CreativeCommonsSA-<COLOR>.svg)](https://creativecommons.org/share-your-work/licensing-types-examples/)

![Lee Songming](https://raw.githubusercontent.com/LiCongMingDeShujuku/git-resources/master/1-clever-data-github.png "李聪明的数据库")

