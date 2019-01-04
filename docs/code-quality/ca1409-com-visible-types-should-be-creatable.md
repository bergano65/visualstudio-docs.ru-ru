---
title: CA1409. Видимые для COM типы должны быть создаваемыми
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5fd168c5174dcc403a38c6eb3e443c3711fce537
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53821692"
---
# <a name="ca1409-com-visible-types-should-be-creatable"></a>CA1409. Видимые для COM типы должны быть создаваемыми

|||
|-|-|
|TypeName|ComVisibleTypesShouldBeCreatable|
|CheckId|CA1409|
|Категория|Microsoft.Interoperability|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Ссылочный тип, который специально помечен как видимый для модели объектов компонента (COM) содержит открытый параметризованный конструктор, но не содержит открытого конструктора по умолчанию (без параметров).

## <a name="rule-description"></a>Описание правила
 Тип без открытого конструктора по умолчанию невозможно создать COM-клиентами. Однако тип по-прежнему возможен COM-клиентами, если другие средства для создания типа и передачи его клиенту (например, через возвращаемое значение вызова метода).

 Правило не учитывает типы, которые являются производными от <xref:System.Delegate?displayProperty=fullName>.

 По умолчанию следующие являются видимыми для COM: сборки, открытые типы, члены открытых экземпляров в открытых типов и все члены открытых типов значения.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, добавьте открытый конструктор по умолчанию или удалите <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> из типа.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение из этого правила, если другие способы, позволяющие создать и передать ему объект COM-клиенту.

## <a name="related-rules"></a>Связанные правила
 [CA1017: Пометьте сборки атрибутом ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>См. также

- [Oпределение типов .NET для взаимодействия](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
- [Взаимодействие с неуправляемым кодом](/dotnet/framework/interop/index)