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
ms.openlocfilehash: 15b63e49f89e17db631772c48765cc610f47ed29
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548308"
---
# <a name="ca1400-pinvoke-entry-points-should-exist"></a>CA1400: необходимо наличие точек входа P/Invoke
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|PInvokeEntryPointsShouldExist|
|CheckId|CA1400|
|Категория|Microsoft. взаимодействие|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный метод помечается атрибутом <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> . Не удается найти неуправляемую библиотеку либо не удается сопоставить метод функции в библиотеке. Если правило не может найти имя метода точно так же, как указано, оно ищет версии метода в кодировке ANSI или расширенных символов, заменяя имя метода на "A" или "W". Если совпадений не найдено, правило пытается найти функцию с помощью __stdcall формата имени ( _MyMethod@12 , где 12 обозначает длину аргументов). Если совпадений не найдено, а имя метода начинается с символа "#", правило ищет функцию как порядковую ссылку, а не ссылку на имя.

## <a name="rule-description"></a>Описание правила
 Проверка на время компиляции недоступна, чтобы методы, помеченные, <xref:System.Runtime.InteropServices.DllImportAttribute> были размещены в неуправляемой библиотеке DLL, на которую указывает ссылка. Если в библиотеке нет функции с указанным именем или аргументы метода не совпадают с аргументами функции, среда CLR выдает исключение.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, исправьте метод с <xref:System.Runtime.InteropServices.DllImportAttribute> атрибутом. Убедитесь, что неуправляемая библиотека существует и находится в том же каталоге, что и сборка, содержащая метод. Если библиотека существует и правильно указана, убедитесь, что имя метода, возвращаемый тип и сигнатура аргумента соответствуют библиотечной функции.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не отключайте предупреждение из этого правила, если неуправляемая библиотека находится в том же каталоге, что и управляемая сборка, которая ссылается на нее. Можно спокойно отключить предупреждение из этого правила в случае, если не удается найти неуправляемую библиотеку.

## <a name="example"></a>Пример
 В следующем примере показан тип, нарушающий правило. `DoSomethingUnmanaged`В kernel32.dll не встречается функция с именем.

 [!code-csharp[FxCop.Interoperability.DLLExists#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DLLExists/cs/FxCop.Interoperability.DLLExists.cs#1)]

## <a name="see-also"></a>См. также:
 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>
