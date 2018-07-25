---
title: Практическое руководство. Перемещение инструментированных двоичных файлов | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.binaries
helpviewer_keywords:
- binaries, instrumented
- instrumentation, instrumented binaries
- instrumented binaries and relocating
- profiling tools, instrumented binaries
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a060506f818ac000611fc0c29988ed324ae89226
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2018
ms.locfileid: "34843657"
---
# <a name="how-to-relocate-instrumented-binaries"></a>Практическое руководство. Перемещение инструментированных двоичных файлов

Во время инструментирования в двоичный файл вставляются зонды для измерения производительности приложения. При перемещении инструментированного двоичного файла копия оригинального двоичного файла инструментируется и помещается в указанное расположение. Этот вариант полезен, если вы не хотите, чтобы профилировщик переименовал ваш исходный двоичный файл. Если двоичный файл не перемещается, будет перезаписана оригинальная версия двоичного файла.

## <a name="to-relocate-instrumented-binary"></a>Перемещение инструментированного двоичного файла

1. В **обозревателе производительности**щелкните правой кнопкой мыши сеанс производительности, а затем выберите **Свойства**.

2. На **страницах свойств**щелкните пункт **Двоичный файл** .

3. Установите флажок **Переместить инструментированные двоичные файлы** .

4. Укажите расположение для инструментированного двоичного файла.

## <a name="see-also"></a>См. также

[Настройка сеансов анализа производительности](../profiling/configuring-performance-sessions.md)  
[VSInstr](../profiling/vsinstr.md)
