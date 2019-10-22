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
ms.openlocfilehash: bcfce9a80d02e525212d3f59173df4a7e8fbe968
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662706"
---
# <a name="ca2143-transparent-methods-should-not-use-security-demands"></a>CA2143: прозрачные методы не должны использовать требования безопасности
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|транспарентмесодсшаулднотдеманд|
|CheckId|CA2143|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Тип транпарент или метод декларативно помечается <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName> `.Demand` спроса или метод вызывает метод <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Описание правила
 Прозрачный для системы безопасности код не должен отвечать за проверку безопасности операции и поэтому не должен требовать разрешений. Прозрачный для системы безопасности код должен использовать полные требования для принятия решений по безопасности, и критичный в плане безопасности код не должен полагаться на прозрачный код, чтобы создать полное требование. Любой код, выполняющий проверки безопасности, такие как требования безопасности, должен быть критически важным для защиты.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Как правило, чтобы устранить нарушение этого правила, пометьте метод атрибутом <xref:System.Security.SecuritySafeCriticalAttribute>. Это требование также можно удалить.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 Файлы правил в следующем коде, поскольку прозрачный метод делает декларативное требование к безопасности.

 [!code-csharp[FxCop.Security.CA2143.TransparentMethodsShouldNotDemand#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2143.transparentmethodsshouldnotdemand/cs/ca2143 - transparentmethodsshouldnotdemand.cs#1)]

## <a name="see-also"></a>См. также раздел
 [CA2142: прозрачный код не должен быть защищен с помощью требований LinkDemand](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)
