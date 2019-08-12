---
title: CA1822. Пометьте члены как статические
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MarkMembersAsStatic
- CA1822
helpviewer_keywords:
- MarkMembersAsStatic
- CA1822
ms.assetid: 743f0af7-41d1-4852-8d97-af0688b31118
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8f25b74949c734921c313ae2cf00a2d217029e52
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921384"
---
# <a name="ca1822-mark-members-as-static"></a>CA1822. Пометьте члены как статические

|||
|-|-|
|TypeName|MarkMembersAsStatic|
|CheckId|CA1822|
|Категория|Microsoft. Performance|
|Критическое изменение|Не критическое — если элемент не виден за пределами сборки, независимо от внесенных изменений. Не критическое — если вы просто изменяете член на член экземпляра с `this` ключевым словом.<br /><br /> Критическое — при изменении члена члена экземпляра на статический член, который является видимым за пределами сборки.|

## <a name="cause"></a>Причина
Элемент, не обращающийся к данным экземпляра, не помечен как статический (общий в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).

## <a name="rule-description"></a>Описание правила
Члены, не обращающиеся к данным экземпляра и не вызывающие методы экземпляра, можно пометить как статические (Shared в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Если пометить методы как статические, компилятор предоставит этим членам невиртуальные места вызова. При выдаче невиртуальных сайтов вызова проверка во время выполнения будет запрещена для каждого вызова, который гарантирует, что текущий указатель объекта не имеет значение null. Это может достичь измеряемого выигрыша в производительности для кода, чувствительного к производительности. В некоторых случаях сбой доступа к текущему экземпляру объекта представляет проблему с корректностью.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Пометьте член как статический (или общий [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) или используйте "this"/"Me" в теле метода, если это уместно.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Можно отключить вывод предупреждения из этого правила для ранее отгруженного кода, для которого исправление будет критическим изменением.

## <a name="related-rules"></a>Связанные правила
[CA1811 Избегайте невызванного закрытого кода](../code-quality/ca1811-avoid-uncalled-private-code.md)

[CA1812 Избегайте использования внутренних классов без экземпляров](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

[CA1804 Удалить неиспользуемые локальные переменные](../code-quality/ca1804-remove-unused-locals.md)