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
ms.openlocfilehash: 111f0b85a601d931ac17bde46f7170fa81e71815
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661399"
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307: укажите StringComparison
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SpecifyStringComparison|
|CheckId|CA1307|
|Категория|Microsoft. Globalization|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Операция сравнения строк использует перегрузку метода, которая не задает параметр <xref:System.StringComparison>.

## <a name="rule-description"></a>Описание правила
 Многие операции со строками, наиболее важные для методов <xref:System.String.Compare%2A> и <xref:System.String.Equals%2A>, предоставляют перегрузку, которая принимает в качестве параметра значение перечисления <xref:System.StringComparison>.

 Всякий раз, когда существует перегрузка, которая принимает параметр <xref:System.StringComparison>, ее следует использовать вместо перегрузки, которая не принимает этот параметр. При явном задании этого параметра код часто становится более четким и простым в обслуживании.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, измените методы сравнения строк на перегрузки, принимающие перечисление <xref:System.StringComparison> в качестве параметра. Например: измените `String.Compare(str1, str2)` на `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Можно отключить вывод предупреждения из этого правила, если библиотека или приложение предназначено для ограниченной локальной аудитории и, следовательно, не будет локализовано.

## <a name="see-also"></a>См. также раздел
 [Предупреждения глобализации](../code-quality/globalization-warnings.md) [CA1309: используйте Ordinal StringComparison](../code-quality/ca1309-use-ordinal-stringcomparison.md)
