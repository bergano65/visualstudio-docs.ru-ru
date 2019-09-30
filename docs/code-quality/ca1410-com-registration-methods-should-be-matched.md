---
title: CA1410. Методы регистрации COM должны быть согласованными
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
helpviewer_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
ms.assetid: f3b2e62d-fd66-4093-9f0c-dba01ad995fd
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: bca9e06c861ab2bcaceead8bf8ee195b64e45c83
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234737"
---
# <a name="ca1410-com-registration-methods-should-be-matched"></a>CA1410. Методы регистрации COM должны быть согласованными

|||
|-|-|
|TypeName|ComRegistrationMethodsShouldBeMatched|
|CheckId|CA1410|
|Категория|Microsoft. взаимодействие|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина:

Тип объявляет метод, помеченный <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> атрибутом, но не объявляет метод, помеченный <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> атрибутом, или наоборот.

## <a name="rule-description"></a>Описание правила

Чтобы клиенты модели COM создали тип .NET, сначала необходимо зарегистрировать тип. Если он доступен, метод, помеченный <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> атрибутом, вызывается во время процесса регистрации для запуска пользовательского кода. В процессе отмены регистрации вызывается соответствующий метод <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> , помеченный атрибутом, чтобы отменить операции метода регистрации.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, добавьте соответствующий метод регистрации или отмены регистрации.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример

В следующем примере показан тип, нарушающий правило. В коде с комментарием отображается исправление нарушения.

[!code-csharp[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/CSharp/ca1410-com-registration-methods-should-be-matched_1.cs)]
[!code-vb[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/VisualBasic/ca1410-com-registration-methods-should-be-matched_1.vb)]

## <a name="related-rules"></a>Связанные правила

[CA1411 Методы регистрации COM не должны быть видимыми](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)

## <a name="see-also"></a>См. также

- <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>
- [Регистрация сборок в COM](/dotnet/framework/interop/registering-assemblies-with-com)
- [Regasm.exe (средство регистрации сборок)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)