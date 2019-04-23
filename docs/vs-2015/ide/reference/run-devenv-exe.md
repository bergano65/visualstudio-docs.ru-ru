---
title: -Run (devenv.exe) | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
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
manager: jillfra
ms.openlocfilehash: 8f941aaff6b4f5f97a298549e91c29ffb19e84ea
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59667528"
---
# <a name="run-devenvexe"></a>/Run (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Компилирует и запускает указанный проект или указанное решение.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
devenv {/run|/r} {SolutionName|ProjectName}  
```  
  
## <a name="arguments"></a>Аргументы  
 `SolutionName`  
 Обязательный. Полный путь и имя для файла решения.  
  
 `ProjectName`  
 Обязательный. Полный путь и имя для файла проекта.  
  
## <a name="remarks"></a>Примечания  
 Компилирует и запускает указанный проект или указанное решение согласно параметрам, заданным для активной конфигурации решения. Этот параметр запускает интегрированную среду разработки (IDE), которая остается активной после завершения выполнения проекта или решения.  
  
-   Строки с пробелами заключаются в двойные кавычки.  
  
-   Сводные данные, включая ошибки, могут отображаться в окне **Команда** или в любом файле журнала, указанном с помощью параметра `/out`.  
  
## <a name="example"></a>Пример  
 Этот пример запускает решение `MySolution`, используя активную конфигурацию развертывания.  
  
```  
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"  
```  
  
## <a name="see-also"></a>См. также раздел  
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [/Runexit (devenv.exe)](../../ide/reference/runexit-devenv-exe.md)   
 [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)   
 [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)   
 [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
