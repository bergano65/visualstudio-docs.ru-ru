---
title: CA1823. Избегайте неиспользуемых частных полей
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- AvoidUnusedPrivateFields
- CA1823
helpviewer_keywords:
- AvoidUnusedPrivateFields
- CA1823
ms.assetid: 614f94f6-0dc7-430f-8124-cb889a4a720f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f5610e97b623c21a7a0f380e9f2e070400e0aefc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53873240"
---
# <a name="ca1823-avoid-unused-private-fields"></a>CA1823. Избегайте неиспользуемых частных полей

|||
|-|-|
|TypeName|AvoidUnusedPrivateFields|
|CheckId|CA1823|
|Категория|Microsoft.Performance|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Это правило передается в том случае, если существует закрытое поле в коде, но не используется в любом пути кода.

## <a name="rule-description"></a>Описание правила
 Обнаружены закрытые поля, доступ к которым, судя по всему, не предоставляется в сборке.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, удалите поле или добавьте код, который его использует.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение из этого правила.

## <a name="related-rules"></a>Связанные правила
 [CA1812: Избегайте неиспользуемых внутренних классов](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801: Проверьте неиспользуемые параметры](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804: Удалите неиспользуемые локальные переменные](../code-quality/ca1804-remove-unused-locals.md)

 [CA1811: Не используйте Невызываемый закрытый код](../code-quality/ca1811-avoid-uncalled-private-code.md)