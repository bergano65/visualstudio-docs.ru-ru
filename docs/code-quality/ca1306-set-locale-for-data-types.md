---
title: 'CA1306: указывайте языковой стандарт для типов данных'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: e60a788d94a6c0d594ee45505b8f4ad9f64dbdff
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547192"
---
# <a name="ca1306-set-locale-for-data-types"></a>CA1306: указывайте языковой стандарт для типов данных

|||
|-|-|
|TypeName|SetLocaleForDataTypes|
|CheckId|CA1306|
|Категория|Microsoft.Globalization|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Метод или конструктор для создания одного или нескольких <xref:System.Data.DataTable?displayProperty=fullName> или <xref:System.Data.DataSet?displayProperty=fullName> экземпляров и не был явно задано свойство locale (<xref:System.Data.DataTable.Locale%2A?displayProperty=fullName> или <xref:System.Data.DataSet.Locale%2A?displayProperty=fullName>).

## <a name="rule-description"></a>Описание правила
 Языковой стандарт определяет язык и региональные параметры представление элементов данных, таких как форматирование для числовых значений, символы валют и порядок сортировки. При создании <xref:System.Data.DataTable> или <xref:System.Data.DataSet>, необходимо явно задать языковой стандарт. По умолчанию языковой стандарт для этих типов — текущий язык и региональные параметры. Для данных, хранящихся в базе данных или файла и глобально, языковой стандарт обычно задается для инвариантного языка и региональных параметров (<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>). Если данные распределяются на языки и региональные параметры, с помощью языкового стандарта по умолчанию может привести к содержимое <xref:System.Data.DataTable> или <xref:System.Data.DataSet> представленные или неправильной интерпретации.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, необходимо явно задать языковой стандарт для <xref:System.Data.DataTable> или <xref:System.Data.DataSet>.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение из этого правила, когда библиотека или приложение предназначены для ограниченной локальной аудитории, данные не используется совместно или по умолчанию возвращает желаемое поведение во всех поддерживаемых сценариях.

## <a name="example"></a>Пример
 В следующем примере создается два <xref:System.Data.DataTable> экземпляров.

 [!code-csharp[FxCop.Globalization.DataTable#1](../code-quality/codesnippet/CSharp/ca1306-set-locale-for-data-types_1.cs)]

## <a name="see-also"></a>См. также

- <xref:System.Data.DataTable?displayProperty=fullName>
- <xref:System.Data.DataSet?displayProperty=fullName>
- <xref:System.Globalization.CultureInfo?displayProperty=fullName>
- <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>
- <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>