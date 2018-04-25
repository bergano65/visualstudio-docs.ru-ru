---
title: 'CA2230: используйте параметры для аргументов переменной'
ms.date: 11/04/2016
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
ms.openlocfilehash: b4496173284eef595097148046f727c844da39f2
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
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