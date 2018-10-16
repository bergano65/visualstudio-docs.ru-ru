---
title: Команда "Задать текущий процесс" | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0baea39c341e8034ff222de32548d0518f115e82
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49246666"
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
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)



