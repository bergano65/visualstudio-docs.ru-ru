---
title: Как отладить функции Windows API? | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.api
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], Windows API functions
- NT symbols and debugging Windows API functions
- Windows API functions, debugging
- Windows API, debugging API functions
- APIs, debugging
ms.assetid: 7c126f57-62ab-4d94-9805-632d696ba1f0
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 66ed3dbd6c67fe247ea514a9d41780584ae8f1e2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-can-i-debug-windows-api-functions"></a>Как отладить функции Windows API?
Если нужно отладить функцию Windows API с загруженными символами NT, необходимо выполнить следующие действия.  
  
### <a name="to-set-a-breakpoint-on-a-windows-api-function-with-nt-symbols-loaded"></a>Установка точки останова в функции Windows API с загруженными символами NT  
  
-   Введите имя функции вместе с именем DLL-файла, в котором эта функция находится. В 32-разрядном коде используйте декорированную форму имени функции. Чтобы задать точку останова на **MessageBeep**, например, необходимо ввести следующее.  
  
    ```  
    {,,USER32.DLL}_MessageBeep@4  
    ```  
  
     Сведения о получении декорированного имени см [Просмотр декорированные имена](http://msdn.microsoft.com/en-us/f79e2717-a4db-4d12-a689-69830cce2be0).  
  
## <a name="see-also"></a>См. также  
 [Часто задаваемые вопросы по отладке машинного кода](../debugger/debugging-native-code-faqs.md)   
 [Отладка машинного кода](../debugger/debugging-native-code.md)