---
title: -Log (devenv.exe) | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8fa0fa90e904d4fb7f3e6820ce997a6a93e738f9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)
Регистрирует все действия в файле журнала для устранения неполадок. Этот файл отображается после вызова `devenv /log` по крайней мере один раз. Файл журнала по умолчанию:  
  
 *%APPDATA%* \Microsoft\VisualStudio\\*Версия*\ActivityLog.xml  
  
 где *Версия* — это версия Visual Studio. Однако можно указать альтернативный путь и имя файла.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Devenv /log Path\NameOfLogFile  
```  
  
## <a name="remarks"></a>Примечания  
 Этот ключ должен находиться в конце командной строки после всех других параметров.  
  
 Журнал записывается для всех экземпляров Visual Studio, которые были активированы с ключом /log. Для экземпляров Visual Studio, которые были активированы без данного ключа, журнал не записывается.  
  
## <a name="see-also"></a>См. также  
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)