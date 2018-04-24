---
title: 'CA1306: указывайте языковой стандарт для типов данных'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d7c95c72978e3828d566598e6076bde904169f4b
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="ca1306-set-locale-for-data-types"></a>CA1306: указывайте языковой стандарт для типов данных
|||
|-|-|
|TypeName|SetLocaleForDataTypes|
|CheckId|CA1306|
|Категория|Microsoft.Globalization|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Метод или конструктор для создания одного или нескольких <xref:System.Data.DataTable?displayProperty=fullName> или <xref:System.Data.DataSet?displayProperty=fullName> экземпляров и не было явно задано свойство языка (<xref:System.Data.DataTable.Locale%2A?displayProperty=fullName> или <xref:System.Data.DataSet.Locale%2A?displayProperty=fullName>).

## <a name="rule-description"></a>Описание правила
 Языковой стандарт определяет язык и региональные параметры представление элементов данных, таких как форматирование для числовых значений, денежных единиц и порядок сортировки. При создании <xref:System.Data.DataTable> или <xref:System.Data.DataSet>, необходимо явно задать языковой стандарт. По умолчанию языковой стандарт для этих типов — текущий язык и региональные параметры. Для данных, хранящихся в базе данных или файле и доступны глобально, языковой стандарт обычно задается инвариантного языка и региональных параметров (<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>). Если данные используются совместно языков и региональных параметров, использует локаль по умолчанию может привести к содержимое <xref:System.Data.DataTable> или <xref:System.Data.DataSet> должны быть представлены или неправильной интерпретации.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, необходимо явно задать языковой стандарт для <xref:System.Data.DataTable> или <xref:System.Data.DataSet>.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Можно безопасно отключать предупреждение из этого правила, если библиотека или приложение предназначены для ограниченного круга локальных пользователей, данные не являются общими или применение параметров по умолчанию допустимо для всех поддерживаемых сценариях.

## <a name="example"></a>Пример
 В следующем примере создается два <xref:System.Data.DataTable> экземпляров.

 [!code-csharp[FxCop.Globalization.DataTable#1](../code-quality/codesnippet/CSharp/ca1306-set-locale-for-data-types_1.cs)]

## <a name="see-also"></a>См. также
 <xref:System.Data.DataTable?displayProperty=fullName> <xref:System.Data.DataSet?displayProperty=fullName> <xref:System.Globalization.CultureInfo?displayProperty=fullName> <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>