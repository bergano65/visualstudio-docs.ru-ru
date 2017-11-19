---
title: "CA1819: Свойства не должны возвращать массивы | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
helpviewer_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
ms.assetid: 85fcf312-57f8-438a-8b10-34441fe0bdeb
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2bd2aae360789646c78fa6b292b1ad97490fc2da
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
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
 Массивы, возвращаемые свойствами, не защищены от записи, даже если свойство доступно только для чтения. Чтобы защитить массив от изменений, свойство должно возвращать копию массива. Как правило, пользователи не понимают требований к производительности при вызове такого свойства. В частности они могут использовать свойство как индексированное свойство.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, сделайте свойство метода или измените свойство для возврата коллекции.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Атрибуты могут содержать свойства, которые возвращают массивы, но не может содержать свойства, которые возвращают коллекции. Можно подавить предупреждение, вызывается для свойства атрибута, который является производным от <xref:System.Attribute> класса. В противном случае не отключайте предупреждение из этого правила.  
  
## <a name="example-violation"></a>Пример нарушения  
  
### <a name="description"></a>Описание  
 Следующий пример показывает свойства, которое нарушает это правило.  
  
### <a name="code"></a>Код  
 [!code-csharp[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_1.cs)]
 [!code-vb[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_1.vb)]  
  
### <a name="comments"></a>Комментарии  
 Чтобы устранить нарушение данного правила, сделайте свойство метода или измените свойство, чтобы вернуть коллекцию вместо массива.  
  
## <a name="change-the-property-to-a-method-example"></a>Измените значение свойства на примере метод  
  
### <a name="description"></a>Описание  
 В следующем примере нарушение устраняется путем изменения свойства в метод.  
  
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
  
## <a name="allowing-users-to-modify-a-property"></a>Предоставление пользователям разрешения на изменение свойства  
  
### <a name="description"></a>Описание  
 Можно разрешить пользователю изменять свойство класса. В следующем примере свойство чтения/записи, которое нарушает это правило.  
  
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