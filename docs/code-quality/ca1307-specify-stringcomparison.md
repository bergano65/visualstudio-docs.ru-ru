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
ms.openlocfilehash: ce2da2c1ff5b2f74d8b4d6341050c1895b68955a
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922297"
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307. Указывайте StringComparison

|||
|-|-|
|TypeName|SpecifyStringComparison|
|CheckId|CA1307|
|Категория|Microsoft. Globalization|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
Операция сравнения строк использует перегрузку метода, которая не задает <xref:System.StringComparison> параметр.

## <a name="rule-description"></a>Описание правила
Многие операции со <xref:System.String.Compare%2A> строками, наиболее важные <xref:System.String.Equals%2A> методы и, предоставляют перегрузку, <xref:System.StringComparison> которая принимает значение перечисления в качестве параметра.

Всякий раз, когда существует перегрузка <xref:System.StringComparison> , которая принимает параметр, ее следует использовать вместо перегрузки, которая не принимает этот параметр. При явном задании этого параметра код часто становится более четким и простым в обслуживании.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила, измените методы сравнения строк на перегрузки, принимающие <xref:System.StringComparison> перечисление в качестве параметра. Например: измените `String.Compare(str1, str2)` на `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Можно отключить вывод предупреждения из этого правила, если библиотека или приложение предназначено для ограниченной локальной аудитории и, следовательно, не будет локализовано.

## <a name="see-also"></a>См. также

- [Предупреждения глобализации](../code-quality/globalization-warnings.md)
- [CA1309 Использовать Ordinal StringComparison](../code-quality/ca1309-use-ordinal-stringcomparison.md)