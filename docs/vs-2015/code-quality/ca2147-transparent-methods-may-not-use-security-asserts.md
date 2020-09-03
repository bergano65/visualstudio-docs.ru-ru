---
title: 'CA2147: прозрачные методы не могут использовать утверждения безопасности | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SecurityTransparentCodeShouldNotAssert
- CA2147
- CA2128
helpviewer_keywords:
- CA2128
- SecurityTransparentCodeShouldNotAssert
ms.assetid: 5d31e940-e599-4b23-9b28-1c336f8d910e
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 45639afc9946aa43df121a5a1881174371413c25
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546384"
---
# <a name="ca2147-transparent-methods-may-not-use-security-asserts"></a>CA2147. Прозрачные методы могут не использовать утверждения безопасности
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|SecurityTransparentCodeShouldNotAssert|
|CheckId|CA2147|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Коду, помеченному как, <xref:System.Security.SecurityTransparentAttribute> не предоставлены достаточные разрешения для утверждения.

## <a name="rule-description"></a>Описание правила
 Это правило анализирует все методы и типы в сборке, которая имеет значение 100% прозрачное или смешанное прозрачное или критическое, и помечает любое декларативное или императивное использование <xref:System.Security.CodeAccessPermission.Assert%2A> .

 Во время выполнения любые вызовы <xref:System.Security.CodeAccessPermission.Assert%2A> из прозрачного кода приведут к возникновению <xref:System.InvalidOperationException> исключения. Это может происходить как в 100% прозрачных сборках, так и в смешанных прозрачных и критических сборках, где метод или тип объявлен как прозрачный, но включает декларативное или императивное утверждение.

 В [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 2,0 появилась функция с именем *прозрачность*. Отдельные методы, поля, интерфейсы, классы и типы могут быть либо прозрачными, либо критически важными.

 Прозрачный код не может повышать привилегии безопасности. Таким образом, любые разрешения, предоставленные или запрошенные им, автоматически передаются через код вызывающему или ведущему домену приложения. Примеры повышения прав включают утверждения, LinkDemands, Суппрессунманажедкоде и `unsafe` код.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить эту проблему, либо пометьте код, который вызывает Assert, с помощью <xref:System.Security.SecurityCriticalAttribute> , либо удалите утверждение.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не отключайте сообщение от этого правила.

## <a name="example"></a>Пример
 Этот код завершится ошибкой `SecurityTestClass` , если является прозрачным, когда `Assert` метод создает исключение <xref:System.InvalidOperationException> .

 [!code-csharp[FxCop.Security.CA2147.TransparentMethodsMustNotUseSecurityAsserts#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2147.transparentmethodsmustnotusesecurityasserts/cs/ca2147 - transparentmethodsmustnotusesecurityasserts.cs#1)]

## <a name="example"></a>Пример
 Один из вариантов — код, приведенный в примере ниже, и, если метод считается безопасным для повышения прав, пометьте Секурититранспарентмесод с критическим с точки зрения безопасности, который должен быть выполнен в методе вместе с любыми вызовами, происходящими в методе под утверждением.

 [!code-csharp[FxCop.Security.SecurityTransparentCode2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SecurityTransparentCode2/cs/FxCop.Security.SecurityTransparentCode2.cs#1)]

 Кроме того, можно удалить утверждение из кода и позволить всем последующим запросам на разрешение ввода-вывода выполнять потоки, расположенные за пределами Секурититранспарентмесод, на вызывающий объект. Это обеспечивает проверку безопасности. В этом случае аудит безопасности не требуется, так как требования к разрешениям будут передаваться вызывающему и (или) домену приложения. Требования к разрешениям тесно контролируются с помощью политик безопасности, среды размещения и разрешений исходного кода.

## <a name="see-also"></a>См. также:
 [Предупреждения системы безопасности](../code-quality/security-warnings.md)
