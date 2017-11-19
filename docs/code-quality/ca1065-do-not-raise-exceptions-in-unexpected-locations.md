---
title: "CA1065: Не вызывайте исключения в непредвиденных местах | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1065
- DoNotRaiseExceptionsInUnexpectedLocations
helpviewer_keywords:
- DoNotRaiseExceptionsInUnexpectedLocations
- CA1065
ms.assetid: 4e1bade4-4ca2-4219-abc3-c7b2d741e157
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3511778536bb9664726fc9a61b4773c209a0fd46
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca1065-do-not-raise-exceptions-in-unexpected-locations"></a>CA1065: не вызывайте исключения в непредвиденных местах
|||  
|-|-|  
|TypeName|DoNotRaiseExceptionsInUnexpectedLocations|  
|CheckId|CA1065|  
|Категория|Microsoft.Design|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Метод вызывает исключение, хотя не должен этого делать.  
  
## <a name="rule-description"></a>Описание правила  
 Методы, которые не должны вызывать исключения можно классифицировать следующим образом:  
  
-   Методы Get свойства  
  
-   Методы доступа к событиям  
  
-   Методы Equals  
  
-   Методы GetHashCode  
  
-   Методы ToString  
  
-   Статические конструкторы  
  
-   Методы завершения  
  
-   Методы Dispose  
  
-   Операторы равенства  
  
-   Операторы неявного приведения  
  
 В следующих разделах рассматриваются эти типы методов.  
  
### <a name="property-get-methods"></a>Методы Get свойства  
 Свойства — в основном смарт-поля. Таким образом они должны соответствовать поведению максимально поля. Поля, которые не вызывают исключений и свойства. Если у вас есть свойство, которое вызывает исключение, имеет смысл сделать его метод.  
  
 Следующие исключения могут возникать из метода получения свойства.  
  
-   <xref:System.InvalidOperationException?displayProperty=fullName>и все производные (включая <xref:System.ObjectDisposedException?displayProperty=fullName>)  
  
-   <xref:System.NotSupportedException?displayProperty=fullName>и все производные  
  
-   <xref:System.ArgumentException?displayProperty=fullName>(только из индексированного get)  
  
-   <xref:System.Collections.Generic.KeyNotFoundException>(только из индексированного get)  
  
### <a name="event-accessor-methods"></a>Методы доступа к событиям  
 К событиям должно быть простые операции, которые не способны вызывать исключения. Событие не должно создавать исключения при попытке добавления или удаления обработчика событий.  
  
 Следующие исключения могут вызываться из доступа к событию.  
  
-   <xref:System.InvalidOperationException?displayProperty=fullName>и все производные (включая <xref:System.ObjectDisposedException?displayProperty=fullName>)  
  
-   <xref:System.NotSupportedException?displayProperty=fullName>и все производные  
  
-   <xref:System.ArgumentException>и производные  
  
### <a name="equals-methods"></a>Методы Equals  
 Следующие **равняется** методы не должны вызывать исключения:  
  
-   <xref:System.Object.Equals%2A?displayProperty=fullName>  
  
-   [M:IEquatable.Equals](http://go.microsoft.com/fwlink/?LinkId=113472)  
  
 **Равняется** метод должен возвращать `true` или `false` вместо создания исключения. Например, если равно передается два несовместимых типов она просто возвращает `false` вместо создания <xref:System.ArgumentException>.  
  
### <a name="gethashcode-methods"></a>Методы GetHashCode  
 Следующие **GetHashCode** методы обычно не должны вызывать исключения:  
  
-   <xref:System.Object.GetHashCode%2A>  
  
-   [M:IEqualityComparer.GetHashCode(T)](http://go.microsoft.com/fwlink/?LinkId=113477)  
  
 **GetHashCode** всегда должны возвращать значение. В противном случае вы можете потерять элементов в хэш-таблице.  
  
 Версии **GetHashCode** , которые принимают аргумент может вызывать <xref:System.ArgumentException>. Тем не менее **Object.GetHashCode** никогда не должно создавать исключения.  
  
### <a name="tostring-methods"></a>Методы ToString  
 Отладчик использует <xref:System.Object.ToString%2A?displayProperty=fullName> для отображения сведений об объектах в строковом формате. Таким образом **ToString** не должны изменять состояние объекта и не должны вызывать исключения.  
  
### <a name="static-constructors"></a>Статические конструкторы  
 Создание исключений из статического конструктора в результате тип будет невозможно использовать в текущем домене приложения. Для создания исключения из статического конструктора должен иметь веская причина (например, проблема безопасности).  
  
### <a name="finalizers"></a>Методы завершения  
 Исключения из метода завершения среда CLR сбой быстрых, который отменяет процесс. Таким образом создание исключений в методе завершения следует избегать.  
  
### <a name="dispose-methods"></a>Методы Dispose  
 Объект <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> метода не должно создавать исключения. Метод Dispose часто вызывается как часть логики очистки в `finally` предложения. Таким образом, явный вызов исключения из метода Dispose вынуждает пользователя добавлять обработку исключений в `finally` предложения.  
  
 **Dispose(false)** путь кода никогда не должен выдавать исключения, так как это почти всегда вызывается из метода завершения.  
  
### <a name="equality-operators--"></a>Операторы равенства (==,! =)  
 Подобно методам Equals, операторы равенства должен возвращать `true` или `false` и не должны вызывать исключения.  
  
### <a name="implicit-cast-operators"></a>Операторы неявного приведения  
 Так как пользователь часто знает, что был вызван оператор неявное приведение, неожиданное исключение, создаваемое с помощью оператора неявное приведение. Таким образом не должен быть исключения из неявных операторов приведения.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Для методов получения свойства либо измените логику, чтобы он больше не порождает исключение, или измените свойство в метод.  
  
 Для всех других перечисленных типов методов измените логику, чтобы он больше не должен вызывать исключение.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Это безопасно подавить предупреждение из этого правила, если нарушение было вызвано объявлением исключения без создания исключений.  
  
## <a name="related-rules"></a>Связанные правила  
 [CA2219: не создавайте исключения в предложениях исключений](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)  
  
## <a name="see-also"></a>См. также  
 [Предупреждения конструктора](../code-quality/design-warnings.md)