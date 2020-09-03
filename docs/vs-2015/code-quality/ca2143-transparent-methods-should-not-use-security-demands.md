---
title: 'CA2143: прозрачные методы не должны использовать требования безопасности | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2143
ms.assetid: 5d3923d7-cf40-4512-bc5c-0db0e0d6e25a
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ca8f049da83b99da7d36ebf74e756dd95f738d64
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546475"
---
# <a name="ca2143-transparent-methods-should-not-use-security-demands"></a>CA2143. Прозрачные методы не должны использовать требования безопасности
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|транспарентмесодсшаулднотдеманд|
|CheckId|CA2143|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Тип или метод транпарент декларативно помечается <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName> `.Demand` требованием, или метод вызывает <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName> метод.

## <a name="rule-description"></a>Описание правила
 Прозрачный для системы безопасности код не должен отвечать за проверку безопасности операции и поэтому не должен требовать разрешений. Прозрачный для системы безопасности код должен использовать полные требования для принятия решений по безопасности, и критичный в плане безопасности код не должен полагаться на прозрачный код, чтобы создать полное требование. Любой код, выполняющий проверки безопасности, такие как требования безопасности, должен быть критически важным для защиты.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Как правило, чтобы устранить нарушение этого правила, пометьте метод <xref:System.Security.SecuritySafeCriticalAttribute> атрибутом. Это требование также можно удалить.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 Файлы правил в следующем коде, поскольку прозрачный метод делает декларативное требование к безопасности.

 [!code-csharp[FxCop.Security.CA2143.TransparentMethodsShouldNotDemand#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2143.transparentmethodsshouldnotdemand/cs/ca2143 - transparentmethodsshouldnotdemand.cs#1)]

## <a name="see-also"></a>См. также:
 [CA2142. Прозрачный код не должен быть защищен проверками LinkDemands](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)
