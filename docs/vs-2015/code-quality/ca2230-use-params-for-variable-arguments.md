---
title: CA2230. Используйте параметры для аргументов переменной | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseParamsForVariableArguments
- CA2230
helpviewer_keywords:
- CA2230
- UseParamsForVariableArguments
ms.assetid: bf98b733-4855-4110-9f16-eba5a9e79421
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8b833f520c574c32f90ff1ec5e20a9671184b78a
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65685101"
---
# <a name="ca2230-use-params-for-variable-arguments"></a>CA2230. Используйте параметры для аргументов переменной
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseParamsForVariableArguments|
|CheckId|CA2230|
|Категория|Microsoft.Usage|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный тип содержит открытый или защищенный метод, который использует `VarArgs` соглашение о вызовах.

## <a name="rule-description"></a>Описание правила
 `VarArgs` Соглашения о вызове используется для некоторых определений методов, принимающих переменное количество параметров. Метод с помощью `VarArgs` соглашение о вызовах не общеязыковой спецификацией (CLS) соответствует и нескольких языках программирования могут оказаться недоступными.

 В C# `VarArgs` соглашение о вызовах используется, когда список параметров метода заканчивается `__arglist` ключевое слово. Visual Basic не поддерживает `VarArgs` соглашение о вызовах и Visual C++ позволяет его использовать только в неуправляемом коде, который использует эллипс `...` нотации.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила на языке C#, используйте [params](https://msdn.microsoft.com/library/1690815e-b52b-4967-8380-5780aff08012) ключевое слово `__arglist`.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показано два метода, который нарушает правило, а другой соблюдается правило.

 [!code-csharp[FxCop.Usage.UseParams#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.UseParams/cs/FxCop.Usage.UseParams.cs#1)]

## <a name="see-also"></a>См. также
 <xref:System.Reflection.CallingConventions?displayProperty=fullName> [Независимость от языка и независимые от языка компоненты](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
