---
title: Команда "Задать текущий процесс" | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5ea3028be32fdccffd70f7b3d0aa9d3b4eba172c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="set-current-process"></a>Команда Set Current Process
Задает указанный процесс в качестве активного процесса в отладчике.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Debug.SetCurrentProcess index  
```  
  
## <a name="arguments"></a>Аргументы  
 `index`  
 Обязательно. Индекс процесса.  
  
## <a name="remarks"></a>Примечания  
 Во время отладки можно подключиться к нескольким процессам, но в любой момент времени только один из них будет активным в отладчике. Чтобы задать активный процесс, можно использовать команду `SetCurrentProcess`.  
  
## <a name="example"></a>Пример  
  
```  
>Debug.SetCurrentProcess 1  
```  
  
## <a name="see-also"></a>См. также  
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Командное окно](../../ide/reference/command-window.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)