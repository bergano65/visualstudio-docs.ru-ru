---
title: 'CA1900: поля типа значения должны быть переносимыми'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1900
- ValueTypeFieldsShouldBePortable
helpviewer_keywords:
- ValueTypeFieldsShouldBePortable
- CA1900
ms.assetid: 1787d371-389f-4d39-b305-12b53bc0dfb9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 56c779095a68fc61c25412e6b895ea2bb5a635c3
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="ca1900-value-type-fields-should-be-portable"></a>CA1900: поля типа значения должны быть переносимыми
|||
|-|-|
|TypeName|ValueTypeFieldsShouldBePortable|
|CheckId|CA1900|
|Категория|Microsoft.Portability|
|Критическое изменение|Критическое, если поле может отображаться за пределами сборки.<br /><br /> Не критическое — если поле не отображается за пределами сборки.|

## <a name="cause"></a>Причина
 Это правило проверяет правильность выравнивания структур, объявленных с явной разметкой, при маршалировании в неуправляемый код на 64-разрядных операционных системах. Обращается к памяти и процесса произойдет сбой, если не будет устранена, это нарушение запрещены IA-64.

## <a name="rule-description"></a>Описание правила
 Структуры, имеющие явно заданный макет, который содержит неправильно выровненные поля могут привести к сбоям в 64-разрядных операционных системах.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Все поля, которые меньше, чем 8 байт должны иметь смещения, кратные их размера и поля размером 8 байт или более должны иметь смещения, кратные 8. Другим решением является использование `LayoutKind.Sequential` вместо `LayoutKind.Explicit`, если слишком много.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Это предупреждение следует отключать только в том случае, если оно возникает в ошибке.