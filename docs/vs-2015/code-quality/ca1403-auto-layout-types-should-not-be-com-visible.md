---
title: CA1403. Типы с автомакетом не должны быть видимыми для COM | Документация Майкрософт
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2420582ab342948d7774e1bb9e4b5947f44f8d2b
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65695443"
---
# <a name="ca1403-auto-layout-types-should-not-be-com-visible"></a>CA1403. Типы с автомакетом не должны быть видимыми для COM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AutoLayoutTypesShouldNotBeComVisible|
|CheckId|CA1403|
|Категория|Microsoft.Interoperability|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Тип значений, видимых объектов модели компонентов (COM) помечен с помощью <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName> атрибут <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=fullName>.

## <a name="rule-description"></a>Описание правила
 <xref:System.Runtime.InteropServices.LayoutKind> Типы макета управляет среда CLR. Макеты этих типов можно изменить в разных версиях .NET Framework, которая приведет к разрыву COM-клиентам, которые ожидают определенного макета. Обратите внимание, что если <xref:System.Runtime.InteropServices.StructLayoutAttribute> атрибут не указан, в C#, [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], и укажите компиляторы C++ <xref:System.Runtime.InteropServices.LayoutKind> макета для типов значений.

 Если не указано иное, все открытые неуниверсальные типы являются видимыми для COM; все закрытые и универсальные типы невидимы для модели COM. Тем не менее чтобы сократить число ложных срабатываний, это правило требует видимость COM типа, чтобы задавать явно; включающая сборка должны быть отмечены <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> присвоено `false` и тип должен быть помечен атрибутом <xref:System.Runtime.InteropServices.ComVisibleAttribute> присвоено `true`.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, измените значение <xref:System.Runtime.InteropServices.StructLayoutAttribute> атрибут <xref:System.Runtime.InteropServices.LayoutKind> или <xref:System.Runtime.InteropServices.LayoutKind>, или сделайте тип невидимым для COM.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В примере показан тип, который нарушает правило и тип, соответствующий этому правилу.

 [!code-csharp[FxCop.Interoperability.AutoLayout#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoLayout/cs/FxCop.Interoperability.AutoLayout.cs#1)]
 [!code-vb[FxCop.Interoperability.AutoLayout#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoLayout/vb/FxCop.Interoperability.AutoLayout.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1408: Не используйте AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>См. также
 [Введение в интерфейс класса](https://msdn.microsoft.com/733c0dd2-12e5-46e6-8de1-39d5b25df024) [уточнение типов .NET для взаимодействия](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd) [взаимодействие с неуправляемым кодом](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
