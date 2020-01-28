![MIKES DATA WORK GIT REPO](https://raw.githubusercontent.com/mikesdatawork/images/master/git_mikes_data_work_banner_01.png "Mikes Data Work")        

# Get All Servers Involved In A Mirror Configuration With SQL
**Post Date: October 13, 2015**        



## Contents    
- [About Process](##About-Process)  
- [SQL Logic](#SQL-Logic)  
- [Build Info](#Build-Info)  
- [Author](#Author)  
- [License](#License)       

## About-Process

<p>Here's some quick sql logic to show you the Servers involved in a database mirror. This does not show you which is Principal or Mirror, but only the server names. The query shows "Server1" and "Server2" plus the "Witness", but that it. It's meant to give you the Server names.</p>      


## SQL-Logic
```SQL
use master;
set nocount on
select
[Server1] = @@servername
,   [Server2] = replace(reverse(right(reverse(mirroring_partner_name), len(mirroring_partner_name) - charindex('.',reverse(mirroring_partner_name),10) + 0)), 'TCP://', '') ,   [Witness] = case
mirroring_witness_name
when '' then 'NOT CONFIGURED'
else replace(reverse(right(reverse(mirroring_witness_name), len(mirroring_witness_name) - charindex('.',reverse(mirroring_witness_name),10) + 0)), 'TCP://', '') end
from
master.sys.database_mirroring
where
mirroring_partner_name is not null
```


[![WorksEveryTime](https://forthebadge.com/images/badges/60-percent-of-the-time-works-every-time.svg)](https://shitday.de/)

## Build-Info

| Build Quality | Build History |
|--|--|
|<table><tr><td>[![Build-Status](https://ci.appveyor.com/api/projects/status/pjxh5g91jpbh7t84?svg?style=flat-square)](#)</td></tr><tr><td>[![Coverage](https://coveralls.io/repos/github/tygerbytes/ResourceFitness/badge.svg?style=flat-square)](#)</td></tr><tr><td>[![Nuget](https://img.shields.io/nuget/v/TW.Resfit.Core.svg?style=flat-square)](#)</td></tr></table>|<table><tr><td>[![Build history](https://buildstats.info/appveyor/chart/tygerbytes/resourcefitness)](#)</td></tr></table>|

## Author

[![Gist](https://img.shields.io/badge/Gist-MikesDataWork-<COLOR>.svg)](https://gist.github.com/mikesdatawork)
[![Twitter](https://img.shields.io/badge/Twitter-MikesDataWork-<COLOR>.svg)](https://twitter.com/mikesdatawork)
[![Wordpress](https://img.shields.io/badge/Wordpress-MikesDataWork-<COLOR>.svg)](https://mikesdatawork.wordpress.com/)


## License
[![LicenseCCSA](https://img.shields.io/badge/License-CreativeCommonsSA-<COLOR>.svg)](https://creativecommons.org/share-your-work/licensing-types-examples/)

![Mikes Data Work](https://raw.githubusercontent.com/mikesdatawork/images/master/git_mikes_data_work_banner_02.png "Mikes Data Work")

