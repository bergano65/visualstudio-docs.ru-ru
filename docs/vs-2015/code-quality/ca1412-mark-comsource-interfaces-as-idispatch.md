---
title: CA1412. Помечайте интерфейсы ComSource как IDispatch | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkComSourceInterfacesAsIDispatch
- CA1412
helpviewer_keywords:
- CA1412
- MarkComSourceInterfacesAsIDispatch
ms.assetid: 131a7563-0410-443c-a8f5-52104250cfb4
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d72dd7e143720ce4ef2fce364a7e5ed3529ff9f3
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65691993"
---
# <a name="ca1412-mark-comsource-interfaces-as-idispatch"></a>CA1412. Пометьте интерфейсы ComSource как IDispatch
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkComSourceInterfacesAsIDispatch|
|CheckId|CA1412|
|Категория|Microsoft.Interoperability|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Тип помечен атрибутом <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> атрибут и по крайней мере один указанного интерфейса не помечен атрибутом <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> атрибут `InterfaceIsDispatch` значение.

## <a name="rule-description"></a>Описание правила
 <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> используется для определения интерфейсов событий, класс предоставляет клиентам компонента объекта модели (COM). Эти интерфейсы должны предоставляться как `InterfaceIsIDispatch` позволяет клиентам COM Visual Basic 6 получать уведомления о событиях. По умолчанию, если интерфейс не помечен атрибутом <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> атрибут, оно будет представлено как сдвоенный интерфейс.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, добавление или изменение <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> таким образом, чтобы его значение установлено для InterfaceIsIDispatch для всех интерфейсов, которые указываются с помощью <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> атрибута.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показан класс, где один из интерфейсов нарушает правило.

 [!code-csharp[FxCop.Interoperability.MarkIDispatch#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.MarkIDispatch/cs/FxCop.Interoperability.MarkIDispatch.cs#1)]
 [!code-vb[FxCop.Interoperability.MarkIDispatch#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.MarkIDispatch/vb/FxCop.Interoperability.MarkIDispatch.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1408: Не используйте AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>См. также
 [Практическое руководство. Вызов событий, обрабатываемых приемником COM](https://msdn.microsoft.com/7c9944b2-e951-4c3e-a0a1-59b2ae37d7fd) [взаимодействие с неуправляемым кодом](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
