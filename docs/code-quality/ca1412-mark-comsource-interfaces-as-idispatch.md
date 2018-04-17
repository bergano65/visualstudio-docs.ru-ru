---
title: 'CA1412: Помечайте интерфейсы ComSource как IDispatch | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- MarkComSourceInterfacesAsIDispatch
- CA1412
helpviewer_keywords:
- CA1412
- MarkComSourceInterfacesAsIDispatch
ms.assetid: 131a7563-0410-443c-a8f5-52104250cfb4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cca84ed1470d43df2163de265e15a7efcbce0b62
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ca1412-mark-comsource-interfaces-as-idispatch"></a>CA1412: помечайте интерфейсы ComSource как IDispatch
|||  
|-|-|  
|TypeName|MarkComSourceInterfacesAsIDispatch|  
|CheckId|CA1412|  
|Категория|Microsoft.Interoperability|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Тип помечен атрибутом <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> атрибут и по крайней мере один указанного интерфейса не помечен атрибутом <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> атрибуту присвоено `InterfaceIsDispatch` значение.  
  
## <a name="rule-description"></a>Описание правила  
 <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> используется для определения интерфейсов событий, предоставляемыми классом клиентам объектов модели компонентов (COM). Эти интерфейсы должны предоставляться как `InterfaceIsIDispatch` позволяет клиентам получать уведомления о событиях COM Visual Basic 6. По умолчанию, если интерфейс не помечен атрибутом <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> атрибута, оно будет представлено как сдвоенный интерфейс.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, добавление или изменение <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> таким образом, чтобы его значение равно InterfaceIsIDispatch для всех интерфейсов, которые указаны с <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> атрибута.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## <a name="example"></a>Пример  
 В следующем примере показан класс, где один из интерфейсов нарушает правило.  
  
 [!code-csharp[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/CSharp/ca1412-mark-comsource-interfaces-as-idispatch_1.cs)]
 [!code-vb[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/VisualBasic/ca1412-mark-comsource-interfaces-as-idispatch_1.vb)]  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1408: не используйте AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)  
  
## <a name="see-also"></a>См. также  
 [Взаимодействие с неуправляемым кодом](/dotnet/framework/interop/index)