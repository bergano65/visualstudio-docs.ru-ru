---
title: CA1822. Пометьте члены как статические
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 77b256ddaff769263bcc56891ca7c0ad2be30d0c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54979703"
---
# <a name="ca1822-mark-members-as-static"></a>CA1822. Пометьте члены как статические

|||
|-|-|
|TypeName|MarkMembersAsStatic|
|CheckId|CA1822|
|Категория|Microsoft.Performance|
|Критическое изменение|Non критическое, если член не видимый за пределами сборки, независимо от того, изменения вносятся. Не критическое, если к члену экземпляра с помощью всего лишь изменить элемент `this` ключевое слово.<br /><br /> Критическое, если элемент изменяется экземпляра в статический член, и отображается за пределами сборки.|

## <a name="cause"></a>Причина
 Элемент, который не осуществляет доступ к данным экземпляра не помечен как статический (Shared в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).

## <a name="rule-description"></a>Описание правила
 Члены, не обращающиеся к данным экземпляра и не вызывающие методы экземпляра, можно пометить как статические (Shared в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Если пометить методы как статические, компилятор предоставит этим членам невиртуальные места вызова. Выпуск невиртуальные места вызова не позволит проверку во время выполнения для каждого вызова, который гарантирует, что текущий указатель на объект не равно null. Это можно достичь измеримое производительности по сравнению с учетом производительности кода. В некоторых случаях отказ в доступе к текущему экземпляру объекта представляет проблему правильность.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Пометьте член как static (или совместно в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) или используйте «this» / «Me» в методе body, при необходимости.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение из этого правила для ранее созданного кода, для которого будет критическим изменением.

## <a name="related-rules"></a>Связанные правила
 [CA1811: Не используйте Невызываемый закрытый код](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812: Избегайте неиспользуемых внутренних классов](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1804: Удалите неиспользуемые локальные переменные](../code-quality/ca1804-remove-unused-locals.md)