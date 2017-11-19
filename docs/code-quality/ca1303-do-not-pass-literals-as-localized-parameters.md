---
title: "CA1303: Не следует передавать литералы в локализованных параметров | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Do not pass literals as localized parameters
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
helpviewer_keywords:
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
ms.assetid: 904d284e-76d0-4b8f-a4df-0094de8d7aac
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ce6ed64a6991342b4dc1506b8384f7691cc90b8f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca1303-do-not-pass-literals-as-localized-parameters"></a>CA1303: не следует передавать литералы в виде локализованных параметров
|||  
|-|-|  
|TypeName|DoNotPassLiteralsAsLocalizedParameters|  
|CheckId|CA1303|  
|Категория|Microsoft.Globalization|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Метод передает строковый литерал в виде параметра конструктору или методу в [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] классов библиотеки, и эта строка должна быть локализуемой.  
  
 Это предупреждение выдается, если строковый литерал передается как значение параметра или свойства, а также один или несколько из следующих условий верно:  
  
-   <xref:System.ComponentModel.LocalizableAttribute> Атрибута параметра или свойства задано значение true.  
  
-   Имя параметра или свойства содержит «Текст», «Сообщение» или «Заголовок».  
  
-   Строковый параметр, который передается методу Console.Write или Console.WriteLine называется «value» или «format».  
  
## <a name="rule-description"></a>Описание правила  
 Строковые литералы, внедренные в исходный код, сложно локализировать.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, замените строковый литерал строки, полученные через экземпляр <xref:System.Resources.ResourceManager> класса.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Это безопасно подавить предупреждение из этого правила, если библиотека кода не будет локализовано, или если строка не показывается конечным пользователем или разработчиком, с использованием кода библиотеки.  
  
 Пользователи могут избавиться от методов, которые не должны передаваться локализованные строки, переименовав параметр или свойство с именем, либо пометив эти элементы как условные помех.  
  
## <a name="example"></a>Пример  
 В следующем примере метод, который создает исключение, если любой из двух аргументов выходят за пределы диапазона. Для первого аргумента конструктору исключения передается строковый литерал, нарушающий это правило. Второй аргумент, конструктор правильно передается строка, извлекаемые с помощью <xref:System.Resources.ResourceManager>.  
  
 [!code-cpp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CPP/ca1303-do-not-pass-literals-as-localized-parameters_1.cpp)]
 [!code-vb[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/VisualBasic/ca1303-do-not-pass-literals-as-localized-parameters_1.vb)]
 [!code-csharp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CSharp/ca1303-do-not-pass-literals-as-localized-parameters_1.cs)]  
  
## <a name="see-also"></a>См. также  
 [Ресурсы в приложениях для настольных систем](/dotnet/framework/resources/index)