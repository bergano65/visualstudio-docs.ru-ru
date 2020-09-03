---
title: 'CA1024: Используйте свойства, если это уместно | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UsePropertiesWhereAppropriate
- CA1024
helpviewer_keywords:
- CA1024
- UsePropertiesWhereAppropriate
ms.assetid: 3a04f765-af7c-4872-87ad-9cc29e8e657f
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a240a6eea86075bbf7f721f8620b6d135d594c20
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546670"
---
# <a name="ca1024-use-properties-where-appropriate"></a>CA1024. По возможности используйте свойства
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|UsePropertiesWhereAppropriate|
|CheckId|CA1024|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный метод имеет имя, начинающееся с `Get` , не принимает параметров и возвращает значение, которое не является массивом.

## <a name="rule-description"></a>Описание правила
 В большинстве случаев свойства представляют данные и методы выполняют действия. Доступ к свойствам аналогичен полям, что упрощает их использование. Метод является хорошим кандидатом для того, чтобы стать свойством при наличии одного из следующих условий:

- Не принимает аргументы и возвращает сведения о состоянии объекта.

- Принимает один аргумент для задания некоторой части состояния объекта.

  Свойства должны вести себя так, как если бы они были полями; Если метод не может, он не должен изменяться на свойство. Методы лучше, чем свойства в следующих ситуациях:

- Метод выполняет трудоемкую операцию. Метод перцеивабли медленнее, чем время, необходимое для задания или получения значения поля.

- Метод выполняет преобразование. При доступе к полю преобразованная версия хранимых данных не возвращается.

- Метод Get имеет наблюдаемый побочный результат. Получение значения поля не приводит к созданию побочных эффектов.

- Порядок выполнения важен. Установка значения поля не зависит от вхождения других операций.

- Вызов метода два раза подряд создает разные результаты.

- Метод является статическим, но возвращает объект, который может быть изменен вызывающим объектом. Получение значения поля не позволяет вызывающему объекту изменять данные, хранящиеся в поле.

- Метод возвращает массив.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, измените метод на свойство.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Подавлять предупреждение из этого правила, если метод удовлетворяет по крайней мере одному из перечисленных выше критериев.

## <a name="controlling-property-expansion-in-the-debugger"></a>Управление развертыванием свойств в отладчике
 Одна из причин того, что программисты не используют свойство, заключается в том, что они не хотят, чтобы отладчик выводил его на автоматическое расширение. Например, свойство может включать выделение большого объекта или вызов P/Invoke, но на самом деле он может не иметь наблюдаемых побочных эффектов.

 Можно запретить отладчику автоматическое развертывание свойств путем применения <xref:System.Diagnostics.DebuggerBrowsableAttribute?displayProperty=fullName> . В следующем примере показан этот атрибут, применяемый к свойству экземпляра.

```vb
Imports System
Imports System.Diagnostics

Namespace Microsoft.Samples

    Public Class TestClass

        ' [...]

        <DebuggerBrowsable(DebuggerBrowsableState.Never)> _
        Public ReadOnly Property LargeObject() As LargeObject
            Get
                ' Allocate large object
                ' [...]
            End Get
        End Property

    End Class

End Namespace
```

```csharp

      using System;
using System.Diagnostics;

namespace Microsoft.Samples
{
    publicclass TestClass
    {
        // [...]

        [DebuggerBrowsable(DebuggerBrowsableState.Never)]
        public LargeObject LargeObject
        {
            get
            {
                // Allocate large object
                // [...]

        }
    }
}
```

## <a name="example"></a>Пример
 Следующий пример содержит несколько методов, которые должны быть преобразованы в свойства, и несколько, которые не должны работать, так как они не ведут себя как поля.

 [!code-csharp[FxCop.Design.MethodsProperties#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.MethodsProperties/cs/FxCop.Design.MethodsProperties.cs#1)]
