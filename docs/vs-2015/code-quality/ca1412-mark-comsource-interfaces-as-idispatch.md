---
title: 'CA1412: помечайте интерфейсы пометьте comsource как IDispatch | Документация Майкрософт'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 86dc7042a48faa200ef9c360829b1756bc261ab0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652733"
---
# <a name="ca1412-mark-comsource-interfaces-as-idispatch"></a>CA1412: помечайте интерфейсы ComSource как IDispatch
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkComSourceInterfacesAsIDispatch|
|CheckId|CA1412|
|Категория|Microsoft. взаимодействие|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Тип помечен атрибутом <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>, и по крайней мере один указанный интерфейс не помечен атрибутом <xref:System.Runtime.InteropServices.InterfaceTypeAttribute>, для которого задано значение `InterfaceIsDispatch`.

## <a name="rule-description"></a>Описание правила
 <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> используется для обнаружения интерфейсов событий, предоставляемых классом клиентам модели COM. Эти интерфейсы должны быть предоставлены как `InterfaceIsIDispatch`, чтобы позволить Visual Basic 6 COM-клиентам получать уведомления о событиях. По умолчанию, если интерфейс не помечен атрибутом <xref:System.Runtime.InteropServices.InterfaceTypeAttribute>, он предоставляется как сдвоенный интерфейс.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, добавьте или измените атрибут <xref:System.Runtime.InteropServices.InterfaceTypeAttribute>, чтобы его значение было равно InterfaceIsIDispatch для всех интерфейсов, указанных с помощью атрибута <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показан класс, в котором один из интерфейсов нарушает правило.

 [!code-csharp[FxCop.Interoperability.MarkIDispatch#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.MarkIDispatch/cs/FxCop.Interoperability.MarkIDispatch.cs#1)]
 [!code-vb[FxCop.Interoperability.MarkIDispatch#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.MarkIDispatch/vb/FxCop.Interoperability.MarkIDispatch.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1408: не используйте AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>См. также раздел
 [Как создавать события, обрабатываемые приемником COM](https://msdn.microsoft.com/7c9944b2-e951-4c3e-a0a1-59b2ae37d7fd) [при взаимодействии с неуправляемым кодом](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
