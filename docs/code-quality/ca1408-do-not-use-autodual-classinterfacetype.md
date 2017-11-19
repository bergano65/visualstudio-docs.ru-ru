---
title: "CA1408: Не используйте AutoDual ClassInterfaceType | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotUseAutoDualClassInterfaceType
- CA1408
helpviewer_keywords:
- CA1408
- DoNotUseAutoDualClassInterfaceType
ms.assetid: 60ca5e02-3c51-42dd-942b-4f950eecfa0f
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ffdbbfb8f28a6150888f3f127aa66ae82d31b4b8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca1408-do-not-use-autodual-classinterfacetype"></a>CA1408: не используйте AutoDual ClassInterfaceType
|||  
|-|-|  
|TypeName|DoNotUseAutoDualClassInterfaceType|  
|CheckId|CA1408|  
|Категория|Microsoft.Interoperability|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Видимый тип объектов модели компонентов (COM) помечается <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> атрибута `AutoDual` значение <xref:System.Runtime.InteropServices.ClassInterfaceType>.  
  
## <a name="rule-description"></a>Описание правила  
 Типы, использующие сдвоенный интерфейс, позволяют клиентам выполнять привязку к определенному макету интерфейса. Все изменения в будущей версии макета типа и в базовых типах приведут к нарушению работы COM-клиентов, связанных с интерфейсом. По умолчанию если <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> атрибут не указан, используется только диспетчерский интерфейс.  
  
 Если не указано иное, все открытые неуниверсальные типы являются видимыми для COM; все закрытые и универсальные типы являются невидимыми для COM.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, измените значение <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> атрибут `None` значение <xref:System.Runtime.InteropServices.ClassInterfaceType> и явно определен интерфейс.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Не отключайте предупреждение из этого правила, если вы не уверены, что в будущей версии макета типа и его базовых типов не изменяет.  
  
## <a name="example"></a>Пример  
 Приведенный ниже показан класс, который нарушает правило и повторное объявление класса, чтобы использовать явный интерфейс.  
  
 [!code-csharp[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/CSharp/ca1408-do-not-use-autodual-classinterfacetype_1.cs)]
 [!code-vb[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/VisualBasic/ca1408-do-not-use-autodual-classinterfacetype_1.vb)]  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1403: типы с автомакетом не должны быть видимыми для COM](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)  
  
 [CA1412: помечайте интерфейсы ComSource как IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)  
  
## <a name="see-also"></a>См. также  
 [Введение в интерфейс класса](http://msdn.microsoft.com/en-us/733c0dd2-12e5-46e6-8de1-39d5b25df024)   
 [Уточнение типов .NET для взаимодействия](/dotnet/framework/interop/qualifying-net-types-for-interoperation)   
 [Взаимодействие с неуправляемым кодом](/dotnet/framework/interop/index)