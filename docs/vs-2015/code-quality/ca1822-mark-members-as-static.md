---
title: 'CA1822: помечайте члены как статические | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkMembersAsStatic
- CA1822
helpviewer_keywords:
- MarkMembersAsStatic
- CA1822
ms.assetid: 743f0af7-41d1-4852-8d97-af0688b31118
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a571be6b713cd59ca290906e9398b78c8c021ba8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661170"
---
# <a name="ca1822-mark-members-as-static"></a>CA1822: помечайте члены как статические
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю документацию по Visual Studio см. в разделе [CA1822: Пометьте члены как статические](https://docs.microsoft.com/visualstudio/code-quality/ca1822-mark-members-as-static).

|||
|-|-|
|TypeName|MarkMembersAsStatic|
|CheckId|CA1822|
|Категория|Microsoft. Performance|
|Критическое изменение|Не критическое — если элемент не виден за пределами сборки, независимо от внесенных изменений.<br /><br /> Не критическое — если вы просто изменяете член на член экземпляра с ключевым словом `this`.<br /><br /> Критическое — при изменении члена члена экземпляра на статический член, который является видимым за пределами сборки.|

## <a name="cause"></a>Причина
 Элемент, не обращающийся к данным экземпляра, не помечен как статический (общий в [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]).

## <a name="rule-description"></a>Описание правила
 Члены, не обращающиеся к данным экземпляра и не вызывающие методы экземпляра, можно пометить как статические (Shared в [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]). Если пометить методы как статические, компилятор предоставит этим членам невиртуальные места вызова. При выдаче невиртуальных сайтов вызова проверка во время выполнения будет запрещена для каждого вызова, который гарантирует, что текущий указатель объекта не имеет значение null. Это может достичь измеряемого выигрыша в производительности для кода, чувствительного к производительности. В некоторых случаях сбой доступа к текущему экземпляру объекта представляет проблему с корректностью.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Пометьте член как статический (или совместно используемый в [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) или используйте "this"/"Me" в теле метода, если это уместно.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Можно отключить вывод предупреждения из этого правила для ранее отгруженного кода, для которого исправление будет критическим изменением.

## <a name="related-rules"></a>Связанные правила
 [CA1811: не используйте невызываемый закрытый код](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812: не создавайте внутренние классы без экземпляров](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1804: удалите неиспользуемые локальные переменные](../code-quality/ca1804-remove-unused-locals.md)
