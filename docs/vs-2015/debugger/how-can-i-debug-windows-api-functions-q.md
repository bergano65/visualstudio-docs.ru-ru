---
title: Как отладить функции Windows API? | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c6b0f06ddaadef8f462b59c9f445a0ae02d0123e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47569499"
---
# <a name="how-can-i-debug-windows-api-functions"></a>Как отладить функции Windows API?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как могу ли я отлаживать функции Windows API?](https://docs.microsoft.com/visualstudio/debugger/how-can-i-debug-windows-api-functions-q).  
  
Если нужно отладить функцию Windows API с загруженными символами NT, необходимо выполнить следующие действия.  
  
### <a name="to-set-a-breakpoint-on-a-windows-api-function-with-nt-symbols-loaded"></a>Установка точки останова в функции Windows API с загруженными символами NT  
  
-   Введите имя функции вместе с именем DLL-файла, в котором эта функция находится. В 32-разрядном коде используйте декорированную форму имени функции. Чтобы задать точку останова на **MessageBeep**, например, нужно указать следующее.  
  
    ```  
    {,,USER32.DLL}_MessageBeep@4  
    ```  
  
     Чтобы получить декорированное имя, см. в разделе [Просмотр декорированные имена](http://msdn.microsoft.com/en-us/f79e2717-a4db-4d12-a689-69830cce2be0).  
  
## <a name="see-also"></a>См. также  
 [Часто задаваемые вопросы отладки машинного кода](../debugger/debugging-native-code-faqs.md)   
 [Отладка машинного кода](../debugger/debugging-native-code.md)



