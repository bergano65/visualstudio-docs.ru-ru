---
title: 'CA1410: должны быть сопоставлены методы регистрации COM | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
helpviewer_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
ms.assetid: f3b2e62d-fd66-4093-9f0c-dba01ad995fd
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 43767ce04b32440a5c6753f5bfcabb91487c1232
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546709"
---
# <a name="ca1410-com-registration-methods-should-be-matched"></a>CA1410. Методы регистрации COM должны быть согласованными
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|Значение|
|-|-|
|TypeName|ComRegistrationMethodsShouldBeMatched|
|CheckId|CA1410|
|Категория|Microsoft. взаимодействие|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Тип объявляет метод, помеченный <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> атрибутом, но не объявляет метод, помеченный <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> атрибутом, или наоборот.

## <a name="rule-description"></a>Описание правила
 Чтобы клиенты модели COM создали [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] тип, сначала необходимо зарегистрировать тип. Если он доступен, метод, помеченный <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> атрибутом, вызывается во время процесса регистрации для запуска пользовательского кода. В процессе отмены регистрации вызывается соответствующий метод, помеченный <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> атрибутом, чтобы отменить операции метода регистрации.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, добавьте соответствующий метод регистрации или отмены регистрации.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показан тип, нарушающий правило. В коде с комментарием отображается исправление нарушения.

 [!code-csharp[FxCop.Interoperability.ComRegistration#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration/cs/FxCop.Interoperability.ComRegistration.cs#1)]
 [!code-vb[FxCop.Interoperability.ComRegistration#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration/vb/FxCop.Interoperability.ComRegistration.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1411. Методы регистрации COM не должны быть видимыми](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)

## <a name="see-also"></a>См. также
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>[Регистрация сборок с помощьюRegasm.exe com](https://msdn.microsoft.com/library/87925795-a3ae-4833-b138-125413478551) [(средство регистрации сборок)](https://msdn.microsoft.com/library/e190e342-36ef-4651-a0b4-0e8c2c0281cb)
