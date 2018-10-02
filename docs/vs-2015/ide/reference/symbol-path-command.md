---
title: Команда "Путь к символам" | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- debug.symbolpath
helpviewer_keywords:
- symbol path command
- Debug.SymbolPath command
- SymbolPath command
ms.assetid: b697ef2d-3f5d-40df-b113-7068a5bec0d4
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b21a745177722160b100d0bbad770c3a74c40ca3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47559615"
---
# <a name="symbol-path-command"></a>Команда Symbol Path
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [команда Symbol Path](https://docs.microsoft.com/visualstudio/ide/reference/symbol-path-command).  
  
  
Задает список каталогов для поиска символов отладчиком.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Debug.SymbolPath pathname1;pathname2;... pathnameN  
```  
  
## <a name="arguments"></a>Аргументы  
 `pathname`  
 Необязательный. Список путей, разделенных точкой с запятой, для поиска символов отладчиком.  
  
## <a name="remarks"></a>Примечания  
 Если `pathname` не указан, эта команда выводит список текущих путей к символам.  
  
## <a name="example"></a>Пример  
 Этот пример добавляет два пути в список каталогов символов.  
  
```  
Debug.SymbolPath C:\Symbol Path 1;C:\Symbol Path 2  
```  
  
## <a name="example"></a>Пример  
 Этот пример отображает список текущих путей к символам, разделенных точкой с запятой.  
  
```  
Debug.SymbolPath  
```  
  
## <a name="see-also"></a>См. также  
 [Командное окно](../../ide/reference/command-window.md)   
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)



