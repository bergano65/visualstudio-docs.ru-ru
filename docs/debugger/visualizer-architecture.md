---
title: Архитектура визуализатора | Документация Майкрософт
description: Визуализатор используется для отображения элемента данных конкретного типа, а также поддерживает возможность редактирования. В этом разделе приводятся сведения об архитектуре визуализатора.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 6aad395f-7170-4d9e-b2b8-a5faf453380e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9df1dfa1912c54d30c5c428ec59de9432fe68051
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884251"
---
# <a name="visualizer-architecture"></a>Архитектура визуализатора
Архитектура визуализатора отладчика состоит из двух частей:

- *Сторона отладчика* — код, который запускается в отладчике Visual Studio. Код со стороны отладчика создает и отображает пользовательский интерфейс визуализатора.

- *Сторона отлаживаемого кода* — код, который выполняется внутри процесса, отлаживаемого в Visual Studio (*отлаживаемая* программа).

  Визуализатор является компонентом отладчика, который позволяет отладчику отображать (*визуализировать*) содержимое объекта данных в удобочитаемом, понятном виде. Некоторые визуализаторы поддерживают также редактирование объекта данных. Путем написания пользовательских визуализаторов можно расширить возможности отладчика для обработки пользовательских типов данных.

  Объект данных, который будет отображен, находится в пределах процесса отладки (*отлаживаемый* процесс). Пользовательский интерфейс, который будет отображать данные, создается в пределах процесса отладчика Visual Studio:

|Процесс отладчика|Отлаживаемый процесс|
|----------------------|----------------------|
|Пользовательский интерфейс отладчика (подсказки, окно "Контрольное значение", окно "Быстрая проверка")|Объект данных для отображения|

 Для визуализации объекта данных в пределах интерфейса отладчика требуется код для обмена данными между двумя процессами. Таким образом, архитектура визуализатора состоит из двух компонентов: кода *стороны отладчика* и кода *стороны отлаживаемого объекта*.

 Код стороны отладчика создает свой собственный интерфейс пользователя, к которому может обращаться интерфейс отладчика, например, окно подсказки, окно контрольного значения или окно быстрой проверки. Интерфейс визуализатора создан с помощью класса <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> и интерфейса <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService>. Как все API визуализатора, DialogDebuggerVisualizer и IDialogVisualizerService находятся в пространстве имен <xref:Microsoft.VisualStudio.DebuggerVisualizers>.

|Сторона отладчика|Сторона отлаживаемого объекта|
|-------------------|-------------------|
|Класс DialogDebuggerVisualizer<br /><br /> Интерфейс IDialogVisualizerService|Объект данных|

 Пользовательский интерфейс получает данные для отображения от поставщика объектов, который существует на стороне отладчика:

|Сторона отладчика|Сторона отлаживаемого объекта|
|-------------------|-------------------|
|Класс DialogDebuggerVisualizer<br /><br /> Интерфейс IDialogVisualizerService|Объект данных|
|Поставщик объектов (реализует <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider>)||

 Существует соответствующий объект на стороне отлаживаемого кода — источник объектов:

|Сторона отладчика|Сторона отлаживаемого объекта|
|-------------------|-------------------|
|Класс DialogDebuggerVisualizer<br /><br /> Интерфейс IDialogVisualizerService|Объект данных|
|Поставщик объектов (реализует <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider>)|Источник объектов (производный от <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>)|

 Поставщик объектов предоставляет объект данных для отображения в пользовательском интерфейсе визуализатора. Поставщик объектов получает объект данных от источника объектов. Поставщик объектов и источник объектов предоставляют API для обмена данными объекта между сторонами отладчика и отлаживаемого кода.

 Каждый визуализатор должен получить объект данных для отображения. В следующей таблице показаны соответствующие API, которые поставщик объектов и источник объектов используют для этой цели:

|Поставщик объектов|Источник объектов|
|---------------------|-------------------|
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A><br /><br /> —или—<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A>|

 Обратите внимание, что поставщик объектов может использовать как <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A>, так и <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A>. Любой API приводит к вызову <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A> для источника объектов. Вызов <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A?displayProperty=fullName> заполняет <xref:System.IO.Stream?displayProperty=fullName>, который представляет сериализованную форму визуализируемого объекта.

 Метод <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A?displayProperty=fullName> десериализует данные обратно в форму объекта, которую затем можно отобразить в пользовательском интерфейсе, создаваемом с помощью класса <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>. Метод <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName> заполняет данные и возвращает их в качестве необработанного объекта `Stream`, который необходимо десериализовать отдельно. <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A?displayProperty=fullName> вызывает <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName> для получения сериализованных данных `Stream`, а затем десериализует данные. Используйте <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName>, когда объект не является сериализуемым средствами .NET и требует пользовательской сериализации. В этом случае необходимо также переопределить метод <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.Serialize%2A?displayProperty=fullName>.

 Если нужен визуализатор только для чтения, достаточно односторонней связи с помощью <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A> или <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A>. Если вы создаете визуализатор с поддержкой редактирования объектов данных, необходимо сделать больше. Необходимо иметь также возможность для отправки объекта данных от поставщика объектов обратно источнику. В следующей таблице показаны API поставщика и источника объектов, используемые для этой цели:

|Поставщик объектов|Источник объектов|
|---------------------|-------------------|
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A><br /><br /> —или—<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.CreateReplacementObject%2A>|

 Обратите внимание, что поставщик объектов может использовать два API. Данные всегда посылаются от поставщика объектов источнику как `Stream`, но метод <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A> требует отдельной сериализации объекта в `Stream`.

 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceObject%2A> принимает объект, сериализует его в `Stream`, затем вызывает метод <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A> для отправки `Stream` в <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.CreateReplacementObject%2A>.

 С помощью одного из методов Replace создается новый объект данных в отлаживаемом коде, который заменяет объект визуализации. Если надо изменить содержимое исходного объекта без его замены, воспользуйтесь одним из методов Transfer, показанных в следующей таблице. Эти API передают данные в обоих направлениях одновременно, без замены визуализируемого объекта:

|Поставщик объектов|Источник объектов|
|---------------------|-------------------|
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.TransferData%2A><br /><br /> —или—<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.TransferObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.TransferData%2A>|

## <a name="see-also"></a>См. также
- [Практическое руководство. Написание визуализатора](create-custom-visualizers-of-data.md)
- [Пошаговое руководство: Написание визуализатора на C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)
- [Пошаговое руководство: Написание визуализатора на Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)
- [Пошаговое руководство: Написание визуализатора на Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)
- [Вопросы безопасности визуализатора](../debugger/visualizer-security-considerations.md)