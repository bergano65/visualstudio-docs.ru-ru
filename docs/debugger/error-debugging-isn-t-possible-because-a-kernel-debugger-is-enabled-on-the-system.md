---
title: "Ошибка: &#39; t невозможна, поскольку отладчик ядра отладки в системе | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.kernel_dbg_enabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords: kernel debugger
ms.assetid: 630a7abd-3303-4aaa-888a-6de3de14bc01
caps.latest.revision: "23"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 448dbc486d58bc46e531b92de9f78272e4304d27
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="error-debugging-isn39t-possible-because-a-kernel-debugger-is-enabled-on-the-system"></a>Ошибка: &#39; t невозможна, поскольку отладчик ядра отладки в системе
При отладке управляемого кода может появиться следующее сообщение об ошибке:  
  
```  
Debugging isn't possible because a kernel debugger is enabled on the system  
```  
  
 Это сообщение появляется при попытке произвести отладку управляемого кода:  
  
-   в системе [!INCLUDE[win7](../debugger/includes/win7_md.md)] или [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)], которая была запущена в режиме отладки;  
  
-   для приложения, использующего среду CLR версии CLR 2.0, 3.0 или 3.5.  
  
## <a name="solution"></a>Решение  
  
#### <a name="to-fix-this-problem"></a>Для устранения этой проблемы:  
  
-   Обновите приложение, чтобы использовалась среда CLR версии 4.0 или 4.5.  
  
     —или—  
  
-   Отключите отладку на уровне ядра и выполняйте отладку в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     —или—  
  
-   Выполняйте отладку с использованием отладчика ядра вместо отладки в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     —или—  
  
-   В отладчике ядра отключите исключения режима пользователя.  
  
#### <a name="to-disable-kernel-debugging-in-the-current-session"></a>Отключение отладки на уровне ядра в текущем сеансе  
  
-   В командной строке введите:  
  
    ```  
    Kdbgctrl.exe -d  
    ```  
  
#### <a name="to-disable-kernel-debugging-for-all-sessions-windows-vista-and-windows-7"></a>Отключение отладки на уровне ядра для всех сеансов (Windows Vista и Windows 7)  
  
1.  В командной строке введите:  
  
    ```  
    bcdedit /debug off   
    ```  
  
2.  Перезагрузите компьютер.  
  
#### <a name="to-disable-kernel-debugging-for-all-sessions-other-windows-operating-systems"></a>Отключение отладки на уровне ядра для всех сеансов (другие операционные системы Windows)  
  
1.  Найдите файл boot.ini на системном диске (обычно это диск C:\\). Файл boot.ini может быть скрыт и иметь атрибут "только для чтения". Поэтому для его отображения необходимо использовать следующую команду:  
  
    ```  
    dir /ASH  
    ```  
  
2.  Откройте файл boot.ini с помощью программы "Блокнот" и удалите следующие параметры:  
  
    ```  
    /debug  
    /debugport  
    /baudrate  
    ```  
  
3.  Перезагрузите компьютер.  
  
#### <a name="to-debug-with-the-kernel-debugger"></a>Выполнение отладки с помощью отладчика ядра  
  
1.  Если отладчик ядра подключен, появится сообщение с запросом, нужно ли продолжать отладку. Нажмите кнопку, чтобы продолжить.  
  
2.  Может появиться `User break exception(Int 3).` Если это произойдет, введите следующую команду отладчика ядра для продолжения отладки:  
  
     `gn`  
  
## <a name="see-also"></a>См. также  
 [Безопасность отладчика](../debugger/debugger-security.md)   
 [Отладка управляемого кода](../debugger/debugging-managed-code.md)