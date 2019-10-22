---
title: 'CA1820: Проверка на наличие пустых строк с использованием длины строки | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
helpviewer_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
ms.assetid: da1e70c8-b1dc-46b9-8b8f-4e6e48339681
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6711dac907de2777cf892b20269fec7e99d3bd6f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657504"
---
# <a name="ca1820-test-for-empty-strings-using-string-length"></a>CA1820: проверьте наличие пустых строк путем проверки длины строки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TestForEmptyStringsUsingStringLength|
|CheckId|CA1820|
|Категория|Microsoft. Performance|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Строка сравнивается с пустой строкой с помощью <xref:System.Object.Equals%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Описание правила
 Сравнение строк с помощью свойства <xref:System.String.Length%2A?displayProperty=fullName> или метода <xref:System.String.IsNullOrEmpty%2A?displayProperty=fullName> выполняется значительно быстрее, чем при использовании <xref:System.Object.Equals%2A>. Это связано с тем, что <xref:System.Object.Equals%2A> выполняет значительно больше инструкций MSIL, чем <xref:System.String.IsNullOrEmpty%2A> или количество выполняемых инструкций для получения значения свойства <xref:System.String.Length%2A> и его сравнения с нулем.

 Следует иметь в виду, что <xref:System.Object.Equals%2A> и <xref:System.String.Length%2A> = = 0 ведут себя по-разному для строк со значением NULL. Если попытаться получить значение свойства <xref:System.String.Length%2A> в строке null, среда CLR выдаст исключение <xref:System.NullReferenceException?displayProperty=fullName>. При выполнении сравнения между пустой строкой и пустой строкой среда CLR не создает исключение. сравнение возвращает `false`. Тестирование на значение NULL не оказывает существенного влияния на относительную производительность этих двух подходов. При нацеливании [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] используйте метод <xref:System.String.IsNullOrEmpty%2A>. В противном случае по возможности используйте сравнение <xref:System.String.Length%2A> = =.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, измените сравнение, чтобы использовать свойство <xref:System.String.Length%2A> и проверить пустую строку. Если нацеливание на [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)], используйте метод <xref:System.String.IsNullOrEmpty%2A>.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 В этом правиле можно отключить вывод предупреждений, если производительность не является проблемой.

## <a name="example"></a>Пример
 В следующем примере показаны различные методы, используемые для поиска пустой строки.

 [!code-csharp[FxCop.Performance.StringTest#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.StringTest/cs/FxCop.Performance.StringTest.cs#1)]
