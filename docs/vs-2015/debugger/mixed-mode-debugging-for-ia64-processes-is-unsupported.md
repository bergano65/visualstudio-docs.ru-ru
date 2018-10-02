---
title: Для процессов IA64 отладка в смешанном режиме не поддерживается. | Документы Майкрософт
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
- vs.debug.error.interop_unsupported_ia64
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 20bc1e38-049b-4388-87c4-936815d85b46
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3777ce079aea853400896408542380c5e2d16ef5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47561656"
---
# <a name="mixed-mode-debugging-for-ia64-processes-is-unsupported"></a>Для процессов IA64 отладка в смешанном режиме не поддерживается.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [для процессов IA64 отладка в смешанном режиме не поддерживается.](https://docs.microsoft.com/visualstudio/debugger/mixed-mode-debugging-for-ia64-processes-is-unsupported).  
  
Visual Studio не поддерживает отладку управляемого и машинного кода в процессах IA64 в смешанном режиме. Таким образом, при выполнении отладки переход из управляемого кода в неуправляемый невозможен (как и обратный переход).  
  
### <a name="workarounds"></a>Методы обхода проблемы  
  
-   Вести отладку управляемого и машинного кода в отдельных сеансах отладки.  
  
     – или –  
  
     Вести отладку смешанного кода в 32-разрядном процессе в соответствии со следующими процедурами:  
  
### <a name="to-change-the-platform-to-32-bit-visual-basic-or-c"></a>Изменение платформы на 32-разрядную версию (Visual Basic или C#)  
  
1.  В **обозревателе решений**, щелкните правой кнопкой мыши на проекте, а затем нажмите кнопку **свойства** в контекстном меню.  
  
2.  На страницах свойств нажмите кнопку **компиляции** или **Отладка** вкладки.  
  
3.  Нажмите кнопку **платформы** и выберите x86 в списке платформ.  
  
     По умолчанию компиляторы Visual Basic и С# создают код, который можно использовать на любом ЦП. На 64-разрядном компьютере такие двоичные файлы работают как 64-разрядные процессы. Чтобы запустить в 32-разрядном процессе, необходимо выбрать **Win32**, а не **AnyCPU**.  
  
### <a name="to-change-the-platform-to-32-bit-cc"></a>Изменение платформы на 32-разрядную версию (C или C++)  
  
1.  В **обозревателе решений**, щелкните правой кнопкой мыши на проекте, а затем нажмите кнопку **свойства** в контекстном меню.  
  
2.  На страницах свойств нажмите кнопку **платформы** и выберите из списка платформ, Win32  
  
## <a name="see-also"></a>См. также  
 [Отладка 64-разрядных приложений](../debugger/debug-64-bit-applications.md)



