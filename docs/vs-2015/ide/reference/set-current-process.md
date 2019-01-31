---
title: Команда "Задать текущий процесс" | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: be451ee1a0b4361e44c8be96713872ca0ee3bd76
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "54768852"
---
# <a name="set-current-process"></a>Команда Set Current Process
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Задает указанный процесс в качестве активного процесса в отладчике.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Debug.SetCurrentProcess index  
```  
  
## <a name="arguments"></a>Аргументы  
 `index`  
 Обязательный. Индекс процесса.  
  
## <a name="remarks"></a>Примечания  
 Во время отладки можно подключиться к нескольким процессам, но в любой момент времени только один из них будет активным в отладчике. Чтобы задать активный процесс, можно использовать команду `SetCurrentProcess`.  
  
## <a name="example"></a>Пример  
  
```  
>Debug.SetCurrentProcess 1  
```  
  
## <a name="see-also"></a>См. также раздел  
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Командное окно](../../ide/reference/command-window.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
