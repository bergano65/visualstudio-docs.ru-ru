---
title: CA1306. Задавайте языковой стандарт для типов данных
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1306
- SetLocaleForDataTypes
helpviewer_keywords:
- CA1306
- SetLocaleForDataTypes
ms.assetid: 104297b2-5806-4de0-a8d9-c589380a796c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aaf16ccd187681be7406fdadbde620a167a40c96
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235027"
---
# <a name="ca1306-set-locale-for-data-types"></a>CA1306. Задавайте языковой стандарт для типов данных

|||
|-|-|
|TypeName|SetLocaleForDataTypes|
|CheckId|CA1306|
|Категория|Microsoft. Globalization|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина:
Метод или конструктор создал <xref:System.Data.DataTable?displayProperty=fullName> один или несколько экземпляров или <xref:System.Data.DataSet?displayProperty=fullName> явно не задал свойство Locale (<xref:System.Data.DataTable.Locale%2A?displayProperty=fullName> или <xref:System.Data.DataSet.Locale%2A?displayProperty=fullName>).

## <a name="rule-description"></a>Описание правила
Языковой стандарт определяет элементы представления для данных, относящиеся к определенному языку и региональным параметрам, например форматирование, используемое для числовых значений, символов валют и порядка сортировки. При создании <xref:System.Data.DataTable> или <xref:System.Data.DataSet>необходимо явно задать языковой стандарт. По умолчанию языковой стандарт для этих типов является текущим языком и региональными параметрами. Для данных, которые хранятся в базе данных или файле и являются глобально общими, языковой стандарт обычно должен быть установлен в инвариантный язык<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>и региональные параметры (). Если данные являются общими для разных языков и региональных параметров, использование языкового стандарта по умолчанию <xref:System.Data.DataSet> может привести к неправильному представлению или интерпретации содержимого <xref:System.Data.DataTable> или.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила, явно задайте языковой стандарт для <xref:System.Data.DataTable> или. <xref:System.Data.DataSet>

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Предупреждение из этого правила можно отключить, если библиотека или приложение предназначено для ограниченной локальной аудитории, данные не являются общими, или параметр по умолчанию дает необходимое поведение во всех поддерживаемых сценариях.

## <a name="example"></a>Пример
В следующем примере создаются два <xref:System.Data.DataTable> экземпляра.

[!code-csharp[FxCop.Globalization.DataTable#1](../code-quality/codesnippet/CSharp/ca1306-set-locale-for-data-types_1.cs)]

## <a name="see-also"></a>См. также

- <xref:System.Data.DataTable?displayProperty=fullName>
- <xref:System.Data.DataSet?displayProperty=fullName>
- <xref:System.Globalization.CultureInfo?displayProperty=fullName>
- <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>
- <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>