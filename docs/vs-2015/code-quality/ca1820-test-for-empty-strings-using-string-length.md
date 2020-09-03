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
ms.openlocfilehash: 296eb6407e3ce63b0eb28ff86c215c12ec724ce9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545318"
---
# <a name="ca1820-test-for-empty-strings-using-string-length"></a>CA1820. Проверяйте наличие пустых строк, используя длину строки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|TestForEmptyStringsUsingStringLength|
|CheckId|CA1820|
|Категория|Microsoft. Performance|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Строка сравнивается с пустой строкой с помощью <xref:System.Object.Equals%2A?displayProperty=fullName> .

## <a name="rule-description"></a>Описание правила
 Сравнение строк с помощью <xref:System.String.Length%2A?displayProperty=fullName> свойства или <xref:System.String.IsNullOrEmpty%2A?displayProperty=fullName> метода выполняется значительно быстрее, чем при использовании <xref:System.Object.Equals%2A> . Это обусловлено тем, что <xref:System.Object.Equals%2A> выполняет значительно больше инструкций MSIL, чем <xref:System.String.IsNullOrEmpty%2A> или количество выполняемых инструкций для получения <xref:System.String.Length%2A> значения свойства и сравнивает его с нулем.

 Следует иметь в виду, что функции <xref:System.Object.Equals%2A> и <xref:System.String.Length%2A> = = 0 ведут себя иначе для строк со значением NULL. Если попытаться получить значение <xref:System.String.Length%2A> свойства в строке null, среда CLR выдаст исключение <xref:System.NullReferenceException?displayProperty=fullName> . При выполнении сравнения между пустой строкой и пустой строкой среда CLR не создает исключение. сравнение возвращает `false` . Тестирование на значение NULL не оказывает существенного влияния на относительную производительность этих двух подходов. При нацеливании [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] Используйте <xref:System.String.IsNullOrEmpty%2A> метод. В противном случае используйте <xref:System.String.Length%2A> Сравнение = = везде, где это возможно.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, измените сравнение, чтобы использовать <xref:System.String.Length%2A> свойство и проверить пустую строку. При нацеливании [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] Используйте <xref:System.String.IsNullOrEmpty%2A> метод.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 В этом правиле можно отключить вывод предупреждений, если производительность не является проблемой.

## <a name="example"></a>Пример
 В следующем примере показаны различные методы, используемые для поиска пустой строки.

 [!code-csharp[FxCop.Performance.StringTest#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.StringTest/cs/FxCop.Performance.StringTest.cs#1)]
