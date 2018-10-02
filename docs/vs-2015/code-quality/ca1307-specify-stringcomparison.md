---
title: 'CA1307: Укажите StringComparison | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1307
- SpecifyStringComparison
helpviewer_keywords:
- CA1307
- SpecifyStringComparison
ms.assetid: 9b0d5e71-1683-4a0d-bc4a-68b2fbd8af71
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2c96b8c895106337a8578b6662c0e61830b38f55
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591900"
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307: укажите StringComparison
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA1307: укажите StringComparison](https://docs.microsoft.com/visualstudio/code-quality/ca1307-specify-stringcomparison).

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
 [Предупреждения глобализации](../code-quality/globalization-warnings.md) [CA1309: используйте порядковый параметр StringComparison](../code-quality/ca1309-use-ordinal-stringcomparison.md)



