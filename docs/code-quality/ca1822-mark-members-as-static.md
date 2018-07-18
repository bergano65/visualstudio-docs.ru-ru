---
title: 'CA1822: помечайте члены как статические'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 498a3638a02891683aff1b343431418d1a82bab0
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31914989"
---
# <a name="ca1822-mark-members-as-static"></a>CA1822: помечайте члены как статические
|||
|-|-|
|TypeName|MarkMembersAsStatic|
|CheckId|CA1822|
|Категория|Microsoft.Performance|
|Критическое изменение|Non критическое, если элемент не отображается за пределами сборки, независимо от того, изменения вносятся. Не критическое, если вы просто меняете члена к члену экземпляра с `this` ключевое слово.<br /><br /> Критическое, если изменить элемент с членом экземпляра на статический элемент, и она отображается за пределами сборки.|

## <a name="cause"></a>Причина
 Элемент, который не осуществляет доступ к данным экземпляра не помечен как статический (Shared в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).

## <a name="rule-description"></a>Описание правила
 Члены, не обращающиеся к данным экземпляра и не вызывающие методы экземпляра, можно пометить как статические (Shared в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Если пометить методы как статические, компилятор предоставит этим членам невиртуальные места вызова. Выдача невиртуальные места вызова сделает невозможным проверку во время выполнения для каждого вызова, который гарантирует, что текущий указатель на объект не является нулевым. Этого можно добиться повышение производительности по сравнению с быстродействие. В некоторых случаях отказ в доступе к текущему экземпляру объекта является нарушением правильности.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Пометьте член как static (или Shared в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) или используйте «this» / «Me» в методе текста, при необходимости.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Можно безопасно подавить предупреждение из этого правила для поставленного ранее кода, для которого будет критическим изменением.

## <a name="related-rules"></a>Связанные правила
 [CA1811: не используйте невызываемый закрытый код](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812: не создавайте внутренние классы без экземпляров](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1804: удалите неиспользуемые локальные переменные](../code-quality/ca1804-remove-unused-locals.md)