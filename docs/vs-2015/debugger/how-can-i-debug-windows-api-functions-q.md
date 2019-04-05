---
title: Как отладить функции Windows API? | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.api
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [C++], Windows API functions
- NT symbols and debugging Windows API functions
- Windows API functions, debugging
- Windows API, debugging API functions
- APIs, debugging
ms.assetid: 7c126f57-62ab-4d94-9805-632d696ba1f0
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fb57f2d46eb103c6b59805ae15bc339b7e3bdc84
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58993140"
---
# <a name="how-can-i-debug-windows-api-functions"></a>Как отладить функции Windows API?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Если нужно отладить функцию Windows API с загруженными символами NT, необходимо выполнить следующие действия.  
  
### <a name="to-set-a-breakpoint-on-a-windows-api-function-with-nt-symbols-loaded"></a>Установка точки останова в функции Windows API с загруженными символами NT  
  
-   Введите имя функции вместе с именем DLL-файла, в котором эта функция находится. В 32-разрядном коде используйте декорированную форму имени функции. Например, чтобы задать точку останова на **MessageBeep**, необходимо ввести следующее.  
  
    ```  
    {,,USER32.DLL}_MessageBeep@4  
    ```  
  
     Чтобы получить декорированное имя, см. в разделе [Просмотр декорированные имена](http://msdn.microsoft.com/f79e2717-a4db-4d12-a689-69830cce2be0).  
  
## <a name="see-also"></a>См. также  
 [Вопросы и ответы по отладке машинного кода](../debugger/debugging-native-code-faqs.md)   
 [Отладка машинного кода](../debugger/debugging-native-code.md)
