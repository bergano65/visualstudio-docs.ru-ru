---
title: 'CA2230: используйте параметры для аргументов переменной'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseParamsForVariableArguments
- CA2230
helpviewer_keywords:
- CA2230
- UseParamsForVariableArguments
ms.assetid: bf98b733-4855-4110-9f16-eba5a9e79421
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 70492152e75d3d257b63e014e854c4b0b431d2ec
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31917722"
---
# <a name="ca2230-use-params-for-variable-arguments"></a>CA2230: используйте параметры для аргументов переменной
|||
|-|-|
|TypeName|UseParamsForVariableArguments|
|CheckId|CA2230|
|Категория|Microsoft.Usage|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный тип содержит открытый или защищенный метод, который использует `VarArgs` соглашение о вызовах.

## <a name="rule-description"></a>Описание правила
 `VarArgs` Соглашение о вызовах используется для некоторых определений методов, принимающих переменное число параметров. Метод с помощью `VarArgs` соглашение о вызовах не общеязыковой спецификацией (CLS) соответствует и нескольких языках программирования могут оказаться недоступными.

 В C# `VarArgs` соглашение о вызовах используется, когда список параметров метода заканчивается `__arglist` ключевое слово. Visual Basic не поддерживает `VarArgs` соглашение о вызовах и Visual C++ позволяет использовать его только в неуправляемый код, который использует эллипса `...` нотации.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила в C#, используйте [params](/dotnet/csharp/language-reference/keywords/params) ключевое слово, а не `__arglist`.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показано два метода, который нарушает правило и, соответствующий этому правилу.

 [!code-csharp[FxCop.Usage.UseParams#1](../code-quality/codesnippet/CSharp/ca2230-use-params-for-variable-arguments_1.cs)]

## <a name="see-also"></a>См. также
 <xref:System.Reflection.CallingConventions?displayProperty=fullName> [Независимость от языка и независимые от языка компоненты](/dotnet/standard/language-independence-and-language-independent-components)