---
title: CA2208. Правильно создавайте экземпляры исключений аргументов
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2208
- InstantiateArgumentExceptionsCorrectly
helpviewer_keywords:
- InstantiateArgumentExceptionsCorrectly
- CA2208
ms.assetid: e2a48939-d9fa-478c-b2f9-3bdbce07dff7
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 9f9425ab1ea9eadd3bd06d950118ce83ba5c35f9
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231649"
---
# <a name="ca2208-instantiate-argument-exceptions-correctly"></a>CA2208. Правильно создавайте экземпляры исключений аргументов

|||
|-|-|
|TypeName|InstantiateArgumentExceptionsCorrectly|
|CheckId|CA2208|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина:

Возможные причины включают в себя следующие ситуации.

- Выполняется вызов конструктора по умолчанию (без параметров) для типа исключения, который является или является производным от класса, <xref:System.ArgumentException>.

- Неверный строковый аргумент передается в параметризованный конструктор типа исключения, который является или является производным от <xref:System.ArgumentException>класса.

## <a name="rule-description"></a>Описание правила

Вместо вызова конструктора по умолчанию вызовите одну из перегрузок конструктора, которая позволяет предоставить более осмысленное сообщение об исключении. Сообщение об исключении должно ориентироваться на разработчика и ясно объяснить состояние ошибки, а также как исправить или избежать исключения.

Сигнатуры одного и двух конструкторов строк класса <xref:System.ArgumentException> и его производных типов не соответствуют положению `message` и `paramName` параметрам. Убедитесь, что эти конструкторы вызываются с правильными строковыми аргументами. Ниже приведены сигнатуры.

- <xref:System.ArgumentException>(строка `message`)
- <xref:System.ArgumentException>(строка `message`, строка `paramName`)
- <xref:System.ArgumentNullException>(строка `paramName`)
- <xref:System.ArgumentNullException>(строка `paramName`, строка `message`)
- <xref:System.ArgumentOutOfRangeException>(строка `paramName`)
- <xref:System.ArgumentOutOfRangeException>(строка `paramName`, строка `message`)
- <xref:System.DuplicateWaitObjectException>(строка `parameterName`)
- <xref:System.DuplicateWaitObjectException>(строка `parameterName`, строка `message`)

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, вызовите конструктор, принимающий сообщение, имя параметра или оба значения, и убедитесь, что аргументы являются правильными для вызываемого типа <xref:System.ArgumentException> .

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Предупреждение из этого правила можно отключить, только если параметризованный конструктор вызывается с правильными строковыми аргументами.

## <a name="example"></a>Пример

В следующем коде показан конструктор, который неправильно создает экземпляр <xref:System.ArgumentNullException>.

[!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_1.cpp)]
[!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_1.cs?range=3-6)]
[!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_1.vb)]

Следующий код устраняет предыдущее нарушение, переключая аргументы конструктора.

[!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_2.cpp)]
[!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_2.cs?range=3-6)]
[!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_2.vb)]

## <a name="related-rules"></a>Связанные правила

- [CA1507: Использовать NameOf вместо String](ca1507.md)