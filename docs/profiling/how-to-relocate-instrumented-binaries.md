---
title: Перемещение инструментированных двоичных файлов | Документация Майкрософт
description: Сведения о том, как во время инструментирования в двоичный файл вставляются зонды для измерения производительности приложения.
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.binaries
helpviewer_keywords:
- binaries, instrumented
- instrumentation, instrumented binaries
- instrumented binaries and relocating
- profiling tools, instrumented binaries
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 7c63a1ce67095696d590670327a1a33e2471c145
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907081"
---
# <a name="how-to-relocate-instrumented-binaries"></a>Практическое руководство. Перемещение инструментированных двоичных файлов

Во время инструментирования в двоичный файл вставляются зонды для измерения производительности приложения. При перемещении инструментированного двоичного файла копия оригинального двоичного файла инструментируется и помещается в указанное расположение. Этот вариант полезен, если вы не хотите, чтобы профилировщик переименовал ваш исходный двоичный файл. Если двоичный файл не перемещается, будет перезаписана оригинальная версия двоичного файла.

## <a name="to-relocate-instrumented-binary"></a>Перемещение инструментированного двоичного файла

1. В **обозревателе производительности** щелкните правой кнопкой мыши сеанс производительности, а затем выберите **Свойства**.

2. На **страницах свойств** щелкните пункт **Двоичный файл** .

3. Установите флажок **Переместить инструментированные двоичные файлы** .

4. Укажите расположение для инструментированного двоичного файла.

## <a name="see-also"></a>См. также

[Настройка сеансов анализа производительности](../profiling/configuring-performance-sessions.md)
[VSInstr](../profiling/vsinstr.md)
