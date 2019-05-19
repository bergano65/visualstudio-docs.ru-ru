---
title: CA1024. По возможности используйте свойства
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- UsePropertiesWhereAppropriate
- CA1024
helpviewer_keywords:
- CA1024
- UsePropertiesWhereAppropriate
ms.assetid: 3a04f765-af7c-4872-87ad-9cc29e8e657f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: bfedb55c0dcdb1077faea03bca56488ab3da1525
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2019
ms.locfileid: "65842466"
---
# <a name="ca1024-use-properties-where-appropriate"></a>CA1024. По возможности используйте свойства

|||
|-|-|
|TypeName|UsePropertiesWhereAppropriate|
|CheckId|CA1024|
|Категория|Microsoft.Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина

Метод имеет имя, которое начинается с `Get`, не принимает никаких параметров и возвращает значение, которое не является массивом.

По умолчанию это правило считывает только открытые и защищенные методы, но это [можно настроить](#configurability).

## <a name="rule-description"></a>Описание правила

В большинстве случаев свойства представления данных и методы выполнения действия. Свойства доступны как поля, которые упрощает их использование. Метод является хорошим кандидатом преобразовать в свойство, если одно из следующих условий:

- Не принимает аргументы и возвращает сведения о состоянии объекта.

- Принимает один аргумент для задания некоторых часть состояния объекта.

Свойства должны вести себя так, будто они представляют поля; Если невозможно, метод он не должен изменяться к свойству. Методы работают лучше, чем свойства в следующих ситуациях:

- Этот метод выполняет длительную операцию. Метод ощутимо максимальное время, необходимое для установки или получения значения поля.

- Этот метод выполняет преобразование. Доступ к полю не возвращает преобразованную версию, она сохраняет данные.

- Метод Get имеет значительное влияние на стороне. Получение значения поля не создает никаких побочных эффектов.

- Важен порядок выполнения. Значение поля не полагаться на возникновение других операций.

- Вызов метода в два раза подряд, выдает различные результаты.

- Метод является статическим, но возвращает объект, который можно изменить в вызывающем объекте. Получение значения поля не позволяет вызывающему объекту изменять данные, хранящиеся в поле.

- Метод возвращает массив.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, измените метод на свойство.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Отключайте предупреждение из этого правила, если метод соответствует хотя бы один из перечисленных выше критериям.

## <a name="configurability"></a>Возможность настройки

Если у вас это правило из [анализаторы FxCop](install-fxcop-analyzers.md) (а не с помощью функций анализа статического кода), можно настроить, какие части вашей базы кода, чтобы применить это правило, в зависимости от их доступности. Например чтобы указать, что правило должно выполняться только для рабочей области не являющийся открытым API, добавьте следующую пару "ключ значение" файла editorconfig в проект:

```ini
dotnet_code_quality.ca1024.api_surface = private, internal
```

В этой категории (структуры) можно настроить этот параметр для только что это правило, для всех правил или для всех правил. Дополнительные сведения см. в разделе [анализаторы FxCop, Настройка](configure-fxcop-analyzers.md).

## <a name="control-property-expansion-in-the-debugger"></a>Элемент управления свойство расширения в отладчике

Одна из причин, программисты не использовать свойство — так как эти нежелательно отладчик должен его. Например свойство может включать выделение больших объектов или вызова P/Invoke, но он может фактически не иметь все наблюдаемые побочные эффекты.

Отладчик из свойства autoexpanding можно предотвратить, применив <xref:System.Diagnostics.DebuggerBrowsableAttribute?displayProperty=fullName>. В примере показан этот атрибут применяется к свойству экземпляра.

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
}
```

## <a name="example"></a>Пример

В следующем примере содержится несколько методов, который должен быть преобразован в свойства и следует не потому, что они не ведут себя как поля.

[!code-csharp[FxCop.Design.MethodsProperties#1](../code-quality/codesnippet/CSharp/ca1024-use-properties-where-appropriate_1.cs)]