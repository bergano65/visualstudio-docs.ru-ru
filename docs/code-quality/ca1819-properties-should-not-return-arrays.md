---
title: 'CA1819: свойства не должны возвращать массивы'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
helpviewer_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
ms.assetid: 85fcf312-57f8-438a-8b10-34441fe0bdeb
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 68f64d37a7616f095a86452353edc498d2d27f28
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/13/2018
ms.locfileid: "45549421"
---
# <a name="ca1819-properties-should-not-return-arrays"></a>CA1819: свойства не должны возвращать массивы

|||
|-|-|
|TypeName|PropertiesShouldNotReturnArrays|
|CheckId|CA1819|
|Категория|Microsoft.Performance|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный свойство в открытом типе возвращает массив.

## <a name="rule-description"></a>Описание правила
 Массивы, возвращаемые свойства не защищен от записи, даже если свойство доступно только для чтения. Чтобы защитить массив от изменений, свойство должно возвращать копию массива. Как правило, пользователи не понимают требований к производительности при вызове такого свойства. В частности они могут использовать свойство как индексированное свойство.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, сделайте свойство метод или измените свойства для возврата коллекции.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Атрибуты могут содержать свойства, которые возвращают массивы, но не могут содержать свойства, которые возвращают коллекции. Можно подавить предупреждение, которое возникает для свойства атрибута, который является производным от <xref:System.Attribute> класса. В противном случае не отключайте предупреждение из этого правила.

## <a name="example-violation"></a>Пример нарушения

### <a name="description"></a>Описание
 В следующем примере свойство, которое нарушает это правило.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_1.cs)]
 [!code-vb[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_1.vb)]

### <a name="comments"></a>Комментарии
 Чтобы устранить нарушение этого правила, сделайте свойство метод или измените свойства для возврата коллекции вместо массива.

## <a name="change-the-property-to-a-method-example"></a>Измените свойство на пример метода

### <a name="description"></a>Описание
 В следующем примере устраняется нарушение, изменив свойство в метод.

### <a name="code"></a>Код
 [!code-vb[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_2.vb)]
 [!code-csharp[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_2.cs)]

## <a name="return-a-collection-example"></a>Пример возврата коллекции

### <a name="description"></a>Описание
 В следующем примере нарушение устраняется путем изменения свойства для возврата

 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_3.cs)]
 [!code-vb[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_3.vb)]

## <a name="allowing-users-to-modify-a-property"></a>Разрешение пользователям изменять свойство

### <a name="description"></a>Описание
 Может потребоваться предоставить пользователю класса, для изменения свойства. В следующем примере свойство чтения/записи, которое нарушает это правило.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_4.cs)]
 [!code-vb[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_4.vb)]

### <a name="comments"></a>Комментарии
 В следующем примере нарушение устраняется путем изменения свойства для возврата <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>.

### <a name="code"></a>Код
 [!code-vb[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_5.vb)]
 [!code-csharp[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_5.cs)]

## <a name="related-rules"></a>Связанные правила
 [CA1024: используйте свойства, если это уместно](../code-quality/ca1024-use-properties-where-appropriate.md)