---
title: Отладка F# | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Debugging [F#]
- F#, debugging
ms.assetid: 20bcd51c-2d06-4281-9a1e-ef2b91d1a779
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4cfe65671e0f3d9b3e4702c9f08740c6694286ce
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51734813"
---
# <a name="debugging-f"></a>Отладка F# #
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Отладка F# подобна отладке любого управляемого языка за несколькими исключениями:  
  
-   **"Видимые"** окне не отображаются F# переменные.  
  
-   Функция "Изменить и продолжить" не поддерживается для языка F#. Редактирование кода на языке F# во время сеанса отладки возможно, но его следует избегать. Поскольку изменения кода не применяются во время сеанса отладки, редактирование кода в это время может привести к несоответствию исходного кода отлаживаемому.  
  
-   Отладчик не распознает выражения F#. Чтобы ввести выражение в окне отладчика или в диалоговом окне во время отладки кода на языке F#, необходимо перевести это выражение в синтаксис C#. Выполняя перевод выражения F# в синтаксис C#, помните, что в C# в качестве оператора сравнения используется ==, а в F# – одинарный знак =.  
  
## <a name="see-also"></a>См. также  
 [Отладка управляемого кода](../debugger/debugging-managed-code.md)



