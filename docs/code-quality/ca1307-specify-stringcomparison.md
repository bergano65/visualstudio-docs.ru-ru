---
title: CA1307. Указывайте StringComparison
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1307
- SpecifyStringComparison
helpviewer_keywords:
- CA1307
- SpecifyStringComparison
ms.assetid: 9b0d5e71-1683-4a0d-bc4a-68b2fbd8af71
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a3aabd73a3c234be61cecdf68fbc92fc7e52883e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62797342"
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307. Указывайте StringComparison

|||
|-|-|
|TypeName|SpecifyStringComparison|
|CheckId|CA1307|
|Категория|Microsoft.Globalization|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Операции сравнения строк используется перегрузка метода, которая не задает <xref:System.StringComparison> параметра.

## <a name="rule-description"></a>Описание правила
 Многие строковые операции, наиболее важных <xref:System.String.Compare%2A> и <xref:System.String.Equals%2A> предоставляют перегрузку, принимающую <xref:System.StringComparison> значение перечисления в качестве параметра.

 Каждый раз, когда существует перегрузка, принимающую <xref:System.StringComparison> параметр, он должен использоваться вместо перегрузку, которая не принимает этот параметр. Часто, явно установив этот параметр, код становится более ясным и удобный в сопровождении.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, измените методы сравнения строк на перегрузки, принимающие <xref:System.StringComparison> перечисления в качестве параметра. Например: изменить `String.Compare(str1, str2)` для `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение из этого правила, если библиотека или приложение предназначено для ограниченного круга локальных пользователей и поэтому не будет локализовано.

## <a name="see-also"></a>См. также

- [Предупреждения глобализации](../code-quality/globalization-warnings.md)
- [CA1309: Используйте порядковый параметр StringComparison](../code-quality/ca1309-use-ordinal-stringcomparison.md)