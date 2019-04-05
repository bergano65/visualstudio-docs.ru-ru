---
title: Практическое руководство. Проверок во время выполнения машинного кода | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- c.runtime.errorchecks
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- /RTC compiler option [C++], /O compiler option
- run-time checks, native
- stack, pointer corruption
- stack pointers, corruption
- /O compiler option, /RTC option
- run-time errors, error checks
- O compiler option, /RTC option
- debugger, runtime errors
- variables [debugger], loss of data
- runtime_checks pragma
- variables [debugger], catching dependencies on uninitialized local variables
- run-time errors, debugging
- debugger, native run-time checks
- optimized build option
- RTC compiler option, /O compiler option
- native run-time checks
- run-time checks
- debugging arrays
- stack pointers
- arrays [Visual Studio], debugging
ms.assetid: dc7b2f1e-5ff6-42e0-89b3-dc9dead83ee1
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8f6fc8c2019e8798411a10cd61272c2f6c1684c0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58993321"
---
# <a name="how-to-use-native-run-time-checks"></a>Практическое руководство. Настройка проверок во время выполнения машинного кода
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В Visual C++ можно использовать проверки в машинном коде [runtime_checks](http://msdn.microsoft.com/library/ae50b43f-f88d-47ad-a2db-3389e9e7df5b) для обнаружения таких распространенных ошибок, возникающих во время выполнения, как:  
  
- повреждение указателя стека;  
  
- переполнение локальных массивов;  
  
- повреждение стека;  
  
- зависимости от неинициализированных локальных переменных;  
  
- потеря данных при присваивании переменным меньшего размера.  
  
  Попытка использования опции **/RTC** с оптимизированным построением (**/O**) приведет к ошибке компилятора. Директивы `runtime_checks` при оптимизированном построении игнорируются.  
  
  Если осуществляется отладка программы с включенным режимом проверки во время выполнения, по умолчанию при возникновении ошибки во время выполнения программа будет прервана и произойдет возврат в отладчик. Это используемое по умолчанию поведение можно изменить для любой проверки во время выполнения. Дополнительные сведения см. в разделе [Управление исключениями с помощью отладчика](../debugger/managing-exceptions-with-the-debugger.md).  
  
  В приведенной ниже процедуре описано, как включить в отладочном построении проверку в машинных кодах во время выполнения, и как изменить поведение проверки в машинных кодах во время выполнения.  
  
  Другие разделы, представленные здесь, содержат следующие сведения:  
  
- [Настройка проверки кода во время выполнения с библиотекой среды выполнения языка C](../debugger/native-run-time-checks-customization.md)  
  
- [Использование проверки кода во время выполнения без библиотеки среды выполнения языка C](../debugger/using-run-time-checks-without-the-c-run-time-library.md)  
  
### <a name="to-enable-native-run-time-checks-in-a-debug-build"></a>Включение проверок в машинных кодах во время выполнения в отладочном построении  
  
-   Используйте опцию **/RTC** и компоновку с отладочной версией библиотеки времени выполнения языка С (например, /MDd).  
  
### <a name="to-modify-native-run-time-check-behavior"></a>Изменение порядка проверки в машинных кодах во время выполнения  
  
-   Используйте директиву `runtime_checks` .  
  
## <a name="see-also"></a>См. также  
 [Отладка в Visual Studio](../debugger/debugging-in-visual-studio.md)   
 [runtime_checks](http://msdn.microsoft.com/library/ae50b43f-f88d-47ad-a2db-3389e9e7df5b)   
 [Проверка ошибок во время выполнения](http://msdn.microsoft.com/library/c965dd01-57ad-4a3c-b1d6-5aa04f920501)
