---
title: 'CA1306: Задание языкового стандарта для типов данных | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1306
- SetLocaleForDataTypes
helpviewer_keywords:
- CA1306
- SetLocaleForDataTypes
ms.assetid: 104297b2-5806-4de0-a8d9-c589380a796c
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: edd1d6a7623f96f03403883ee2585d245414bb3b
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539026"
---
# <a name="ca1306-set-locale-for-data-types"></a>CA1306. Задавайте языковой стандарт для типов данных
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|SetLocaleForDataTypes|
|CheckId|CA1306|
|Категория|Microsoft. Globalization|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Метод или конструктор создал один или несколько <xref:System.Data.DataTable?displayProperty=fullName> экземпляров или <xref:System.Data.DataSet?displayProperty=fullName> явно не задал свойство Locale ( <xref:System.Data.DataTable.Locale%2A?displayProperty=fullName> или <xref:System.Data.DataSet.Locale%2A?displayProperty=fullName> ).

## <a name="rule-description"></a>Описание правила
 Языковой стандарт определяет элементы представления для данных, относящиеся к определенному языку и региональным параметрам, например форматирование, используемое для числовых значений, символов валют и порядка сортировки. При создании или необходимо <xref:System.Data.DataTable> <xref:System.Data.DataSet> явно задать языковой стандарт. По умолчанию языковой стандарт для этих типов является текущим языком и региональными параметрами. Для данных, которые хранятся в базе данных или файле и являются глобально общими, языковой стандарт обычно должен быть установлен в инвариантный язык и региональные параметры ( <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName> ). Если данные являются общими для разных языков и региональных параметров, использование языкового стандарта по умолчанию может привести к <xref:System.Data.DataTable> <xref:System.Data.DataSet> неправильному представлению или интерпретации содержимого или.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, явно задайте языковой стандарт для <xref:System.Data.DataTable> или <xref:System.Data.DataSet> .

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Предупреждение из этого правила можно отключить, если библиотека или приложение предназначено для ограниченной локальной аудитории, данные не являются общими, или параметр по умолчанию дает необходимое поведение во всех поддерживаемых сценариях.

## <a name="example"></a>Пример
 В следующем примере создаются два <xref:System.Data.DataTable> экземпляра.

 [!code-csharp[FxCop.Globalization.DataTable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DataTable/cs/FxCop.Globalization.DataTable.cs#1)]

## <a name="see-also"></a>См. также
 <xref:System.Data.DataTable?displayProperty=fullName> <xref:System.Data.DataSet?displayProperty=fullName>
 <xref:System.Globalization.CultureInfo?displayProperty=fullName>
 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>
 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>
