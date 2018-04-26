---
title: 'CA1309: используйте порядковый параметр StringComparison'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseOrdinalStringComparison
- CA1309
helpviewer_keywords:
- UseOrdinalStringComparison
- CA1309
ms.assetid: 19be0854-cb6e-4efd-a4c8-a5c1fc6f7a71
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ebea0208beddebb82484297eb990baa9b22c58e8
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="ca1309-use-ordinal-stringcomparison"></a>CA1309: используйте порядковый параметр StringComparison
|||
|-|-|
|TypeName|UseOrdinalStringComparison|
|CheckId|CA1309|
|Категория|Microsoft.Globalization|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Не задает операции сравнения строк, лингвистической <xref:System.StringComparison> параметра к **порядковый номер** или **OrdinalIgnoreCase**.

## <a name="rule-description"></a>Описание правила
 Многие строковые операции, наиболее важные <xref:System.String.Compare%2A?displayProperty=fullName> и <xref:System.String.Equals%2A?displayProperty=fullName> методы, теперь предоставляют перегрузку, которая принимает <xref:System.StringComparison?displayProperty=fullName> значение перечисления в качестве параметра.

 При указании либо **StringComparison.Ordinal** или **StringComparison.OrdinalIgnoreCase**, то строковое сравнение будет лингвистической. То есть функции, характерные для естественного языка игнорируются при принятии решений сравнения. Это означает, что решения основываются на простых байтовых сравнений и игнорировать таблиц регистров или эквивалентности, которые параметризуются языком и региональными параметрами. В результате путем явного задания для параметра либо **StringComparison.Ordinal** или **StringComparison.OrdinalIgnoreCase**, кода часто увеличивается скорость, повышает правильность и становится более надежным.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, измените метод сравнения строк на перегрузку, которая принимает <xref:System.StringComparison?displayProperty=fullName> перечисления в качестве параметра и указать либо **порядковый номер** или **OrdinalIgnoreCase**. Например, измените `String.Compare(str1, str2)` на `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Можно безопасно отключать предупреждение из этого правила, если библиотека или приложение предназначено для ограниченного круга локальных пользователей или когда следует использовать семантику текущего языка и региональных параметров.

## <a name="see-also"></a>См. также
 [Предупреждения глобализации](../code-quality/globalization-warnings.md) [CA1307: укажите StringComparison](../code-quality/ca1307-specify-stringcomparison.md)