---
title: CA2230. Используйте параметры для аргументов переменной
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 505aa8cdc1371a3bc288772d77b49eb7a50e9830
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920144"
---
# <a name="ca2230-use-params-for-variable-arguments"></a>CA2230. Используйте параметры для аргументов переменной

|||
|-|-|
|TypeName|UseParamsForVariableArguments|
|CheckId|CA2230|
|Категория|Microsoft. Usage|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
Открытый или защищенный тип содержит открытый или защищенный метод, использующий `VarArgs` соглашение о вызовах.

## <a name="rule-description"></a>Описание правила
Соглашение `VarArgs` о вызовах используется с определенными определениями методов, принимающими переменное число параметров. Метод, использующий `VarArgs` соглашение о вызовах, не совместим со спецификацией CLS и может быть недоступен для разных языков программирования.

В C#используется соглашение `VarArgs` о вызовах, когда `__arglist` список параметров метода заканчивается ключевым словом. Visual Basic не поддерживает соглашение о `VarArgs` вызовах, а визуальный C++ элемент позволяет использовать его только в неуправляемом коде, который `...` использует нотацию эллипса.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила в C#, используйте `__arglist`ключевое слово [params](/dotnet/csharp/language-reference/keywords/params) вместо.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
В следующем примере показаны два метода: один, нарушающий правило, и другой, удовлетворяющий правилу.

[!code-csharp[FxCop.Usage.UseParams#1](../code-quality/codesnippet/CSharp/ca2230-use-params-for-variable-arguments_1.cs)]

## <a name="see-also"></a>См. также

- <xref:System.Reflection.CallingConventions?displayProperty=fullName>
- [Независимость от языка и независимые от языка компоненты](/dotnet/standard/language-independence-and-language-independent-components)