---
title: "-ProjectConfig (devenv.exe) | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- /projectconfig Devenv switch
- configurations, rebuilding
- deployment projects, creating
- configurations, cleaning
- deployment projects, specifying
- deployment projects, adding
- build configurations, specifying
- Devenv, /projectconfig switch
- projectconfig Devenv switch (/projectconfig)
- projects [Visual Studio], build configuration
- projects [Visual Studio], cleaning
ms.assetid: 6b54ef59-ffed-4f62-a645-1279ede97ebf
caps.latest.revision: 11
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 02fd2a046b7b4070fa4e1903bd13772c518a7207
ms.lasthandoff: 02/22/2017

---
# <a name="projectconfig-devenvexe"></a>/ProjectConfig (devenv.exe)
Указывает конфигурацию сборки проекта, применяемую при сборке, очистке, перестроении или развертывании проекта, указанного в аргументе `/project`.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
devenv SolutionName {/build|/clean|/rebuild|/deploy} SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]  
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
 Обязательный. Имя конфигурации решения, которая будет применяться для решения с именем `SolutionName`.  
  
 `SolutionName`  
 Обязательный. Полный путь и имя для файла решения.  
  
 /project `ProjName`  
 Необязательно. Путь и имя для файла проекта в решении. Можно ввести относительный путь из папки `SolutionName` к файлу проекта, отображаемое имя проекта либо полный путь и имя для файла проекта.  
  
 /projectconfig `ProjConfigName`  
 Необязательно. Имя конфигурации сборки проекта, которая применяется к указанному `/project`.  
  
## <a name="remarks"></a>Примечания  
  
-   Следует использовать с параметром `/project` в составе команды `devenv /build`, /`clean`, `/rebuild` или `/deploy`.  
  
-   Строки с пробелами заключаются в двойные кавычки.  
  
-   Сводные данные для сборок, включая ошибки, могут отображаться в окне **команд** или в любом файле журнала, указанном с помощью параметра `/out`.  
  
## <a name="example"></a>Пример  
 В этом примере выполняется сборка проекта `CSharpConsoleApp` с использованием конфигурации проекта `Debug` в пределах конфигурация решения `Debug` для `MySolution`.  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug   
```  
  
## <a name="see-also"></a>См. также  
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [/Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)   
 [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)   
 [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)   
 [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)   
 [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)   
 [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
