---
title: "CA1413: Избегайте использования не открытых полей в видимых типах значений COM | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
helpviewer_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
ms.assetid: 1352e7eb-fefc-4239-8847-25edc7804a54
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e8dc7c435d9f853cfb67f7c45f5ec7116ff6fb8e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca1413-avoid-non-public-fields-in-com-visible-value-types"></a>CA1413: избегайте использования не открытых полей в видимых типах значений COM
|||  
|-|-|  
|TypeName|AvoidNonpublicFieldsInComVisibleValueTypes|  
|CheckId|CA1413|  
|Категория|Microsoft.Interoperability|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Тип значения, который специально помечен как видимый для модели объектов компонентов (COM) объявляет поле закрытого экземпляра.  
  
## <a name="rule-description"></a>Описание правила  
 Не являющиеся общедоступными поля экземпляров типов значений, отображаемых для модели COM, отображаются для COM-клиентов. Проверьте содержимое полей сведения, не следует делать видимыми, или которые могут оказать нежелательное воздействие на разработку или безопасность.  
  
 По умолчанию все открытые типы значений являются видимыми для COM. Однако во избежание ложных положительных результатов, это правило требует видимость COM необходимо явно указать тип. Содержащей сборки должны быть отмечены <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> значение `false` и тип должен быть помечен атрибутом <xref:System.Runtime.InteropServices.ComVisibleAttribute> значение `true`.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила и сохранить скрытые поля, измените тип значения в ссылочный тип или удалите <xref:System.Runtime.InteropServices.ComVisibleAttribute> атрибут на основе типа.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Это безопасно подавить предупреждение из этого правила, если допустима раскрытию поля.  
  
## <a name="example"></a>Пример  
 В следующем примере показано тип, нарушающий правило.  
  
 [!code-csharp[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/CSharp/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.cs)]
 [!code-vb[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/VisualBasic/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.vb)]  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1407: не используйте статические члены в видимых COM типах](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)  
  
 [CA1017: помечайте сборки атрибутом ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## <a name="see-also"></a>См. также  
 [Взаимодействие с неуправляемым кодом](/dotnet/framework/interop/index)   
 [Oпределение типов .NET для взаимодействия](/dotnet/framework/interop/qualifying-net-types-for-interoperation)