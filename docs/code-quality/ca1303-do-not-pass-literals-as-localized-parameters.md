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
ms.openlocfilehash: 2700dc2ade7ba901f15f67045e3170e2bbb40ff8
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235117"
---
# <a name="ca1303-do-not-pass-literals-as-localized-parameters"></a>CA1303. Не передавайте литералы в качестве локализованных параметров

|||
|-|-|
|TypeName|DoNotPassLiteralsAsLocalizedParameters|
|CheckId|CA1303|
|Категория|Microsoft. Globalization|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина:

Метод передает строковый литерал в качестве параметра в конструктор или метод .NET, и эта строка должна быть локализуемой.

Это предупреждение возникает, когда литеральная строка передается в качестве значения параметру или свойству, и один или несколько из следующих случаев имеют значение true:

- <xref:System.ComponentModel.LocalizableAttribute> Атрибут параметра или свойства имеет значение true.

- Имя параметра или свойства содержит "Text", "Message" или "Caption".

- Имя строкового параметра, передаваемого методу Console. Write или Console. WriteLine — либо value, либо Format.

## <a name="rule-description"></a>Описание правила

Строковые литералы, внедренные в исходный код, трудно локализовать.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, замените строковый литерал строкой, полученной с помощью экземпляра <xref:System.Resources.ResourceManager> класса.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Предупреждение из этого правила можно отключить, если библиотека кода не будет локализована или если строка не доступна конечному пользователю или разработчику, использующему библиотеку кода.

Пользователи могут исключить шум от методов, которые не должны передавать локализованные строки путем переименования параметра или свойства, или помечая эти элементы как условные.

## <a name="example"></a>Пример

В следующем примере показан метод, который создает исключение, если один из его двух аргументов выходит за пределы диапазона. Для первого аргумента конструктору исключений передается литеральная строка, которая нарушает это правило. Для второго аргумента конструктор правильно передает строку, полученную через <xref:System.Resources.ResourceManager>.

[!code-cpp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CPP/ca1303-do-not-pass-literals-as-localized-parameters_1.cpp)]
[!code-vb[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/VisualBasic/ca1303-do-not-pass-literals-as-localized-parameters_1.vb)]
[!code-csharp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CSharp/ca1303-do-not-pass-literals-as-localized-parameters_1.cs)]

## <a name="see-also"></a>См. также

- [Ресурсы в классических приложениях](/dotnet/framework/resources/index)