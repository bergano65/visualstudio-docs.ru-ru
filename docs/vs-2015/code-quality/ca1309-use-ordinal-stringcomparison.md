---
title: 'CA1309: используйте порядковое StringComparison | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseOrdinalStringComparison
- CA1309
helpviewer_keywords:
- UseOrdinalStringComparison
- CA1309
ms.assetid: 19be0854-cb6e-4efd-a4c8-a5c1fc6f7a71
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: be60d2a1dcb769a0b7a8574984de3d288bf57af4
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85538883"
---
# <a name="ca1309-use-ordinal-stringcomparison"></a>CA1309. Используйте порядковый параметр StringComparison
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|UseOrdinalStringComparison|
|CheckId|CA1309|
|Категория|Microsoft. Globalization|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Нелингвистическая операция сравнения строк не устанавливает <xref:System.StringComparison> параметр в значение **Ordinal** или **OrdinalIgnoreCase**.

## <a name="rule-description"></a>Описание правила
 Многие операции со строками, наиболее <xref:System.String.Compare%2A?displayProperty=fullName> важные <xref:System.String.Equals%2A?displayProperty=fullName> методы и, теперь предоставляют перегрузку, которая принимает <xref:System.StringComparison?displayProperty=fullName> значение перечисления в качестве параметра.

 При указании либо **StringComparison. Ordinal** , либо **StringComparison. OrdinalIgnoreCase**, сравнение строк будет нелингвистическим. То есть функции, характерные для естественного языка, игнорируются при принятии решений по сравнению. Это означает, что решения основаны на простых сравнениях байтов и не учитывают регистр или таблицы эквивалентности, параметризованные языком и региональными параметрами. В результате, явно присвоив параметру значение **StringComparison. Ordinal** или **StringComparison. OrdinalIgnoreCase**, ваш код часто получает скорость, увеличивает правильность и становится более надежным.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, измените метод сравнения строк на перегрузку, принимающую <xref:System.StringComparison?displayProperty=fullName> перечисление в качестве параметра, и укажите либо **Ordinal** , либо **OrdinalIgnoreCase**. Например, измените `String.Compare(str1, str2)` на `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Предупреждение из этого правила можно отключить, если библиотека или приложение предназначены для ограниченной локальной аудитории или если необходимо использовать семантику текущего языка и региональных параметров.

## <a name="see-also"></a>См. также
 [Предупреждения глобализации](../code-quality/globalization-warnings.md) [CA1307: укажите StringComparison](../code-quality/ca1307-specify-stringcomparison.md)
