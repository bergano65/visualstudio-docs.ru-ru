---
title: 'CA1307: укажите StringComparison | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1307
- SpecifyStringComparison
helpviewer_keywords:
- CA1307
- SpecifyStringComparison
ms.assetid: 9b0d5e71-1683-4a0d-bc4a-68b2fbd8af71
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 033d8f0e22ec040ffb10821993a5a9c647ee401e
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85538922"
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307. Указывайте StringComparison
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|Значение|
|-|-|
|TypeName|SpecifyStringComparison|
|CheckId|CA1307|
|Категория|Microsoft. Globalization|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Операция сравнения строк использует перегрузку метода, которая не задает <xref:System.StringComparison> параметр.

## <a name="rule-description"></a>Описание правила
 Многие операции со строками, наиболее <xref:System.String.Compare%2A> важные <xref:System.String.Equals%2A> методы и, предоставляют перегрузку, которая принимает <xref:System.StringComparison> значение перечисления в качестве параметра.

 Всякий раз, когда существует перегрузка, которая принимает <xref:System.StringComparison> параметр, ее следует использовать вместо перегрузки, которая не принимает этот параметр. При явном задании этого параметра код часто становится более четким и простым в обслуживании.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, измените методы сравнения строк на перегрузки, принимающие <xref:System.StringComparison> перечисление в качестве параметра. Например: измените `String.Compare(str1, str2)` на `String.Compare(str1, str2, StringComparison.Ordinal)` .

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Можно отключить вывод предупреждения из этого правила, если библиотека или приложение предназначено для ограниченной локальной аудитории и, следовательно, не будет локализовано.

## <a name="see-also"></a>См. также
 [Предупреждения глобализации](../code-quality/globalization-warnings.md) [CA1309: используйте Ordinal StringComparison](../code-quality/ca1309-use-ordinal-stringcomparison.md)
