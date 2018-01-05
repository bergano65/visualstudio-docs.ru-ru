---
title: "CA1406: Не следует использовать аргументы Int64 для клиентов Visual Basic 6 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
helpviewer_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
ms.assetid: d5d0d3fc-f105-43da-be5b-923ab023309c
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ed47a2ccea76ce9cb6e2a1ef6dd73d53c961544c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ca1406-avoid-int64-arguments-for-visual-basic-6-clients"></a>CA1406: не следует использовать аргументы Int64 для клиентов Visual Basic 6
|||  
|-|-|  
|TypeName|AvoidInt64ArgumentsForVB6Clients|  
|CheckId|CA1406|  
|Категория|Microsoft.Interoperability|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Тип, который специально помечен как видимый для модели объектов компонентов (COM) объявляет член, принимающую <xref:System.Int64?displayProperty=fullName> аргумент.  
  
## <a name="rule-description"></a>Описание правила  
 Клиенты COM Visual Basic 6 не может получить доступ к 64-разрядных целых чисел.  
  
 По умолчанию, являются видимыми для COM следующие: сборки, открытые типы, члены общих экземпляров в открытых типах и все элементы общих типов значений. Однако во избежание ложных положительных результатов, это правило требует видимость COM типа требуется явно указывать; содержащей сборки должны быть отмечены <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> значение `false` и тип должен быть помечен атрибутом <xref:System.Runtime.InteropServices.ComVisibleAttribute> значение `true`.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила для параметра, значение которого всегда может быть выражен как 32-разрядного целого числа, измените тип параметра для <xref:System.Int32?displayProperty=fullName>. Если значение параметра может быть больше, чем может быть выражен как 32-разрядного целого числа, измените тип параметра, чтобы <xref:System.Decimal?displayProperty=fullName>. Обратите внимание, что оба <xref:System.Single?displayProperty=fullName> и <xref:System.Double?displayProperty=fullName> происходит потеря точности в верхнем диапазоны <xref:System.Int64> тип данных. Если элемент не должен быть видимым для COM, пометьте его с <xref:System.Runtime.InteropServices.ComVisibleAttribute> значение `false`.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Это безопасно подавить предупреждение из этого правила, если известно, что клиенты COM Visual Basic 6 не будет доступа к типу.  
  
## <a name="example"></a>Пример  
 В следующем примере показано тип, нарушающий правило.  
  
 [!code-csharp[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/CSharp/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.cs)]
 [!code-vb[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/VisualBasic/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.vb)]  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1413: избегайте использования не открытых полей в видимых типах значений COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)  
  
 [CA1407: не используйте статические члены в видимых COM типах](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)  
  
 [CA1017: помечайте сборки атрибутом ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## <a name="see-also"></a>См. также  
 [Взаимодействие с неуправляемым кодом](/dotnet/framework/interop/index)   
 [Тип данных Long](/dotnet/visual-basic/language-reference/data-types/long-data-type)