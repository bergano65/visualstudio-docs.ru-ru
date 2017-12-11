---
title: "Команда \"Путь к символам\" | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: debug.symbolpath
helpviewer_keywords:
- symbol path command
- Debug.SymbolPath command
- SymbolPath command
ms.assetid: b697ef2d-3f5d-40df-b113-7068a5bec0d4
caps.latest.revision: "9"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d446779e4f84bf19e965393f9fa1142c7e4e166a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="symbol-path-command"></a>Команда Symbol Path
Задает список каталогов для поиска символов отладчиком.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Debug.SymbolPath pathname1;pathname2;... pathnameN  
```  
  
## <a name="arguments"></a>Аргументы  
 `pathname`  
 Необязательно. Список путей, разделенных точкой с запятой, для поиска символов отладчиком.  
  
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