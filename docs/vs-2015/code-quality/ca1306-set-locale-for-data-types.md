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
ms.openlocfilehash: 03344f0b19552aa00270c8a6fa760c6ba6ee75f4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661415"
---
# <a name="ca1306-set-locale-for-data-types"></a>CA1306: указывайте языковой стандарт для типов данных
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SetLocaleForDataTypes|
|CheckId|CA1306|
|Категория|Microsoft. Globalization|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Метод или конструктор создал один или несколько <xref:System.Data.DataTable?displayProperty=fullName> или <xref:System.Data.DataSet?displayProperty=fullName> экземпляров и не задал свойство локали явным образом (<xref:System.Data.DataTable.Locale%2A?displayProperty=fullName> или <xref:System.Data.DataSet.Locale%2A?displayProperty=fullName>).

## <a name="rule-description"></a>Описание правила
 Языковой стандарт определяет элементы представления для данных, относящиеся к определенному языку и региональным параметрам, например форматирование, используемое для числовых значений, символов валют и порядка сортировки. При создании <xref:System.Data.DataTable> или <xref:System.Data.DataSet> необходимо явно задать языковой стандарт. По умолчанию языковой стандарт для этих типов является текущим языком и региональными параметрами. Для данных, которые хранятся в базе данных или файле и являются глобально общими, языковой стандарт обычно должен быть установлен в инвариантный язык и региональные параметры (<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>). Если данные являются общими для разных языков и региональных параметров, использование языкового стандарта по умолчанию может привести к неправильному представлению или интерпретации содержимого <xref:System.Data.DataTable> или <xref:System.Data.DataSet>.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, явно задайте языковой стандарт для <xref:System.Data.DataTable> или <xref:System.Data.DataSet>.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Предупреждение из этого правила можно отключить, если библиотека или приложение предназначено для ограниченной локальной аудитории, данные не являются общими, или параметр по умолчанию дает необходимое поведение во всех поддерживаемых сценариях.

## <a name="example"></a>Пример
 В следующем примере создаются два экземпляра <xref:System.Data.DataTable>.

 [!code-csharp[FxCop.Globalization.DataTable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DataTable/cs/FxCop.Globalization.DataTable.cs#1)]

## <a name="see-also"></a>См. также раздел
 <xref:System.Data.DataTable?displayProperty=fullName> <xref:System.Data.DataSet?displayProperty=fullName>
 <xref:System.Globalization.CultureInfo?displayProperty=fullName>
 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>
 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>
