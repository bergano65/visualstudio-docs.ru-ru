---
title: 'Отладка F # | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Debugging [F#]
- F#, debugging
ms.assetid: 20bcd51c-2d06-4281-9a1e-ef2b91d1a779
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2b3bb2a9379dd6cd43bb0398ccda2b031b96d56e
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="debugging-f"></a>Отладка F#
Отладка F# подобна отладке любого управляемого языка за несколькими исключениями:  
  
-   **Видимые** в окне не отображаются переменные F #.  
  
-   Функция "Изменить и продолжить" не поддерживается для языка F#. Редактирование кода на языке F# во время сеанса отладки возможно, но его следует избегать. Поскольку изменения кода не применяются во время сеанса отладки, редактирование кода в это время может привести к несоответствию исходного кода отлаживаемому.  
  
-   Отладчик не распознает выражения F#. Чтобы ввести выражение в окне отладчика или в диалоговом окне во время отладки кода на языке F#, необходимо перевести это выражение в синтаксис C#. Выполняя перевод выражения F# в синтаксис C#, помните, что в C# в качестве оператора сравнения используется ==, а в F# – одинарный знак =.  
  
## <a name="see-also"></a>См. также  
 [Отладка управляемого кода](../debugger/debugging-managed-code.md)
