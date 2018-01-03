---
title: "-Deploy (devenv.exe) | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Devenv, /deploy switch
- deploy Devenv switch
- deploying applications [Visual Studio], after build
- /deploy Devenv switch
ms.assetid: e47c8723-df08-4645-aa2d-0c956e7ccca2
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 2f7697217d59d430e2b4661548b7f922f8fd8c95
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="deploy-devenvexe"></a>/Deploy (devenv.exe)
Развертывает решения после сборки или перестроения. Применяется только к проектам с управляемым кодом.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
devenv SolutionName /deploy SolnConfigName [/project ProjName] [/projectconfig ProjConfigName] [/out LogFileName]  
```  
  
## <a name="arguments"></a>Аргументы  
 `SolnConfigName`  
 Обязательно. Имя конфигурации решения, которая будет применяться для сборки решения, указанного в `SolutionName`.  
  
 `SolutionName`  
 Обязательно. Полный путь и имя для файла решения.  
  
 /project `ProjName`  
 Необязательный. Путь и имя для файла проекта в решении. Можно ввести относительный путь из папки `SolutionName` к файлу проекта, отображаемое имя проекта либо полный путь и имя для файла проекта.  
  
 /projectconfig `ProjConfigName`  
 Необязательный. Имя конфигурации сборки проекта, которая применяется при сборке указанного `/project`.  
  
## <a name="remarks"></a>Примечания  
 Указанный проект должен быть проектом развертывания. В противном случае при передаче собранного проекта для развертывания возникает ошибка.  
  
 Строки с пробелами заключаются в двойные кавычки.  
  
 Сводные данные для сборок, включая ошибки, могут отображаться в окне **команд** или в любом файле журнала, указанном с помощью параметра `/out`.  
  
## <a name="example"></a>Пример  
 Этот пример развертывает проект `CSharpConsoleApp` с использованием конфигурации сборки проекта `Release` в пределах конфигурация решения `Release` для `MySolution`.  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /deploy Release /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Release   
```  
  
## <a name="see-also"></a>См. также  
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [/Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)   
 [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)   
 [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)   
 [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)   
 [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)