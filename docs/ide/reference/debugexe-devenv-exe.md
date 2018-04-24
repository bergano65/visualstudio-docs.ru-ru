---
title: -DebugExe (devenv.exe) | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Devenv, /DebugExe switch
- DebugExe switch
- /DebugExe [devenv.exe]
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e0882ae58919cafae71bcb056e74533b7ce64a4e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)
Открывает указанный исполняемый файл для отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Devenv /debugexe ExecutableFile  
```  
  
## <a name="arguments"></a>Аргументы  
 `ExecutableFile`  
 Обязательно. Путь и имя EXE-файла.  
  
 Если EXE-файл не найден или не существует, никакие предупреждения или ошибки не выводятся, а [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] запускается обычным образом.  
  
## <a name="remarks"></a>Примечания  
 Строки, следующие за параметром `ExecutableFile`, передаются в этот файл в качестве аргументов.  
  
## <a name="example"></a>Пример  
 Следующий пример открывает файл `MyApplication.exe` для отладки.  
  
```  
Devenv.exe /debugexe MyApplication.exe  
```  
  
## <a name="see-also"></a>См. также  
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)