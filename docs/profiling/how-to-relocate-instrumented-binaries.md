---
title: Как выполнить Перемещение инструментированных двоичных файлов | Документация Майкрософт
ms.date: 11/04/2016
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
ms.openlocfilehash: f8b50c5b76ea5b22bc9d734d32e433db1c7594d9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53893082"
---
# <a name="how-to-relocate-instrumented-binaries"></a>Как выполнить Перемещение инструментированных двоичных файлов

Во время инструментирования в двоичный файл вставляются зонды для измерения производительности приложения. При перемещении инструментированного двоичного файла копия оригинального двоичного файла инструментируется и помещается в указанное расположение. Этот вариант полезен, если вы не хотите, чтобы профилировщик переименовал ваш исходный двоичный файл. Если двоичный файл не перемещается, будет перезаписана оригинальная версия двоичного файла.

## <a name="to-relocate-instrumented-binary"></a>Перемещение инструментированного двоичного файла

1. В **обозревателе производительности**щелкните правой кнопкой мыши сеанс производительности, а затем выберите **Свойства**.

2. На **страницах свойств**щелкните пункт **Двоичный файл** .

3. Установите флажок **Переместить инструментированные двоичные файлы** .

4. Укажите расположение для инструментированного двоичного файла.

## <a name="see-also"></a>См. также

[Настройка сеансов анализа производительности](../profiling/configuring-performance-sessions.md)  
[VSInstr](../profiling/vsinstr.md)
