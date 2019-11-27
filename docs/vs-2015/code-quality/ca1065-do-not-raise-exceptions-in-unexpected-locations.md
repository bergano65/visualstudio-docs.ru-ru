---
title: 'CA1065: не вызывайте исключения в непредвиденных расположениях | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1065
- DoNotRaiseExceptionsInUnexpectedLocations
helpviewer_keywords:
- DoNotRaiseExceptionsInUnexpectedLocations
- CA1065
ms.assetid: 4e1bade4-4ca2-4219-abc3-c7b2d741e157
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 439c6b5fc30be2e76eb6c0b6a44b1ec5226633b1
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295944"
---
# <a name="ca1065-do-not-raise-exceptions-in-unexpected-locations"></a>CA1065: не вызывайте исключения в непредвиденных местах
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotRaiseExceptionsInUnexpectedLocations|
|CheckId|CA1065|
|Категория|Microsoft. Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Метод вызывает исключение, хотя не должен этого делать.

## <a name="rule-description"></a>Описание правила
 Методы, которые не должны вызывать исключения, можно классифицировать следующим образом:

- Методы получения свойств

- Методы доступа к событиям

- Методы Equals

- Методы GetHashCode

- Методы ToString

- Статические конструкторы

- Методы завершения

- Методы Dispose

- Операторы равенства

- Операторы неявного приведения

  Эти типы методов обсуждаются в следующих разделах.

### <a name="property-get-methods"></a>Методы получения свойств
 Свойства — это, по сути, интеллектуальные поля. Поэтому они должны вести себя как поле как можно больше. Поля не создают исключений, и ни одно из них не должно быть свойством. Если у вас есть свойство, вызывающее исключение, рассмотрите возможность сделать его методом.

 Следующие исключения могут быть вызваны из метода Get свойства:

- <xref:System.InvalidOperationException?displayProperty=fullName> и все производные (включая <xref:System.ObjectDisposedException?displayProperty=fullName>)

- <xref:System.NotSupportedException?displayProperty=fullName> и все производные

- <xref:System.ArgumentException?displayProperty=fullName> (только из индексированного получения)

- <xref:System.Collections.Generic.KeyNotFoundException> (только из индексированного получения)

### <a name="event-accessor-methods"></a>Методы доступа к событиям
 Методы доступа к событиям должны быть простыми операциями, которые не создают исключения. При попытке добавления или удаления обработчика событий событие не должно вызывать исключение.

 Следующие исключения могут вызываться из акцесор событий:

- <xref:System.InvalidOperationException?displayProperty=fullName> и все производные (включая <xref:System.ObjectDisposedException?displayProperty=fullName>)

- <xref:System.NotSupportedException?displayProperty=fullName> и все производные

- <xref:System.ArgumentException> и производные

### <a name="equals-methods"></a>Методы Equals
 Следующие методы **Equals** не должны вызывать исключения.

- <xref:System.Object.Equals%2A?displayProperty=fullName>

- [м:иекуатабле.екуалс](https://go.microsoft.com/fwlink/?LinkId=113472)

  Метод **Equals** должен возвращать `true` или `false` вместо генерации исключения. Например, если Equals передается два несовпадающих типа, он должен просто возвращать `false` вместо создания <xref:System.ArgumentException>.

### <a name="gethashcode-methods"></a>Методы GetHashCode
 Следующие методы **GetHashCode** обычно должны не создавать исключения:

- <xref:System.Object.GetHashCode%2A>

- [М:иекуалитикомпарер.жесашкоде (T)](https://go.microsoft.com/fwlink/?LinkId=113477)

  **GetHashCode** всегда должен возвращать значение. В противном случае можно потерять элементы в хэш-таблице.

  Версии **GetHashCode** , которые принимают аргумент, могут вызывать <xref:System.ArgumentException>. Однако **Object. GetHashCode** никогда не должен вызывать исключение.

### <a name="tostring-methods"></a>Методы ToString
 Отладчик использует <xref:System.Object.ToString%2A?displayProperty=fullName> для просмотра сведений об объектах в строковом формате. Таким образом, **метод ToString** не должен изменять состояние объекта и не должен вызывать исключения.

### <a name="static-constructors"></a>Статические конструкторы
 Создание исключений из статического конструктора приводит к тому, что тип будет непригоден для использования в текущем домене приложения. У вас должна быть очень хорошая причина (например, проблемы с безопасностью) для генерации исключения из статического конструктора.

### <a name="finalizers"></a>Методы завершения
 Создание исключения из метода завершения приводит к тому, что среда CLR быстро завершает работу, что слезамиет процесс. Поэтому всегда следует избегать генерации исключений в методе завершения.

### <a name="dispose-methods"></a>Методы Dispose
 Метод <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> не должен вызывать исключение. Метод Dispose часто вызывается как часть логики очистки в предложении `finally`. Таким образом, явное создание исключения из Dispose приводит к тому, что пользователь добавляет обработку исключений в предложение `finally`.

 Путь кода **Dispose (false)** никогда не должен вызывать исключения, так как этот метод почти всегда вызывается методом завершения.

### <a name="equality-operators--"></a>Операторы равенства (= =,! =)
 Как и методы Equals, операторы равенства должны возвращать либо `true`, либо `false` и не должны вызывать исключения.

### <a name="implicit-cast-operators"></a>Операторы неявного приведения
 Поскольку пользователь часто не знает, что был вызван неявный оператор приведения, исключение, созданное неявным оператором приведения, является полностью непредвиденным. Поэтому исключения не должны вызываться из неявных операторов приведения.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Для методов получения свойств либо измените логику так, чтобы она больше не вызывала исключение, либо измените свойство в методе.

 Для всех других типов методов, перечисленных ранее, измените логику так, чтобы она больше не вызывала исключение.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Предупреждение из этого правила можно отключить, если нарушение было вызвано объявлением исключения вместо выданного исключения.

## <a name="related-rules"></a>Связанные правила
 [CA2219: не создавайте исключения в предложениях исключений](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)

## <a name="see-also"></a>См. также
 [Предупреждения конструктора](../code-quality/design-warnings.md)
