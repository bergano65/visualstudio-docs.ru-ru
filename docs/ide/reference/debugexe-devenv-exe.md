---
title: "-DebugExe (devenv.exe) | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Devenv, /DebugExe switch
- DebugExe switch
- /DebugExe [devenv.exe]
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
caps.latest.revision: "4"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8f50bfd0fa5b0f9303bc6256078a30da6e1c0575
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
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