---
title: "-Log (devenv.exe) | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cf5ab0e1949716005d12d51d06b0d915344833aa
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)
Регистрирует все действия в файле журнала для устранения неполадок. Этот файл отображается после вызова `devenv /log` по крайней мере один раз. Файл журнала по умолчанию:  
  
 *%APPDATA%*\Microsoft\VisualStudio\\*Версия*\ActivityLog.xml  
  
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