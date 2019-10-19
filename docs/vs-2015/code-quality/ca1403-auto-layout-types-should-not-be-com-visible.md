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
ms.openlocfilehash: 5f39540cb23d86dda4244604da8a9ff764594e11
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661335"
---
# <a name="ca1403-auto-layout-types-should-not-be-com-visible"></a>CA1403: типы макета Auto не должны быть видимыми для COM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AutoLayoutTypesShouldNotBeComVisible|
|CheckId|CA1403|
|Категория|Microsoft. взаимодействие|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Видимый тип значения модели COM помечен атрибутом <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName>, для которого задано значение <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=fullName>.

## <a name="rule-description"></a>Описание правила
 типы макета <xref:System.Runtime.InteropServices.LayoutKind> управляются средой CLR. Макет этих типов может изменяться в разных версиях .NET Framework, что приведет к нарушению работы клиентов COM, которые предполагают конкретный макет. Обратите внимание, что если атрибут <xref:System.Runtime.InteropServices.StructLayoutAttribute> не задан, C#то [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] и C++ компиляторы указывают <xref:System.Runtime.InteropServices.LayoutKind>ный макет для типов значений.

 Если не указано иное, все открытые неуниверсальные типы видимы для COM. все неоткрытые и универсальные типы являются невидимыми для COM. Однако для сокращения числа ложных срабатываний это правило требует явного определения видимости типа COM. включающая сборка должна быть помечена <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName>, для которой задано значение `false`, а тип должен быть помечен <xref:System.Runtime.InteropServices.ComVisibleAttribute>ным значением `true`.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, измените значение атрибута <xref:System.Runtime.InteropServices.StructLayoutAttribute> на <xref:System.Runtime.InteropServices.LayoutKind> или <xref:System.Runtime.InteropServices.LayoutKind> или сделайте тип невидимым для COM.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показан тип, нарушающий правило, и тип, соответствующий правилу.

 [!code-csharp[FxCop.Interoperability.AutoLayout#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoLayout/cs/FxCop.Interoperability.AutoLayout.cs#1)]
 [!code-vb[FxCop.Interoperability.AutoLayout#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoLayout/vb/FxCop.Interoperability.AutoLayout.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1408: не используйте AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>См. также раздел
 [Введение в интерфейс класса,](https://msdn.microsoft.com/733c0dd2-12e5-46e6-8de1-39d5b25df024) [соответствующий типам .NET для](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd) взаимодействия [с неуправляемым кодом](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
