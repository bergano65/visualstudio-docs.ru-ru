---
title: "Отладка F # | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Debugging [F#]
- F#, debugging
ms.assetid: 20bcd51c-2d06-4281-9a1e-ef2b91d1a779
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a37d69339a8a6345bbc63f563379c9f87d6cf483
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="debugging-f"></a>Отладка F#
Отладка F# подобна отладке любого управляемого языка за несколькими исключениями:  
  
-   **Видимые** в окне не отображаются переменные F #.  
  
-   Функция "Изменить и продолжить" не поддерживается для языка F#. Редактирование кода на языке F# во время сеанса отладки возможно, но его следует избегать. Поскольку изменения кода не применяются во время сеанса отладки, редактирование кода в это время может привести к несоответствию исходного кода отлаживаемому.  
  
-   Отладчик не распознает выражения F#. Чтобы ввести выражение в окне отладчика или в диалоговом окне во время отладки кода на языке F#, необходимо перевести это выражение в синтаксис C#. Выполняя перевод выражения F# в синтаксис C#, помните, что в C# в качестве оператора сравнения используется ==, а в F# – одинарный знак =.  
  
## <a name="see-also"></a>См. также  
 [Отладка управляемого кода](../debugger/debugging-managed-code.md)
