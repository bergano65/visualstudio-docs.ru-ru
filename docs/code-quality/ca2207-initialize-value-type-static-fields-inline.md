---
title: 'CA2207: инициализируйте статические поля типа значений встроенными средствами'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 883e5d842346a0821b54b2b4eacad3cbc92028b6
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="ca2207-initialize-value-type-static-fields-inline"></a>CA2207: инициализируйте статические поля типа значений встроенными средствами
|||
|-|-|
|TypeName|InitializeValueTypeStaticFieldsInline|
|CheckId|CA2207|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Тип значения объявляет явный статический конструктор.

## <a name="rule-description"></a>Описание правила
 При объявлении типа значения, к нему применяется инициализация по умолчанию, где все поля типа значения равны нулю, а все поля ссылочного типа присваивается `null` (`Nothing` в Visual Basic). Явный статический конструктор только обязательно выполняется перед конструктором экземпляра или вызова статического члена типа. Таким образом Если тип создается без вызова конструктора экземпляра, статический конструктор не гарантируется для запуска.

 Если все статические данные инициализированный встроенным образом и объявляется явный статический конструктор, компиляторы C# и Visual Basic добавьте `beforefieldinit` флаг к определению класса MSIL. Компиляторы также добавляют закрытый статический конструктор, который содержит статический код инициализации. Этот закрытый статический конструктор обязательно выполняется перед доступны все статические поля типа.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила инициализацию всех статических данных при объявляется и удалите статический конструктор.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="related-rules"></a>Связанные правила
 [CA1810: инициализируйте статические поля ссылочного типа встроенными средствами](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)