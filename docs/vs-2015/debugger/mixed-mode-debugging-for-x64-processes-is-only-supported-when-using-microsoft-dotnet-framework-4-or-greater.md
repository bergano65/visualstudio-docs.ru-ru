---
title: Смешанный режим отладки для x64 поддерживается только при использовании Microsoft.NET Framework 4 или более поздней версии | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.interop_unsupported_x64
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: b7495655-54c0-4315-8422-43bf63b8c22e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c7735e1199e7871324fe22b0af33d2ff3230ca51
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49175777"
---
# <a name="mixed-mode-debugging-for-x64-processes-is-only-supported-when-using-microsoftnet-framework-4-or-greater"></a>На 64-разрядных платформах Windows отладка в смешанном режиме поддерживается только при использовании платформы Microsoft.NET Framework версии 4.0 или выше
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

NET Framework версии ранее чем 4 не поддерживает отладку в смешанном режиме x64 обрабатывает. Это значит, что при выполнении отладки переход из управляемого кода в неуправляемый (как и обратный переход) невозможен.  
  
### <a name="workarounds"></a>Методы обхода проблемы  
  
-   Обновить проект так, чтобы в нем использовалась платформа Microsoft .NET Framework версии 4 или позднее.  
  
     – или –  
  
     Вести отладку управляемого и машинного кода в отдельных сеансах отладки.  
  
     – или –  
  
     Вести отладку смешанного кода в 32-разрядном процессе в соответствии со следующими процедурами:  
  
### <a name="to-change-the-platform-to-32-bit-visual-basic-or-c"></a>Изменение платформы на 32-разрядную версию (Visual Basic или C#)  
  
1.  В **обозревателе решений**, щелкните правой кнопкой мыши проект и нажмите кнопку **свойства**.  
  
2.  На страницах свойств нажмите кнопку **компиляции** или **Отладка** вкладки.  
  
3.  Нажмите кнопку **платформы** и выберите x86 в списке платформ.  
  
     По умолчанию компиляторы Visual Basic и С# создают код, который можно использовать на любом ЦП. На 64-разрядном компьютере такие двоичные файлы работают как 64-разрядные процессы. Чтобы запустить в 32-разрядном процессе, необходимо выбрать **Win32**, а не **AnyCPU**.  
  
### <a name="to-change-the-platform-to-32-bit-cc"></a>Изменение платформы на 32-разрядную версию (C или C++)  
  
1.  В **обозревателе решений**, щелкните правой кнопкой мыши проект, а затем нажмите кнопку **свойства**.  
  
2.  На страницах свойств нажмите кнопку **платформы** и выберите в списке платформ Win32.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   См. в разделе [настройки отладки SQL](http://msdn.microsoft.com/en-us/3db09e68-edcc-42de-9c22-4e97cfd55ab3).  
  
## <a name="see-also"></a>См. также  
 [Отладка 64-разрядных приложений](../debugger/debug-64-bit-applications.md)



