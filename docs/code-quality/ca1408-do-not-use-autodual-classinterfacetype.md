---
title: 'CA1408: Не используйте AutoDual ClassInterfaceType | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- DoNotUseAutoDualClassInterfaceType
- CA1408
helpviewer_keywords:
- CA1408
- DoNotUseAutoDualClassInterfaceType
ms.assetid: 60ca5e02-3c51-42dd-942b-4f950eecfa0f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9ee8c016896381814aa5406b4023e24799f29219
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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
 [Уточнение типов .NET для взаимодействия](/dotnet/framework/interop/qualifying-net-types-for-interoperation)   
 [Взаимодействие с неуправляемым кодом](/dotnet/framework/interop/index)