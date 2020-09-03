---
title: 'CA1409: типы, видимые для com, должны быть создаваемыми | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
helpviewer_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
ms.assetid: 9f59569b-de15-4a38-b7cb-cff152972243
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 180a8d6bbc7f035fa0ae2eeafaa4e2c884cddc8d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547333"
---
# <a name="ca1409-com-visible-types-should-be-creatable"></a>CA1409. Видимые для COM типы должны быть создаваемыми
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|ComVisibleTypesShouldBeCreatable|
|CheckId|CA1409|
|Категория|Microsoft. взаимодействие|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Ссылочный тип, специально помеченный как видимый для модели COM, содержит открытый параметризованный конструктор, но не содержит открытый конструктор по умолчанию (без параметров).

## <a name="rule-description"></a>Описание правила
 Клиенты COM не могут создавать тип без открытого конструктора по умолчанию. Однако при наличии других средств для создания типа и передачи его клиенту (например, через возвращаемое значение вызова метода) Этот тип по-прежнему может быть доступен клиентам COM.

 Правило не учитывает типы, которые являются производными от <xref:System.Delegate?displayProperty=fullName> .

 По умолчанию следующие элементы видимы для COM: сборки, открытые типы, члены открытых экземпляров в открытых типах и все члены открытых типов значений.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, добавьте открытый конструктор по умолчанию или удалите <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> из типа.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Предупреждение из этого правила можно отключить, если для создания и передачи объекта COM-клиенту используется другой способ.

## <a name="related-rules"></a>Связанные правила
 [CA1017. Пометьте сборки с помощью ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>См. также:
 [Уточнение типов .NET для](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd) взаимодействия [с неуправляемым кодом](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
