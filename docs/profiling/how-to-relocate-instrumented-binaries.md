---
title: Практическое руководство. Перемещение инструментированных двоичных файлов | Документы Майкрософт
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
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: cddbb0b3e27b841441937b7256ea32d722e25f5e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "74774904"
---
# <a name="how-to-relocate-instrumented-binaries"></a>Практическое руководство. Перемещение инструментированных двоичных файлов

Во время инструментирования в двоичный файл вставляются зонды для измерения производительности приложения. При перемещении инструментированного двоичного файла копия оригинального двоичного файла инструментируется и помещается в указанное расположение. Этот вариант полезен, если вы не хотите, чтобы профилировщик переименовал ваш исходный двоичный файл. Если двоичный файл не перемещается, будет перезаписана оригинальная версия двоичного файла.

## <a name="to-relocate-instrumented-binary"></a>Перемещение инструментированного двоичного файла

1. В **обозревателе производительности**щелкните правой кнопкой мыши сеанс производительности, а затем выберите **Свойства**.

2. На **страницах свойств**щелкните пункт **Двоичный файл** .

3. Установите флажок **Переместить инструментированные двоичные файлы** .

4. Укажите расположение для инструментированного двоичного файла.

## <a name="see-also"></a>См. также раздел

[Настройка сеансов анализа производительности](../profiling/configuring-performance-sessions.md)
[VSInstr](../profiling/vsinstr.md)
