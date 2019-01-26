---
title: CA1811. Избегайте невызываемого частного кода
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 6fca30671616dbe1e9d1c3468420d4526aa02250
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54975157"
---
# <a name="ca1811-avoid-uncalled-private-code"></a>CA1811. Избегайте невызываемого частного кода

|||
|-|-|
|TypeName|AvoidUncalledPrivateCode|
|CheckId|CA1811|
|Категория|Microsoft.Performance|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Член закрытым или внутренним (на уровне сборки) не поддерживает вызывающих объектов в сборке, не вызывается средой CLR и не вызывается делегат. Это правило не проверяются следующие члены:

- Явные члены интерфейса.

- Статические конструкторы.

- Конструкторы сериализации.

- Методы, помеченные как <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> или <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>.

- Члены, которые являются переопределениями.

## <a name="rule-description"></a>Описание правила
 Это правило можно отчетов ложных положительных результатов, в случае точки входа, не распознаются в настоящее время логике правила. Кроме того компилятор может выдать noncallable кода в сборку.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, удалите noncallable код или добавьте код, который ее вызывает.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение из этого правила.

## <a name="related-rules"></a>Связанные правила
 [CA1812: Избегайте неиспользуемых внутренних классов](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801: Проверьте неиспользуемые параметры](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804: Удалите неиспользуемые локальные переменные](../code-quality/ca1804-remove-unused-locals.md)