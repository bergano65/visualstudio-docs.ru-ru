---
title: -Run (devenv.exe) | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- /run Devenv
- run Devenv switch
- applications [Visual Studio], running
- /r Devenv switch
- Devenv, /run switch
- r Devenv switch (/r)
ms.assetid: b1f22f9d-39a5-4918-8a2a-4b5c1e872665
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 98ec2d8be12b8d0dbf9f3283b31c62d90d55e7b4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571592"
---
# <a name="run-devenvexe"></a>/Run (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [-Run (devenv.exe)](https://docs.microsoft.com/visualstudio/ide/reference/run-devenv-exe).  
  
  
Компилирует и запускает указанный проект или указанное решение.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
devenv {/run|/r} {SolutionName|ProjectName}  
```  
  
## <a name="arguments"></a>Аргументы  
 `SolutionName`  
 Обязательно. Полный путь и имя для файла решения.  
  
 `ProjectName`  
 Обязательно. Полный путь и имя для файла проекта.  
  
## <a name="remarks"></a>Примечания  
 Компилирует и запускает указанный проект или указанное решение согласно параметрам, заданным для активной конфигурации решения. Этот параметр запускает интегрированную среду разработки (IDE), которая остается активной после завершения выполнения проекта или решения.  
  
-   Строки с пробелами заключаются в двойные кавычки.  
  
-   Сводные данные, включая ошибки, могут отображаться в окне **Команда** или в любом файле журнала, указанном с помощью параметра `/out`.  
  
## <a name="example"></a>Пример  
 Этот пример запускает решение `MySolution`, используя активную конфигурацию развертывания.  
  
```  
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"  
```  
  
## <a name="see-also"></a>См. также  
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [/Runexit (devenv.exe)](../../ide/reference/runexit-devenv-exe.md)   
 [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)   
 [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)   
 [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)



