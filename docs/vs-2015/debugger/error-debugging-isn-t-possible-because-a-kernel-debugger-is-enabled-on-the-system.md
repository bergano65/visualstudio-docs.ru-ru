---
title: 'Ошибка: Отладка&#39;t невозможна, поскольку в системе включен отладчик ядра | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.kernel_dbg_enabled
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
- C++
helpviewer_keywords:
- kernel debugger
ms.assetid: 630a7abd-3303-4aaa-888a-6de3de14bc01
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4f2f963ad2fbdad9453f6c6b853bc720034f613c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68197075"
---
# <a name="error-debugging-isn39t-possible-because-a-kernel-debugger-is-enabled-on-the-system"></a>Ошибка: Отладка&#39;t невозможна, поскольку в системе включен отладчик ядра
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

При отладке управляемого кода может появиться следующее сообщение об ошибке:  
  
```  
Debugging isn't possible because a kernel debugger is enabled on the system  
```  
  
 Это сообщение появляется при попытке произвести отладку управляемого кода:  
  
- в системе [!INCLUDE[win7](../includes/win7-md.md)] или [!INCLUDE[wiprlhext](../includes/wiprlhext-md.md)], которая была запущена в режиме отладки;  
  
- для приложения, использующего среду CLR версии CLR 2.0, 3.0 или 3.5.  
  
## <a name="solution"></a>Решение  
  
#### <a name="to-fix-this-problem"></a>Для устранения этой проблемы:  
  
- Обновите приложение, чтобы использовалась среда CLR версии 4.0 или 4.5.  
  
     —или—  
  
- Отключите отладку на уровне ядра и выполняйте отладку в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
     —или—  
  
- Выполняйте отладку с использованием отладчика ядра вместо отладки в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
     —или—  
  
- В отладчике ядра отключите исключения режима пользователя.  
  
#### <a name="to-disable-kernel-debugging-in-the-current-session"></a>Отключение отладки на уровне ядра в текущем сеансе  
  
- В командной строке введите следующее:  
  
    ```  
    Kdbgctrl.exe -d  
    ```  
  
#### <a name="to-disable-kernel-debugging-for-all-sessions-windows-vista-and-windows-7"></a>Отключение отладки на уровне ядра для всех сеансов (Windows Vista и Windows 7)  
  
1. В командной строке введите следующее:  
  
    ```  
    bcdedit /debug off   
    ```  
  
2. Перезагрузите компьютер.  
  
#### <a name="to-disable-kernel-debugging-for-all-sessions-other-windows-operating-systems"></a>Отключение отладки на уровне ядра для всех сеансов (другие операционные системы Windows)  
  
1. Найдите файл boot.ini на системном диске (обычно C:\\). Файл boot.ini может быть скрыт и иметь атрибут "только для чтения". Поэтому для его отображения необходимо использовать следующую команду:  
  
    ```  
    dir /ASH  
    ```  
  
2. Откройте файл boot.ini с помощью программы "Блокнот" и удалите следующие параметры:  
  
    ```  
    /debug  
    /debugport  
    /baudrate  
    ```  
  
3. Перезагрузите компьютер.  
  
#### <a name="to-debug-with-the-kernel-debugger"></a>Выполнение отладки с помощью отладчика ядра  
  
1. Если отладчик ядра подключен, появится сообщение с запросом, нужно ли продолжать отладку. Нажмите кнопку, чтобы продолжить.  
  
2. Может появиться `User break exception(Int 3).` Если это произойдет, введите следующую команду отладчика ядра для продолжения отладки:  
  
     `gn`  
  
## <a name="see-also"></a>См. также  
 [Безопасность отладчика](../debugger/debugger-security.md)   
 [Отладка управляемого кода](../debugger/debugging-managed-code.md)
