---
title: CA2207. Используйте встроенную инициализацию статических полей типов значений
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InitializeValueTypeStaticFieldsInline
- CA2207
helpviewer_keywords:
- CA2207
- InitializeValueTypeStaticFieldsInline
ms.assetid: d1ea9d8b-ecc2-46ca-86e2-c41dd0e76658
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d2caeb78af5fed0c74c02c6e3f578fa34e765355
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920375"
---
# <a name="ca2207-initialize-value-type-static-fields-inline"></a>CA2207. Используйте встроенную инициализацию статических полей типов значений

|||
|-|-|
|TypeName|InitializeValueTypeStaticFieldsInline|
|CheckId|CA2207|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
Тип значения объявляет явный статический конструктор.

## <a name="rule-description"></a>Описание правила
При объявлении типа значения он проходит инициализацию по умолчанию, где все поля типа значения имеют нулевое значение, а всем полям ссылочного типа присваивается `null` значение (`Nothing` в Visual Basic). Явный статический конструктор гарантированно выполняется только перед вызовом конструктора экземпляра или статического члена типа. Таким образом, если тип создается без вызова конструктора экземпляра, выполнение статического конструктора не гарантируется.

Если все статические данные инициализируются встроенным образом и не объявлен явный статический конструктор, компиляторы C# и Visual Basic добавляют `beforefieldinit` флаг в определение класса MSIL. Компиляторы также добавляют закрытый статический конструктор, который содержит статический код инициализации. Этот закрытый статический конструктор гарантированно выполняется перед обращением к любым статическим полям типа.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила, инициализируйте все статические данные при объявлении и удалите статический конструктор.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Для этого правила отключать вывод предупреждений не следует.

## <a name="related-rules"></a>Связанные правила
[CA1810 Инициализация статических полей ссылочного типа встроенными](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)