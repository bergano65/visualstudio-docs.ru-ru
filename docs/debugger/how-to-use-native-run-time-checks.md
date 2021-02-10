---
title: Использование проверок во время выполнения машинного кода | Документация Майкрософт
description: Использование проверок во время выполнения машинного кода в Visual Studio для обнаружения таких распространенных ошибок, возникающих во время выполнения, как повреждение указателя стека, переполнение локальных массивов и повреждение стека.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- c.runtime.errorchecks
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
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
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: be6684ed1801bc825bcb0db236737f33fe3901af
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891804"
---
# <a name="how-to-use-native-run-time-checks"></a>Практическое руководство. Настройка проверок во время выполнения машинного кода
В проекте Visual Studio C++ можно использовать проверки в машинном коде [runtime_checks](/cpp/preprocessor/runtime-checks) для обнаружения таких распространенных ошибок, возникающих во время выполнения, как:

- повреждение указателя стека;

- переполнение локальных массивов;

- повреждение стека;

- зависимости от неинициализированных локальных переменных;

- потеря данных при присваивании переменным меньшего размера.

  Попытка использования опции **/RTC** с оптимизированным построением ( **/O**) приведет к ошибке компилятора. Директивы `runtime_checks` при оптимизированном построении игнорируются.

  Если осуществляется отладка программы с включенным режимом проверки во время выполнения, по умолчанию при возникновении ошибки во время выполнения программа будет прервана и произойдет возврат в отладчик. Это используемое по умолчанию поведение можно изменить для любой проверки во время выполнения. Дополнительные сведения см. в статье [Управление исключениями с помощью отладчика](../debugger/managing-exceptions-with-the-debugger.md).

  В приведенной ниже процедуре описано, как включить в отладочном построении проверку в машинных кодах во время выполнения, и как изменить поведение проверки в машинных кодах во время выполнения.

  Другие разделы, представленные здесь, содержат следующие сведения:

- [Настройка проверки кода во время выполнения с библиотекой среды выполнения языка C](../debugger/native-run-time-checks-customization.md)

### <a name="to-enable-native-run-time-checks-in-a-debug-build"></a>Включение проверок в машинных кодах во время выполнения в отладочном построении

- Используйте опцию **/RTC** и компоновку с отладочной версией библиотеки времени выполнения языка С (например, /MDd).

### <a name="to-modify-native-run-time-check-behavior"></a>Изменение порядка проверки в машинных кодах во время выполнения

- Используйте директиву `runtime_checks` .

## <a name="see-also"></a>См. также
- [Отладка в Visual Studio](../debugger/index.yml)
- [Первое знакомство с отладчиком](../debugger/debugger-feature-tour.md)
- [runtime_checks](/cpp/preprocessor/runtime-checks)
- [Проверка ошибок во время выполнения](/cpp/c-runtime-library/run-time-error-checking)