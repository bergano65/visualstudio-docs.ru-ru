---
title: 'CA1065: Не вызывайте исключения в непредвиденных местах | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1065
- DoNotRaiseExceptionsInUnexpectedLocations
helpviewer_keywords:
- DoNotRaiseExceptionsInUnexpectedLocations
- CA1065
ms.assetid: 4e1bade4-4ca2-4219-abc3-c7b2d741e157
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 142322360d4ba1ffed6ef893bf02254548ee2705
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49887611"
---
# <a name="ca1065-do-not-raise-exceptions-in-unexpected-locations"></a>CA1065: не вызывайте исключения в непредвиденных местах
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotRaiseExceptionsInUnexpectedLocations|
|CheckId|CA1065|
|Категория|Microsoft.Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Метод вызывает исключение, хотя не должен этого делать.

## <a name="rule-description"></a>Описание правила
 Методы, которые не должны вызывать исключения можно классифицировать следующим образом.

- Методы Get свойства

- Методы доступа к событиям

- Методов Equals

- Методы GetHashCode

- Методы ToString

- Статические конструкторы

- Методы завершения

- Удаления методов

- Операторы равенства

- Операторы неявного приведения

  В следующих разделах рассматриваются эти типы методов.

### <a name="property-get-methods"></a>Методы Get свойства
 Свойства являются по сути интеллектуальные поля. Таким образом они должны ведут себя как поле насколько это возможно. Поля не вызывают исключений и свойства. Если у вас есть свойство, которое вызывает исключение, имеет смысл сделать его метод.

 Следующие исключения могут вызываться из метода получения свойства.

-   <xref:System.InvalidOperationException?displayProperty=fullName> и все производные (включая <xref:System.ObjectDisposedException?displayProperty=fullName>)

-   <xref:System.NotSupportedException?displayProperty=fullName> и все производные

-   <xref:System.ArgumentException?displayProperty=fullName> (только на индексированный метод получения)

-   <xref:System.Collections.Generic.KeyNotFoundException> (только на индексированный метод получения)

### <a name="event-accessor-methods"></a>Методы доступа к событиям
 К событиям должно быть простые операции, которые не вызывают исключений. Событие не должны вызывать исключение при попытке добавить или удалить обработчик событий.

 Следующие исключения могут быть созданы из к событию.

-   <xref:System.InvalidOperationException?displayProperty=fullName> и все производные (включая <xref:System.ObjectDisposedException?displayProperty=fullName>)

-   <xref:System.NotSupportedException?displayProperty=fullName> и все производные

-   <xref:System.ArgumentException> и производные

### <a name="equals-methods"></a>Методов Equals
 Следующие **равно** методы не должны вызывать исключения:

- <xref:System.Object.Equals%2A?displayProperty=fullName>

- [M:IEquatable.Equals](http://go.microsoft.com/fwlink/?LinkId=113472)

  **Равно** метод должен возвращать `true` или `false` вместо выдачи исключения. Например, если равно передается два несовместимых типов он должен просто вернуть `false` вместо выдачи <xref:System.ArgumentException>.

### <a name="gethashcode-methods"></a>Методы GetHashCode
 Следующие **GetHashCode** методы обычно не должны вызывать исключения:

- <xref:System.Object.GetHashCode%2A>

- [M:IEqualityComparer.GetHashCode(T)](http://go.microsoft.com/fwlink/?LinkId=113477)

  **GetHashCode** всегда должны возвращать значение. В противном случае вы можете потерять элементы в хэш-таблице.

  В версиях **GetHashCode** , которые принимают аргумент может вызвать исключение <xref:System.ArgumentException>. Тем не менее **Object.GetHashCode** никогда не должен создавать исключение.

### <a name="tostring-methods"></a>Методы ToString
 Отладчик использует <xref:System.Object.ToString%2A?displayProperty=fullName> обеспечивает отображение сведений об объектах в строковом формате. Таким образом **ToString** не должны изменять состояние объекта и не должны вызывать исключения.

### <a name="static-constructors"></a>Статические конструкторы
 Создание исключений из статический конструктор вызывает тип будет невозможно использовать в текущем домене приложения. Для создания исключения из статического конструктора должны иметь веская причина (например, проблема безопасности).

### <a name="finalizers"></a>Методы завершения
 Исключение из метода завершения приводит к среде CLR быстро прекращаться, которое отменяет процесс. Таким образом создание исключений в методе завершения следует избегать.

### <a name="dispose-methods"></a>Удаления методов
 Объект <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> метод не должен создавать исключение. Dispose часто вызывается как часть логики очистки в `finally` предложение. Таким образом, явное создание исключения из метода Dispose вынуждает пользователя добавить обработку исключений в `finally` предложение.

 **Dispose(false)** путь кода никогда не должен выдавать исключения, так как это почти всегда вызывается из метода завершения.

### <a name="equality-operators--"></a>Операторы равенства (==,! =)
 Как и методы Equals, операторы равенства должен возвращать `true` или `false` и не должны вызывать исключения.

### <a name="implicit-cast-operators"></a>Операторы неявного приведения
 Так как он часто знают, что был вызван оператор неявное приведение, неожиданное исключение, создаваемое с помощью оператора неявного приведения. Таким образом не должен быть исключения из неявных операторов приведения.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Для свойств либо измените логику, чтобы он больше не порождает исключение, или измените свойство в метод.

 Для всех других перечисленных типов методов измените логику, чтобы он больше не следует вызвать исключение.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение из этого правила, если нарушение было вызвано объявления исключения вместо исключения.

## <a name="related-rules"></a>Связанные правила
 [CA2219: не создавайте исключения в предложениях исключений](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)

## <a name="see-also"></a>См. также
 [Предупреждения конструктора](../code-quality/design-warnings.md)



