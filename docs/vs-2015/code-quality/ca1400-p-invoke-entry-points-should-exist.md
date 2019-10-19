---
title: 'CA1400: должны существовать точки входа P-Invoke | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1400
- PInvokeEntryPointsShouldExist
helpviewer_keywords:
- PInvokeEntryPointsShouldExist
- CA1400
ms.assetid: 1d64e470-7b2f-4cca-8fb0-ac92829e6332
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d1083f7bbdf3b3af78b83aed293b31d898ae7522
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661378"
---
# <a name="ca1400-pinvoke-entry-points-should-exist"></a>CA1400: необходимо наличие точек входа P/Invoke
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PInvokeEntryPointsShouldExist|
|CheckId|CA1400|
|Категория|Microsoft. взаимодействие|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный метод помечается <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. Не удается найти неуправляемую библиотеку либо не удается сопоставить метод функции в библиотеке. Если правило не может найти имя метода точно так же, как указано, оно ищет версии метода в кодировке ANSI или расширенных символов, заменяя имя метода на "A" или "W". Если совпадений не найдено, правило пытается найти функцию с помощью формата имени __stdcall (_MyMethod@12, где 12 обозначает длину аргументов). Если совпадений не найдено, а имя метода начинается с символа "#", правило ищет функцию как порядковую ссылку, а не ссылку на имя.

## <a name="rule-description"></a>Описание правила
 Проверка на время компиляции недоступна, чтобы методы, помеченные <xref:System.Runtime.InteropServices.DllImportAttribute>, размещались в неуправляемой библиотеке DLL, на которую указывает ссылка. Если в библиотеке нет функции с указанным именем или аргументы метода не совпадают с аргументами функции, среда CLR выдает исключение.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, исправьте метод с атрибутом <xref:System.Runtime.InteropServices.DllImportAttribute>. Убедитесь, что неуправляемая библиотека существует и находится в том же каталоге, что и сборка, содержащая метод. Если библиотека существует и правильно указана, убедитесь, что имя метода, возвращаемый тип и сигнатура аргумента соответствуют библиотечной функции.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не отключайте предупреждение из этого правила, если неуправляемая библиотека находится в том же каталоге, что и управляемая сборка, которая ссылается на нее. Можно спокойно отключить предупреждение из этого правила в случае, если не удается найти неуправляемую библиотеку.

## <a name="example"></a>Пример
 В следующем примере показан тип, нарушающий правило. В kernel32. dll не выполняется ни одна функция с именем `DoSomethingUnmanaged`.

 [!code-csharp[FxCop.Interoperability.DLLExists#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DLLExists/cs/FxCop.Interoperability.DLLExists.cs#1)]

## <a name="see-also"></a>См. также раздел
 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>
