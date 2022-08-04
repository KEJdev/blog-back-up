---
title: Anconda 가상환경 구축 후, env name 사라지는 현상
date:   2022-07-03 09:00:00 +0300
categories:  [Error, Python]
sitemap :
math: true
mermaid: true
changefreq : always
priority : 1.0
use_math: true
---

평소 keras만 쓰다가, 갑자기 pytorch를 써야되서 conda 환경 하나 팠다.  
그리고 몇칠 후, 다른 환경으로 가려고 평소 쓰던 환경으로 `conda activate [env name]`을 쳤는데, 안된다?   

급히  `conda env list` 명령어로 확인하니, 이름이 사라진 것을 보게 되었다.

<center><img src = "../../assets/images/env-name-missing.png" width="650" ></center>  

진짜 이름만 사라져서 당황...  
확인해보니, `[env name]` 에 직접 경로를 입력해주니까 해당 환경으로 들어가지는데, 그래도 근본적인 문제를 해결해야지.    


stackoverflow에서는 conda update 하라고 했는데, 나는 소용없었고, `conda config --add envs_dirs <path to envs>` 명령어로 해결하였다.  

<center><img src = "../../assets/images/env-name-missing2.png" width="650" ></center>  

좀더 찾아보니, 가끔 conda에서 업데이트나 여러 환경을 만들다가 발생할 수 있는 문제라고 한다.  
