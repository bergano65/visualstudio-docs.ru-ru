---
title: 'CA1403: типы автоматического макета не должны быть видимыми для COM | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AutoLayoutTypesShouldNotBeComVisible
- CA1403
helpviewer_keywords:
- CA1403
- AutoLayoutTypesShouldNotBeComVisible
ms.assetid: a7007714-f9b4-4730-94e0-67d3dc68991f
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1752efb5be1828f62703e1fe1a1130b37ff80503
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534931"
---
# <a name="ca1403-auto-layout-types-should-not-be-com-visible"></a>CA1403. Типы с автомакетом не должны быть видимыми для COM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|AutoLayoutTypesShouldNotBeComVisible|
|CheckId|CA1403|
|Категория|Microsoft. взаимодействие|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Видимый тип значения модели COM помечен <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName> атрибутом, для которого задано значение <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=fullName> .

## <a name="rule-description"></a>Описание правила
 <xref:System.Runtime.InteropServices.LayoutKind> типы макета управляются средой CLR. Макет этих типов может изменяться в разных версиях .NET Framework, что приведет к нарушению работы клиентов COM, которые предполагают конкретный макет. Обратите внимание, что если <xref:System.Runtime.InteropServices.StructLayoutAttribute> атрибут не задан, [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] компиляторы C#, и C++ указывают <xref:System.Runtime.InteropServices.LayoutKind> макет для типов значений.

 Если не указано иное, все открытые неуниверсальные типы видимы для COM. все неоткрытые и универсальные типы являются невидимыми для COM. Однако для сокращения числа ложных срабатываний это правило требует явного определения видимости типа COM. включающая сборка должна быть помечена <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> значением, `false` а тип должен быть помечен <xref:System.Runtime.InteropServices.ComVisibleAttribute> значением `true` .

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, измените значение <xref:System.Runtime.InteropServices.StructLayoutAttribute> атрибута на <xref:System.Runtime.InteropServices.LayoutKind> или <xref:System.Runtime.InteropServices.LayoutKind> , либо сделайте тип невидимым для com.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показан тип, нарушающий правило, и тип, соответствующий правилу.

 [!code-csharp[FxCop.Interoperability.AutoLayout#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoLayout/cs/FxCop.Interoperability.AutoLayout.cs#1)]
 [!code-vb[FxCop.Interoperability.AutoLayout#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoLayout/vb/FxCop.Interoperability.AutoLayout.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1408. Не используйте тип AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>См. также:
 [Введение в интерфейс класса,](https://msdn.microsoft.com/733c0dd2-12e5-46e6-8de1-39d5b25df024) [соответствующий типам .NET для](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd) взаимодействия [с неуправляемым кодом](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
