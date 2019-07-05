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
ms.openlocfilehash: 2110a8d0b58d87a4554971cf00af6441d293aa91
ms.sourcegitcommit: 92a04c57ac0a49f304fa2ea5043436f30068c3cd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/21/2019
ms.locfileid: "65975892"
---
# <a name="ca2208-instantiate-argument-exceptions-correctly"></a>CA2208. Правильно создавайте экземпляры исключений аргументов

|||
|-|-|
|TypeName|InstantiateArgumentExceptionsCorrectly|
|CheckId|CA2208|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Возможны следующие причины следующих ситуациях.

- Выполняется вызов конструктора по умолчанию (без параметров) типа исключения, которое, или унаследованный от него, <xref:System.ArgumentException>.

- Неправильный аргумент строки передается параметризованному конструктору, или унаследованный от него, тип исключения <xref:System.ArgumentException>.

## <a name="rule-description"></a>Описание правила

Вместо вызова конструктора по умолчанию, вызовите одну из перегрузок конструктора, что позволяет более понятное сообщение об исключении, должны быть предоставлены. Сообщение об исключении должно предназначаться разработчикам и понятно объяснить условие ошибки и как исправить или избежать исключения.

Сигнатуры двух и строка конструкторы <xref:System.ArgumentException> и его производные типы не соответствуют по отношению к положение `message` и `paramName` параметров. Убедитесь, что эти конструкторы вызываются с правильными аргументами. Сигнатуры выглядят следующим образом:

- <xref:System.ArgumentException>(строка `message`)
- <xref:System.ArgumentException>(строка `message`, строка `paramName`)
- <xref:System.ArgumentNullException>(строка `paramName`)
- <xref:System.ArgumentNullException>(строка `paramName`, строка `message`)
- <xref:System.ArgumentOutOfRangeException>(строка `paramName`)
- <xref:System.ArgumentOutOfRangeException>(строка `paramName`, строка `message`)
- <xref:System.DuplicateWaitObjectException>(строка `parameterName`)
- <xref:System.DuplicateWaitObjectException>(строка `parameterName`, строка `message`)

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, вызовите конструктор, который принимает сообщение и имя параметра и убедитесь, что аргументы имеют правильный тип <xref:System.ArgumentException> вызова.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Его можно безопасно подавить предупреждение из этого правила, только в том случае, если параметризованный конструктор вызывается с правильными аргументами.

## <a name="example"></a>Пример

В следующем коде показан конструктор, который неправильно создает экземпляр <xref:System.ArgumentNullException>.

[!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_1.cpp)]
[!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_1.cs?range=3-6)]
[!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_1.vb)]

Следующий код предыдущее нарушение устраняется путем переключения аргументы конструктора.

[!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_2.cpp)]
[!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_2.cs?range=3-6)]
[!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_2.vb)]

## <a name="related-rules"></a>Связанные правила

- [CA1507: Используйте nameof вместо строки](ca1507.md)