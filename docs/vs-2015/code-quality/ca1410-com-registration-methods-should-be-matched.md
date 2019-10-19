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
ms.openlocfilehash: 30f507f07de858dc222b4824ac6da633c76812ab
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652746"
---
# <a name="ca1410-com-registration-methods-should-be-matched"></a>CA1410: методы регистрации для COM-клиента должны быть соответствующими
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ComRegistrationMethodsShouldBeMatched|
|CheckId|CA1410|
|Категория|Microsoft. взаимодействие|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Тип объявляет метод, помеченный атрибутом <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName>, но не объявляет метод, помеченный атрибутом <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>, или наоборот.

## <a name="rule-description"></a>Описание правила
 Чтобы клиенты модели COM создали тип [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], сначала необходимо зарегистрировать тип. Если он доступен, метод, помеченный атрибутом <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>, вызывается в процессе регистрации для запуска пользовательского кода. В процессе отмены регистрации вызывается соответствующий метод, помеченный атрибутом <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>, чтобы отменить операции метода регистрации.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, добавьте соответствующий метод регистрации или отмены регистрации.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показан тип, нарушающий правило. В коде с комментарием отображается исправление нарушения.

 [!code-csharp[FxCop.Interoperability.ComRegistration#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration/cs/FxCop.Interoperability.ComRegistration.cs#1)]
 [!code-vb[FxCop.Interoperability.ComRegistration#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration/vb/FxCop.Interoperability.ComRegistration.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1411: методы регистрации для COM-клиента не должны быть видимыми](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)

## <a name="see-also"></a>См. также раздел
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName> [регистрации сборок с помощью COM](https://msdn.microsoft.com/library/87925795-a3ae-4833-b138-125413478551) [Regasm. exe (средство регистрации сборок)](https://msdn.microsoft.com/library/e190e342-36ef-4651-a0b4-0e8c2c0281cb)
