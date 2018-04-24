---
title: -Project (devenv.exe) | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- /project Devenv switch
- projects [Visual Studio], rebuilding
- projects [Visual Studio], building
- deployment projects, specifying
- project Devenv switch (/project)
- Devenv, /project switch
- projects [Visual Studio], cleaning
ms.assetid: 8b07859c-3439-436d-9b9a-a8ee744eee30
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 56dc2cdb28e05c884fbf1e29c282a3e43f7390ff
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="project-devenvexe"></a>/Project (devenv.exe)
Указывает отдельный проект в заданной конфигурации решения для сборки, очистки, перестроения или развертывания.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
devenv SolutionName {/build|/clean|/rebuild|/deploy} SolnConfigName   
[/project ProjName] [/projectconfig ProjConfigName]   
```  
  
## <a name="arguments"></a>Аргументы  
 /build  
 Выполняет сборку проекта, заданного в `/project` `ProjName`.  
  
 /clean  
 Удаляет все промежуточные файлы и выходные каталоги, созданные во время сборки.  
  
 /rebuild  
 Очищает проект, заданный в `/project` `ProjName`, а затем выполняет его сборку.  
  
 /deploy  
 Указывает, что проект должен быть развернут после сборки или перестроения.  
  
 `SolnConfigName`  
 Обязательно. Имя конфигурации решения, которая будет применяться для решения с именем `SolutionName`.  
  
 `SolutionName`  
 Обязательно. Полный путь и имя для файла решения.  
  
 /project `ProjName`  
 Необязательный. Путь и имя для файла проекта в решении. Можно ввести относительный путь из папки `SolutionName` к файлу проекта, отображаемое имя проекта либо полный путь и имя для файла проекта.  
  
 /projectconfig `ProjConfigName`  
 Необязательный. Имя конфигурации сборки проекта, которая применяется к указанному `/project`.  
  
## <a name="remarks"></a>Примечания  
  
-   Следует использовать в составе команды `devenv /build`, /`clean`, `/rebuild` или `/deploy`.  
  
-   Строки с пробелами заключаются в двойные кавычки.  
  
-   Сводные данные для сборок, включая ошибки, могут отображаться в окне **команд** или в любом файле журнала, указанном с помощью параметра `/out`.  
  
## <a name="example"></a>Пример  
 В этом примере выполняется сборка проекта `CSharpConsoleApp` с использованием конфигурации проекта `Debug` в пределах конфигурация решения `Debug` для `MySolution`.  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug   
```  
  
## <a name="see-also"></a>См. также  
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [/ProjectConfig (devenv.exe)](../../ide/reference/projectconfig-devenv-exe.md)   
 [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)   
 [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)   
 [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)   
 [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)   
 [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)