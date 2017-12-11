---
title: "-Rebuild (devenv.exe) | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Devenv, /rebuild switch
- rebuild Devenv switch (/rebuild)
- projects [Visual Studio], rebuilding
- /rebuild Devenv switch
- applications [Visual Studio], rebuilding
ms.assetid: c5a8a4bf-0e2b-46eb-a44a-8aeb29b92c32
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: fcabe7b1ce4130eb52369ff9f16900b1979b8582
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="rebuild-devenvexe"></a>/Rebuild (devenv.exe)
Удаляет и затем выполняет сборку заданной конфигурации решения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
devenv SolutionName /rebuild SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]  
```  
  
## <a name="arguments"></a>Аргументы  
 `SolnConfigName`  
 Обязательный. Имя конфигурации решения, которая будет применяться для перестроения решения, указанного в `SolutionName`.  
  
 `SolutionName`  
 Обязательный. Полный путь и имя для файла решения.  
  
 /project `ProjName`  
 Необязательно. Путь и имя для файла проекта в решении. Можно ввести относительный путь из папки `SolutionName` к файлу проекта, отображаемое имя проекта либо полный путь и имя для файла проекта.  
  
 /projectconfig `ProjConfigName`  
 Необязательно. Имя конфигурации сборки проекта, которая применяется при перестроении указанного `/project`.  
  
## <a name="remarks"></a>Примечания  
  
-   Этот параметр выполняет те же функции, что и команда меню **Перестроить решение** в интегрированной среде разработки (IDE).  
  
-   Строки с пробелами заключаются в двойные кавычки.  
  
-   Сводные данные для удаления и сборки, включая ошибки, могут отображаться в окне **Команда** или любом файле журнала, указанном с помощью параметра `/out`.  
  
## <a name="example"></a>Пример  
 В этом примере выполняется удаление и перестроение проекта `CSharpWinApp` с помощью конфигурации сборки `Debug` в конфигурации решения `Debug` `MySolution`.  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /rebuild Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug   
```  
  
## <a name="see-also"></a>См. также  
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)   
 [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)   
 [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)