---
title: CA1811. Избегайте невызываемого частного кода
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidUncalledPrivateCode
- CA1811
helpviewer_keywords:
- CA1811
- AvoidUncalledPrivateCode
ms.assetid: aadbba74-7821-475f-8980-34d17c0a0a8b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 92a7542499eceeccbd62ce327b386dc099b726b2
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233624"
---
# <a name="ca1811-avoid-uncalled-private-code"></a>CA1811. Избегайте невызываемого частного кода

|||
|-|-|
|TypeName|AvoidUncalledPrivateCode|
|CheckId|CA1811|
|Категория|Microsoft. Performance|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина:
Частный или внутренний член (уровень сборки) не имеет вызывающих объектов в сборке, не вызывается средой CLR и не вызывается делегатом. Следующие члены не проверяются с помощью этого правила:

- Явные члены интерфейса.

- Статические конструкторы.

- Конструкторы сериализации.

- Методы, помеченные <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>как <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> или.

- Элементы, которые являются переопределениями.

## <a name="rule-description"></a>Описание правила
Это правило может сообщать ложные срабатывания при возникновении точек входа, которые в настоящее время не определяются логикой правила. Кроме того, компилятор может выдавать невызывающий код в сборку.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила, удалите невызывающий код или добавьте код, который его вызывает.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
В этом правиле можно отключить вывод предупреждений.

## <a name="related-rules"></a>Связанные правила
[CA1812 Избегайте использования внутренних классов без экземпляров](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

[CA1801: Проверка неиспользуемых параметров](../code-quality/ca1801-review-unused-parameters.md)

[CA1804 Удалить неиспользуемые локальные переменные](../code-quality/ca1804-remove-unused-locals.md)