---
title: ": CA1400 точек входа P-Invoke | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1400
- PInvokeEntryPointsShouldExist
helpviewer_keywords:
- PInvokeEntryPointsShouldExist
- CA1400
ms.assetid: 1d64e470-7b2f-4cca-8fb0-ac92829e6332
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: dd92619a652255f67c1e1558c40ea05840cd0eb5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca1400-pinvoke-entry-points-should-exist"></a>CA1400: необходимо наличие точек входа P/Invoke
|||  
|-|-|  
|TypeName|PInvokeEntryPointsShouldExist|  
|CheckId|CA1400|  
|Категория|Microsoft.Interoperability|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Открытый или защищенный метод, помеченный атрибутом <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. Не удается найти неуправляемую библиотеку либо не удается сопоставить метод функции в библиотеке. Если правило не удается найти имя метода, точно так, как он указан, он ищет ANSI или Юникода версии метода формируемый имя метода с «» или «W». Если совпадение не найдено, правило пытается найти функцию с помощью формата имени __stdcall (_MyMethod@12, где 12 — это длина аргументов). Если совпадение не найдено, и имя метода начинается с «#», выполняется поиск как порядковому номеру, а не ссылки на имя функции.  
  
## <a name="rule-description"></a>Описание правила  
 Проверка во время компиляции не доступен для убедитесь, что методы, помеченные с <xref:System.Runtime.InteropServices.DllImportAttribute> расположены в упоминаемой неуправляемой библиотеки DLL. Если ни одна из функций с указанным именем находится в библиотеке или аргументы метода не соответствуют аргументы функции, общеязыковая среда выполнения создает исключение.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, исправьте метод, который имеет <xref:System.Runtime.InteropServices.DllImportAttribute> атрибута. Убедитесь, что неуправляемая библиотека существует и находится в том же каталоге, что и сборка, содержащая метод. Если библиотека еще существует и правильно указана, убедитесь, что имя метода, возвращаемый тип и подпись аргумента соответствуют функции библиотеки.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Не отключайте предупреждение из этого правила, когда неуправляемая библиотека находится в том же каталоге, управляемая сборка, которая ссылается на него. Можно безопасно подавить предупреждение из этого правила в случае, когда неуправляемая библиотека, не удалось найти.  
  
## <a name="example"></a>Пример  
 В следующем примере показано тип, нарушающий правило. Ни одна из функций, которая называется `DoSomethingUnmanaged` происходит в kernel32.dll.  
  
 [!code-csharp[FxCop.Interoperability.DLLExists#1](../code-quality/codesnippet/CSharp/ca1400-p-invoke-entry-points-should-exist_1.cs)]  
  
## <a name="see-also"></a>См. также  
 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>