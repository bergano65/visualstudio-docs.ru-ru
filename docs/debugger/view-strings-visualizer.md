---
title: Просмотр строк в визуализаторе строка | Документация Майкрософт
ms.date: 04/08/2019
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JavaScript
helpviewer_keywords:
- string visualizer
- visualizers, string
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ffd19dccb69d3ae05a84ae49a280ff49c14f2809
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59367312"
---
# <a name="view-strings-in-a-string-visualizer-in-visual-studio"></a>Просмотр строк в визуализатор строки в Visual Studio

При отладке в Visual Studio, можно просмотреть строки с помощью визуализатора встроенным строковым. Визуализатор строки показаны строки, которые слишком длинны для окна подсказки или отладчик данных. Он также поможет выявить неправильный формат строки.

Включает встроенный строковый визуализатор обычного текста, XML, HTML и JSON параметров. Также можно открыть встроенные визуализаторы для некоторых других типов, таких как [DataSet, DataTable и DataView](../debugger/dataset-visualizer-dialog-box.md) объекты, от **"Видимые"** или других окнах отладчика.

> [!NOTE]
> Если вам нужно проверять элементы XAML или пользовательского интерфейса WPF в средстве визуализации, см. в разделе или [свойства проверять XAML во время отладки](../debugger/inspect-xaml-properties-while-debugging.md) или [Практическое использование визуализатора дерева WPF](../debugger/how-to-use-the-wpf-tree-visualizer.md).

## <a name="open-a-string-visualizer"></a>Открыть визуализатор строки

Чтобы открыть визуализатор строки, должен быть приостановлен во время отладки. Наведите курсор на переменную, которая имеет обычный текст, XML, HTML или JSON строковое значение и щелкните значок лупы ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "значок визуализатор").

![Открыть визуализатор строки](../debugger/media/dbg-tips-string-visualizers.png "визуализатор откройте строки")

## <a name="view-string-visualizer-data"></a>Просмотр данных визуализатора строки

В окне визуализатора строки **выражение** поле показывает, переменную или выражение при наведении указателя, и **значение** поле отображается строковое значение.

Пустое **значение** означает, что выбранный визуализатор не может распознать строку. Например **визуализатор XML** показано пустое **значение** строку текста без тегов XML, или строку JSON.

Чтобы просмотреть строки, не может распознать выбранного визуализатор, выберите **визуализатор текста**. **Визуализатор текста** показан обычный текст.

### <a name="view-json-string-data"></a>Представление JSON строковых данных

Правильный формат строки JSON выглядит как на следующем рисунке в визуализатор JSON. Неправильно сформированный JSON может отображать значок ошибки (или остается пустым, если нераспознанный). Чтобы определить ошибку, JSON, скопируйте и вставьте строку в средство анализа кода JSON, такие как [JSLint](https://www.jslint.com/).

![Визуализатор строки JSON](../debugger/media/dbg-tips-string-visualizer-json.png "визуализатор строки JSON")

### <a name="view-xml-string-data"></a>Строка XML-представление данных

Правильный формат XML-строку выглядит как на следующем рисунке в визуализаторе XML. Некорректный код XML может отображать без тегов XML либо пуст, если нераспознанный.

![Визуализатор строки XML](../debugger/media/dbg-string-visualizers-xml.png "визуализатор строки XML")

### <a name="view-html-string-data"></a>Просмотр HTML строковых данных

Правильный формат строки HTML отображается так, как если Визуализированный в браузере, как показано на следующем рисунке. Неправильный формат HTML могут отображаться в виде обычного текста.

![HTML-визуализатор строки](../debugger/media/dbg-string-visualizers-html.png "HTML-визуализатор строки")

## <a name="see-also"></a>См. также

- [Создание настраиваемых визуализаторов (C#, Visual Basic)](../debugger/create-custom-visualizers-of-data.md)
- [Визуализации данных в Visual Studio для Mac](/visualstudio/mac/data-visualizations)