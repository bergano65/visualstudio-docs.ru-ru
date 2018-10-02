---
title: 'CA1409: Видимые COM-типы должны быть создаваемыми | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
helpviewer_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
ms.assetid: 9f59569b-de15-4a38-b7cb-cff152972243
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a9b946fc68774d33bc17a37dafc5366d6532f745
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47592017"
---
# <a name="ca1409-com-visible-types-should-be-creatable"></a>CA1409: видимые COM-типы должны быть создаваемыми
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA1409: видимые COM-типы должны быть создаваемыми](https://docs.microsoft.com/visualstudio/code-quality/ca1409-com-visible-types-should-be-creatable).

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
 [CA1017: помечайте сборки атрибутом ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>См. также
 [Уточнение типов .NET для взаимодействия](http://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd) [взаимодействие с неуправляемым кодом](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)



