---
title: CA1303. Не передавайте литералы в качестве локализованных параметров
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- Do not pass literals as localized parameters
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
helpviewer_keywords:
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
ms.assetid: 904d284e-76d0-4b8f-a4df-0094de8d7aac
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: cc32db1aea9c5514a7548bc889b65463de3de3d5
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66714696"
---
# <a name="ca1303-do-not-pass-literals-as-localized-parameters"></a>CA1303. Не передавайте литералы в качестве локализованных параметров

|||
|-|-|
|TypeName|DoNotPassLiteralsAsLocalizedParameters|
|CheckId|CA1303|
|Категория|Microsoft.Globalization|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Метод передает строковый литерал в качестве параметра .NET конструктору или методу, и эта строка должна быть локализуемой.

Это предупреждение возникает в том случае, если строковый литерал передается как значение параметра или свойства, а также один или несколько из следующих условий верно:

- <xref:System.ComponentModel.LocalizableAttribute> Установлен атрибут параметра или свойства в значение true.

- Имя параметра или свойства содержит «Text», «Message» или «Заголовок».

- Строковый параметр, который передается методу Console.Write и Console.WriteLine называется «value» или «format».

## <a name="rule-description"></a>Описание правила

Строковые литералы, внедренные в исходный код, сложно локализировать.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, замените строковый литерал строки, полученной через экземпляр <xref:System.Resources.ResourceManager> класса.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Его можно безопасно подавить предупреждение из этого правила, если библиотека кода не будет локализовано или если строка не предоставляется конечному пользователю или разработчик, использующий библиотеку кода.

Пользователи могут избавиться от методов, которые не должны передаваться локализованные строки, переименовав параметра или свойства, или помечая эти элементы как условные помех.

## <a name="example"></a>Пример

В следующем примере метод, который создает исключение, если любой из двух аргументов выходят за пределы диапазона. Для первого аргумента конструктору исключения передается строковый литерал, который нарушает это правило. Для второго аргумента конструктора правильно передается строка извлечь с помощью <xref:System.Resources.ResourceManager>.

[!code-cpp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CPP/ca1303-do-not-pass-literals-as-localized-parameters_1.cpp)]
[!code-vb[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/VisualBasic/ca1303-do-not-pass-literals-as-localized-parameters_1.vb)]
[!code-csharp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CSharp/ca1303-do-not-pass-literals-as-localized-parameters_1.cs)]

## <a name="see-also"></a>См. также

- [Ресурсы в приложениях для настольных систем](/dotnet/framework/resources/index)