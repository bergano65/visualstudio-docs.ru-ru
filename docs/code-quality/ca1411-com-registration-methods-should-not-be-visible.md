---
title: CA1411. Методы регистрации COM не должны быть видимыми
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1411
- ComRegistrationMethodsShouldNotBeVisible
helpviewer_keywords:
- ComRegistrationMethodsShouldNotBeVisible
- CA1411
ms.assetid: a59f96f1-1f38-4596-b656-947df5c55311
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: bd721edab080de7708ac395e2a7d7e486c504fba
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62546379"
---
# <a name="ca1411-com-registration-methods-should-not-be-visible"></a>CA1411. Методы регистрации COM не должны быть видимыми

|||
|-|-|
|TypeName|ComRegistrationMethodsShouldNotBeVisible|
|CheckId|CA1411|
|Категория|Microsoft.Interoperability|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина

Метод, отмеченный атрибутом <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> или <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> атрибута видим извне.

## <a name="rule-description"></a>Описание правила
 Когда сборка регистрируется с помощью модели объектов компонента (COM), записи добавляются в реестр для каждого видимым COM-типа в сборке. Методы, помеченные атрибутом <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> и <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> атрибуты называются во время регистрации и отмены регистрации, соответственно, для выполнения пользовательского кода, характерное для регистрации или ее отмены из этих типов. Этот код не должен вызываться за пределами этих процессов.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, изменить доступность метода `private` или `internal` (`Friend` в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 Следующий пример показывает два метода, которые нарушают данное правило.

 [!code-csharp[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/CSharp/ca1411-com-registration-methods-should-not-be-visible_1.cs)]
 [!code-vb[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/VisualBasic/ca1411-com-registration-methods-should-not-be-visible_1.vb)]

## <a name="related-rules"></a>Связанные правила
 [CA1410: Методы регистрации COM должны быть соответствующими](../code-quality/ca1410-com-registration-methods-should-be-matched.md)

## <a name="see-also"></a>См. также

- <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>
- [Регистрация сборок в COM](/dotnet/framework/interop/registering-assemblies-with-com)
- [Regasm.exe (средство регистрации сборок)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)