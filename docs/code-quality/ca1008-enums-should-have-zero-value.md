---
title: "CA1008: перечисляемые Перечисления должны иметь нулевое значение | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1008
- EnumsShouldHaveZeroValue
helpviewer_keywords:
- CA1008
- EnumsShouldHaveZeroValue
ms.assetid: 3503a73c-360c-416d-8ee4-c2aa44365a05
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 84c43a95cd607a13a302e2247cacb091a39a3070
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca1008-enums-should-have-zero-value"></a>CA1008: перечисляемые типы должны иметь нулевое значение
|||  
|-|-|  
|TypeName|EnumsShouldHaveZeroValue|  
|CheckId|CA1008|  
|Категория|Microsoft.Design|  
|Критическое изменение|Не критическое — при появлении предложения добавить **нет** значение перечисления без флага. Критическое — если приглашение переименовать или удалить все значения перечисления.|  
  
## <a name="cause"></a>Причина  
 Перечисление без примененного <xref:System.FlagsAttribute?displayProperty=fullName> не определяет член, имеющий значение равно нулю; или перечисление с примененным примененного <xref:System.FlagsAttribute> определяет элемент, имеет нулевое значение, но его имя не является «None» или перечисление определяет несколько нулевым значением элементы.  
  
## <a name="rule-description"></a>Описание правила  
 Значение по умолчанию неинициализированного перечисления, как и других типов значений, равно нулю. Перечисление без флагов атрибутов должно определять член с нулевым значением, чтобы значение по умолчанию является допустимым значением перечисления. При необходимости, имя члена «None». В противном случае присвойте ноль наиболее часто используемых элементов. Обратите внимание, что по умолчанию, если значение первого элемента перечисления не указано в объявлении, его значение равно нулю.  
  
 Если перечисление с примененным <xref:System.FlagsAttribute> применения определяет член с нулевым значением, его имя должно быть «None», чтобы указать, что не были заданы значения в перечислении. С помощью член с нулевым значением для других целей противоречит использование <xref:System.FlagsAttribute> в том, что и и или битовые операторы смысла для члена. Это означает, что в нулевое значение следует назначать только одному члену. Обратите внимание, что несколько элементов, имеющих нулевое значение появление в перечислении флагами в качестве атрибутов, `Enum.ToString()` возвращает неверные результаты для членов, которые не равны нулю.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение этого правила для перечислений без флагов атрибутов, определите член, имеющий значение равно нулю; Это некритическое изменение. Для перечислений, флаги в качестве атрибутов, которые определяют член с нулевым значением назовите этот член «None» и удалите любые другие члены, которые имеют значение равно нулю; Это критическое изменение.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Не отключайте предупреждение из этого правила, за исключением атрибутов флаги перечисления, которые были предоставлены ранее.  
  
## <a name="example"></a>Пример  
 В следующем примере показано два перечисления, которые удовлетворяют правилу и перечисления, `BadTraceOptions`, которое нарушает правило.  
  
 [!code-cpp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CPP/ca1008-enums-should-have-zero-value_1.cpp)]
 [!code-csharp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CSharp/ca1008-enums-should-have-zero-value_1.cs)]
 [!code-vb[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/VisualBasic/ca1008-enums-should-have-zero-value_1.vb)]  
  
## <a name="related-rules"></a>Связанные правила  
 [CA2217: не следует помечать перечисления атрибутом FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
 [CA1700: не следует называть значения перечислений именем "Reserved"](../code-quality/ca1700-do-not-name-enum-values-reserved.md)  
  
 [CA1712: не добавляйте имя типа перед перечисляемыми значениями](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)  
  
 [CA1028: хранилище перечислений должно иметь тип Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)  
  
 [CA1027: следует помечать перечисления атрибутом FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
## <a name="see-also"></a>См. также  
 <xref:System.Enum?displayProperty=fullName>