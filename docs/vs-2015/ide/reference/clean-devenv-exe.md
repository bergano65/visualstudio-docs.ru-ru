---
title: -Clean (devenv.exe) | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- builds [Team System], cleaning files
- clean Devenv switch
- /clean Devenv switch
- Devenv, /clean switch
ms.assetid: 79929dfd-22c9-4cec-a0d0-a16f15b8f7e4
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e1c32e062cf2a5406f235133fb646a16d21707cb
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59646793"
---
# <a name="clean-devenvexe"></a>/Clean (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Удаляет все промежуточные файлы и выходные каталоги.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
devenv FileName /Clean [ /project projectnameorfile [/projectconfig name ] ]  
```  
  
## <a name="arguments"></a>Аргументы  
 `FileName`  
 Обязательный. Полный путь и имя для файла решения или файла проекта.  
  
 /project `ProjName`  
 Необязательный параметр. Путь и имя для файла проекта в решении. Можно ввести относительный путь из папки `SolutionName` к файлу проекта, отображаемое имя проекта либо полный путь и имя для файла проекта.  
  
 /projectconfig `ProjConfigName`  
 Необязательный параметр. Имя конфигурации сборки проекта, которая применяется при очистке указанного `/project`.  
  
## <a name="remarks"></a>Примечания  
 Этот параметр выполняет те же функции, что и команда меню **Очистить решение** в интегрированной среде разработки (IDE).  
  
 Строки с пробелами заключаются в двойные кавычки.  
  
 Сводные данные для удаления и сборки, включая ошибки, могут отображаться в окне **Команда** или любом файле журнала, указанном с помощью параметра `/out`.  
  
## <a name="example"></a>Пример  
 Первый пример очищает решение `MySolution` с использованием конфигурации по умолчанию, указанной в файле решения.  
  
 Второй пример очищает проект `CSharpConsoleApp` с использованием конфигурации сборки проекта `Debug` в пределах конфигурация решения `Debug` для `MySolution`.  
  
```  
Devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /Clean  
  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /Clean /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig "Debug"   
```  
  
## <a name="see-also"></a>См. также раздел  
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)   
 [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)   
 [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
