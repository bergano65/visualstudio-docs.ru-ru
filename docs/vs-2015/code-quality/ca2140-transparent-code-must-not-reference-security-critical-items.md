---
title: 'CA2140: прозрачный код не должен ссылаться на критически важные элементы безопасности | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2129
- SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode
- CA2140
helpviewer_keywords:
- CA2140
- SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode
- CA2129
ms.assetid: 251a12da-0557-47f5-a4f7-0229d590ae7b
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5c3e624e4210e59406fd1d5955cd37c2e83ed79a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72602866"
---
# <a name="ca2140-transparent-code-must-not-reference-security-critical-items"></a>CA2140: прозрачный код не должен ссылаться на элементы, критичные в плане безопасности
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|транспарентмесодсмустнотреференцекритикалкоде|
|CheckId|CA2140|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Прозрачный метод:

- обрабатывает критически важный для безопасности тип исключения безопасности

- имеет параметр, помеченный как тип, критический для безопасности

- имеет универсальный параметр с ограниченными критическими ограничениями безопасности

- имеет локальную переменную с критическим типом безопасности

- ссылается на тип, помеченный как критически важный для безопасности

- вызывает метод, помеченный как критически важный для безопасности

- ссылается на поле, помеченное как критическое для безопасности

- Возвращает тип, помеченный как критический с точки зрения безопасности

## <a name="rule-description"></a>Описание правила
 Элемент кода, помеченный атрибутом <xref:System.Security.SecurityCriticalAttribute>, является критически важным для безопасности. Прозрачный метод не может использовать элемент, критический с точки зрения безопасности. Если прозрачный тип пытается использовать критически важный для безопасности тип, возникает <xref:System.TypeAccessException>, <xref:System.MethodAccessException> или <xref:System.FieldAccessException>.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, выполните одно из следующих действий.

- Пометьте элемент кода, использующий критически важный для безопасности код с помощью атрибута <xref:System.Security.SecurityCriticalAttribute>

     \- или -

- Удалите атрибут <xref:System.Security.SecurityCriticalAttribute> из элементов кода, помеченных как критически важный для безопасности, а затем пометьте их атрибутом <xref:System.Security.SecuritySafeCriticalAttribute> или <xref:System.Security.SecurityTransparentAttribute>.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующих примерах прозрачный метод пытается сослаться на общую коллекцию с критической безопасностью, поле критическое для безопасности и метод критической безопасности.

 [!code-csharp[FxCop.Security.CA2140.TransparentMethodsMustNotReferenceCriticalCode#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2140.transparentmethodsmustnotreferencecriticalcode/cs/ca2140 - transparentmethodsmustnotreferencecriticalcode.cs#1)]

## <a name="see-also"></a>См. также раздел
 <xref:System.Security.SecurityTransparentAttribute> <xref:System.Security.SecurityCriticalAttribute>
 <xref:System.Security.SecurityTransparentAttribute>
 <xref:System.Security.SecurityTreatAsSafeAttribute>
 <xref:System.Security?displayProperty=fullName>
