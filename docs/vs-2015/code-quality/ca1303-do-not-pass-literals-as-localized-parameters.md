---
title: 'CA1303: не передавайте литералы как локализованные параметры | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- Do not pass literals as localized parameters
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
helpviewer_keywords:
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
ms.assetid: 904d284e-76d0-4b8f-a4df-0094de8d7aac
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ce85a3a933d9453c63ef118d5dfd9e0b17cbf130
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661448"
---
# <a name="ca1303-do-not-pass-literals-as-localized-parameters"></a>CA1303: не следует передавать литералы в виде локализованных параметров
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotPassLiteralsAsLocalizedParameters|
|CheckId|CA1303|
|Категория|Microsoft. Globalization|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Метод передает строковый литерал в качестве параметра конструктору или методу в библиотеке классов [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], и эта строка должна быть локализуемой.

 Это предупреждение возникает, когда литеральная строка передается в качестве значения параметру или свойству, и один или несколько из следующих случаев имеют значение true:

- Атрибут <xref:System.ComponentModel.LocalizableAttribute> параметра или свойства имеет значение true.

- Имя параметра или свойства содержит "Text", "Message" или "Caption".

- Имя строкового параметра, передаваемого методу Console. Write или Console. WriteLine — либо value, либо Format.

## <a name="rule-description"></a>Описание правила
 Строковые литералы, внедренные в исходный код, трудно локализовать.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, замените строковый литерал строкой, полученной с помощью экземпляра класса <xref:System.Resources.ResourceManager>.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Предупреждение из этого правила можно отключить, если библиотека кода не будет локализована или если строка недоступна конечному пользователю или разработчику, использующему библиотеку кода.

 Пользователи могут исключить шум для методов, которые не должны передавать локализованные строки путем переименования параметра или свойства либо помечая эти элементы как условные.

## <a name="example"></a>Пример
 В следующем примере показан метод, который создает исключение, если один из его двух аргументов выходит за пределы диапазона. Для первого аргумента конструктору исключений передается литеральная строка, которая нарушает это правило. Для второго аргумента конструктор правильно передает строку, полученную с помощью <xref:System.Resources.ResourceManager>.

 [!code-cpp[FxCop.Globalization.DoNotPassLiterals#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/cpp/FxCop.Globalization.DoNotPassLiterals.cpp#1)]
 [!code-csharp[FxCop.Globalization.DoNotPassLiterals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/cs/FxCop.Globalization.DoNotPassLiterals.cs#1)]
 [!code-vb[FxCop.Globalization.DoNotPassLiterals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/vb/FxCop.Globalization.DoNotPassLiterals.vb#1)]

## <a name="see-also"></a>См. также раздел
 [Ресурсы в приложениях для настольных систем](https://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)
