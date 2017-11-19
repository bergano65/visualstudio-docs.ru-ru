---
title: "CA1412: Помечайте интерфейсы ComSource как IDispatch | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MarkComSourceInterfacesAsIDispatch
- CA1412
helpviewer_keywords:
- CA1412
- MarkComSourceInterfacesAsIDispatch
ms.assetid: 131a7563-0410-443c-a8f5-52104250cfb4
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b8a53053588670fef616f4df7633b3a25fb45712
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
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
 <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>используется для определения интерфейсов событий, предоставляемыми классом клиентам объектов модели компонентов (COM). Эти интерфейсы должны предоставляться как `InterfaceIsIDispatch` позволяет клиентам получать уведомления о событиях COM Visual Basic 6. По умолчанию, если интерфейс не помечен атрибутом <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> атрибута, оно будет представлено как сдвоенный интерфейс.  
  
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
 [Практическое руководство. Вызов событий, обрабатываемых приемником COM](http://msdn.microsoft.com/en-us/7c9944b2-e951-4c3e-a0a1-59b2ae37d7fd)   
 [Взаимодействие с неуправляемым кодом](/dotnet/framework/interop/index)