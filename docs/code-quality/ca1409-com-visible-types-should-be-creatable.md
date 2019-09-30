---
title: CA1409. Видимые для COM типы должны быть создаваемыми
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
helpviewer_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
ms.assetid: 9f59569b-de15-4a38-b7cb-cff152972243
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 54630b7fba69ef96a2c08486e535ae45d8e614b8
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234767"
---
# <a name="ca1409-com-visible-types-should-be-creatable"></a>CA1409. Видимые для COM типы должны быть создаваемыми

|||
|-|-|
|TypeName|ComVisibleTypesShouldBeCreatable|
|CheckId|CA1409|
|Категория|Microsoft. взаимодействие|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина:
Ссылочный тип, специально помеченный как видимый для модели COM, содержит открытый параметризованный конструктор, но не содержит открытый конструктор по умолчанию (без параметров).

## <a name="rule-description"></a>Описание правила
Клиенты COM не могут создавать тип без открытого конструктора по умолчанию. Однако при наличии других средств для создания типа и передачи его клиенту (например, через возвращаемое значение вызова метода) Этот тип по-прежнему может быть доступен клиентам COM.

Правило не учитывает типы, которые являются производными <xref:System.Delegate?displayProperty=fullName>от.

По умолчанию следующие элементы видимы для COM: сборки, открытые типы, члены открытых экземпляров в открытых типах и все члены открытых типов значений.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила, добавьте открытый конструктор по умолчанию или удалите <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> из типа.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Предупреждение из этого правила можно отключить, если для создания и передачи объекта COM-клиенту используется другой способ.

## <a name="related-rules"></a>Связанные правила
[CA1017 Пометка сборок с помощью ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>См. также

- [Oпределение типов .NET для взаимодействия](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
- [Взаимодействие с неуправляемым кодом](/dotnet/framework/interop/index)