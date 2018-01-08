---
title: "Просмотр строк в визуализатор строки | Документы Microsoft"
ms.custom: 
ms.date: 07/11/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vs.debug.stringviewer
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- string visualizer
- visualizers, string
ms.assetid: 080fd8f1-72b0-461f-8451-3c84d5dc51df
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 801618c900f11a562b42e610c56dfa7855dfaf39
ms.sourcegitcommit: 9e6ff74da1afd8bd2f0e69387ce81f2a74619182
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/04/2018
---
# <a name="view-strings-in-a-string-visualizer-in-visual-studio"></a>Просмотр строк в визуализатор строки в Visual Studio
При отладке, можно открыть визуализатор строки на представление строки, которые слишком длинны для просмотра в окне подсказки или отладчик данных. Во многих сценариях визуализатора может помочь определить имеет неправильный формат строки.

Строка стандартного встроенные визуализаторы включают обычного текста, XML, HTML и JSON. Несколько других типов, таких как WPF для объектов в отладчике windows, например **видимые** окна, можно также открыть визуализаторов.

## <a name="open-a-string-visualizer"></a>Открытие визуализатора строки

Чтобы просмотреть обычного текста, XML, HTML или JSON строку, щелкните значок лупы ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "значок визуализатор") при наведении указателя мыши на переменную, содержащий строковое значение. Вы должен быть приостановлен в отладчике появляется значок лупы.

![Открыть визуализатор строки](../debugger/media/dbg-tips-string-visualizers.png "OpenStringVisualizer")

## <a name="view-string-data"></a>Представление строковых данных

**Выражение** поля в визуализатор строки показывает текущую переменную или выражение при прохождении курсора над в отладчике.

**Значение** поле отображается значение строки. Средство визуализации текста показаны в виде обычного текста.

Пустое **значение** указывает, что определенные визуализатор не удалось распознать строкового типа. Например, визуализатор XML показывает пустым **значение** для простую текстовую строку (с не XML-тегов) или JSON форматированную строку. Если вам нужно просмотреть неопознанное строку в средстве визуализации, используйте средство визуализации текста.

### <a name="view-json-string-data"></a>Представление JSON строковых данных

Строка формата JSON будет выглядеть следующим образом в визуализатор JSON. Неправильный формат JSON может отображать значок ошибки (или остается пустым, если нераспознанный).

![Визуализатор строки JSON](../debugger/media/dbg-tips-string-visualizer-json.png "визуализатор строки JSON")

### <a name="view-xml-string-data"></a>Строка XML-представление данных

Корректный XML-строки будет выглядеть следующим образом в визуализаторе XML. Без тегов XML (или остается пустым, если нераспознанный) могут отображаться неправильно сформированный XML.

![Визуализатор строки XML](../debugger/media/dbg-string-visualizers-xml.png "визуализатор строки XML")

### <a name="view-html-string-data"></a>Представление HTML строковых данных

Строка формата HTML выводит представление, которые появляются при строка отображается в браузере, как показано на следующем рисунке. Код HTML неправильного формата может отображаться в виде обычного текста.

![Визуализатор строки HTML](../debugger/media/dbg-string-visualizers-html.png "визуализатор HTML-строки")

## <a name="see-also"></a>См. также  
 [Создание пользовательских визуализаторов (C#, Visual Basic)](../debugger/create-custom-visualizers-of-data.md)