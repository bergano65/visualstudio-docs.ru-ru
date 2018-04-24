---
title: 'CA1811: не используйте невызываемый закрытый код'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d7f31b27740b286065221838e733d99e94b3307d
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="ca1811-avoid-uncalled-private-code"></a>CA1811: не используйте невызываемый закрытый код
|||
|-|-|
|TypeName|AvoidUncalledPrivateCode|
|CheckId|CA1811|
|Категория|Microsoft.Performance|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 (На уровне сборки) член закрытым или внутренним ни объектами сборки, не используется средой CLR и не вызывается делегат. Это правило не проверяются следующие члены:

-   Явные члены интерфейса.

-   Статические конструкторы.

-   Конструкторы сериализации.

-   Методы, помеченные <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> или <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>.

-   Элементы, которые являются переопределениями.

## <a name="rule-description"></a>Описание правила
 Это правило можно отчетов ложных положительных результатов в случае точки входа, в настоящее время не определены логикой правила. Кроме того компилятор может вставить noncallable кода в сборку.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, удалите noncallable код или добавьте код, который вызывает ее.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение из этого правила.

## <a name="related-rules"></a>Связанные правила
 [CA1812: не создавайте внутренние классы без экземпляров](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801: проверьте неиспользуемые параметры](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804: удалите неиспользуемые локальные переменные](../code-quality/ca1804-remove-unused-locals.md)