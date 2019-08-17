---
title: CA1041. Укажите сообщение ObsoleteAttribute
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1041
- ProvideObsoleteAttributeMessage
helpviewer_keywords:
- ProvideObsoleteAttributeMessage
- CA1041
ms.assetid: be5bee69-d2d2-44e1-be2e-3ea451969003
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: a0545503b80e2f256593012e06cdf7ccd8b3b5b1
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547642"
---
# <a name="ca1041-provide-obsoleteattribute-message"></a>CA1041. Укажите сообщение ObsoleteAttribute

|||
|-|-|
|TypeName|ProvideObsoleteAttributeMessage|
|CheckId|CA1041|
|Категория|Microsoft. Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Тип или член помечается с помощью <xref:System.ObsoleteAttribute?displayProperty=fullName> атрибута, для которого не <xref:System.ObsoleteAttribute.Message%2A?displayProperty=fullName> указано свойство.

По умолчанию это правило рассматривает только видимые извне типы и члены, но это можно [настроить](#configurability).

## <a name="rule-description"></a>Описание правила

<xref:System.ObsoleteAttribute>используется для обозначения устаревших типов и членов библиотеки. Потребители библиотек должны избегать использования любого типа или члена, помеченного как устаревший. Это связано с тем, что он может не поддерживаться и в конечном итоге будет удален из более поздних версий библиотеки. При компиляции типа или члена <xref:System.ObsoleteAttribute> <xref:System.ObsoleteAttribute.Message%2A> , помеченного с помощью, отображается свойство атрибута. Это предоставляет пользователю сведения об устаревшем типе или члене. Эти сведения обычно включают в себя, как долго устаревший тип или член будет поддерживаться конструкторами библиотек и предпочтительной заменой для использования.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, добавьте `message` параметр <xref:System.ObsoleteAttribute> в конструктор.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Не отключайте предупреждение из этого правила, так <xref:System.ObsoleteAttribute.Message%2A> как свойство предоставляет важные сведения об устаревшем типе или члене.

## <a name="configurability"></a>Возможности настройки

Если вы используете это правило из [анализаторов FxCop](install-fxcop-analyzers.md) (а не для анализа прежних версий), можно настроить, на какие части базы кода следует запускать это правило, в зависимости от их доступности. Например, чтобы указать, что правило должно выполняться только для поверхности API, не являющейся общедоступной, добавьте следующую пару "ключ-значение" в файл. editorconfig в проекте:

```ini
dotnet_code_quality.ca1041.api_surface = private, internal
```

Этот параметр можно настроить только для этого правила, для всех правил или для всех правил в этой категории (конструктор). Дополнительные сведения см. в статье [Настройка средств FxCop Analyzer](configure-fxcop-analyzers.md).

## <a name="example"></a>Пример

В следующем примере показан устаревший член, который правильно объявлен <xref:System.ObsoleteAttribute>.

[!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CPP/ca1041-provide-obsoleteattribute-message_1.cpp)]
[!code-csharp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CSharp/ca1041-provide-obsoleteattribute-message_1.cs)]
[!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/VisualBasic/ca1041-provide-obsoleteattribute-message_1.vb)]

## <a name="see-also"></a>См. также

- <xref:System.ObsoleteAttribute?displayProperty=fullName>