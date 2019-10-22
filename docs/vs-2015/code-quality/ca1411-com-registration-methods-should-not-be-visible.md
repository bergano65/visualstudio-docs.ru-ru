---
title: 'CA1411: методы регистрации COM не должны быть видимыми | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1411
- ComRegistrationMethodsShouldNotBeVisible
helpviewer_keywords:
- ComRegistrationMethodsShouldNotBeVisible
- CA1411
ms.assetid: a59f96f1-1f38-4596-b656-947df5c55311
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f3ddd2c90d23884bd08a90560dcc5ed0fe700aaf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652714"
---
# <a name="ca1411-com-registration-methods-should-not-be-visible"></a>CA1411: методы регистрации для COM-клиента не должны быть видимыми
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ComRegistrationMethodsShouldNotBeVisible|
|CheckId|CA1411|
|Категория|Microsoft. взаимодействие|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Метод, помеченный <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> или атрибутом <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>, является внешним видимым.

## <a name="rule-description"></a>Описание правила
 Когда сборка регистрируется с помощью модели COM, записи добавляются в реестр для каждого типа, видимого для COM, в сборке. Методы, помеченные атрибутами <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> и <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>, вызываются в процессе регистрации и отмены регистрации соответственно для выполнения пользовательского кода, относящегося к регистрации или отмене регистрации этих типов. Этот код не должен вызываться за пределами этих процессов.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, измените уровень доступа метода на `private` или `internal` (`Friend` в [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]).

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показаны два метода, которые нарушают правило.

 [!code-csharp[FxCop.Interoperability.ComRegistration2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration2/cs/FxCop.Interoperability.ComRegistration2.cs#1)]
 [!code-vb[FxCop.Interoperability.ComRegistration2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration2/vb/FxCop.Interoperability.ComRegistration2.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1410: методы регистрации для COM-клиента должны быть соответствующими](../code-quality/ca1410-com-registration-methods-should-be-matched.md)

## <a name="see-also"></a>См. также раздел
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName> [регистрации сборок с помощью COM](https://msdn.microsoft.com/library/87925795-a3ae-4833-b138-125413478551) [Regasm. exe (средство регистрации сборок)](https://msdn.microsoft.com/library/e190e342-36ef-4651-a0b4-0e8c2c0281cb)
