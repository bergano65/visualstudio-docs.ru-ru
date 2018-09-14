---
title: 'CA1410: методы регистрации для COM-клиента должны быть соответствующими'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 1d4cbff52a5b5b5ef5fc46ef0b2f93926f097485
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/13/2018
ms.locfileid: "45550902"
---
# <a name="ca1410-com-registration-methods-should-be-matched"></a>CA1410: методы регистрации для COM-клиента должны быть соответствующими

|||
|-|-|
|TypeName|ComRegistrationMethodsShouldBeMatched|
|CheckId|CA1410|
|Категория|Microsoft.Interoperability|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Тип объявляет метод, отмеченный атрибутом <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> атрибута, но не объявляет метод, отмеченный атрибутом <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> атрибут, или наоборот.

## <a name="rule-description"></a>Описание правила
 Для клиентов компонента объекта модели (COM) для создания [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] типа, этот тип должен быть зарегистрирован. Если он доступен, метод, отмеченный атрибутом <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> атрибут называется во время процесса регистрации для выполнения кода, определяемое пользователем. Соответствующий метод, отмеченный атрибутом <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> атрибут называется во время отмены регистрации для отката операций метод регистрации.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, добавьте соответствующий регистрации или метод отмены регистрации.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В примере показан тип, который нарушает правило. Закомментированный код показано исправления для нарушения.

 [!code-csharp[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/CSharp/ca1410-com-registration-methods-should-be-matched_1.cs)]
 [!code-vb[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/VisualBasic/ca1410-com-registration-methods-should-be-matched_1.vb)]

## <a name="related-rules"></a>Связанные правила
 [CA1411: методы регистрации для COM-клиента не должны быть видимыми](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)

## <a name="see-also"></a>См. также

- <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>
- [Регистрация сборок в COM](/dotnet/framework/interop/registering-assemblies-with-com)
- [Regasm.exe (средство регистрации сборок)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)