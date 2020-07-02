---
title: 'CA2230: использование параметров для переменных аргументов | Документация Майкрософт'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ce66e04272618b9df2ab1957af305bb9bf40ee9c
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85540365"
---
# <a name="ca2230-use-params-for-variable-arguments"></a>CA2230. Используйте параметры для аргументов переменной
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|UseParamsForVariableArguments|
|CheckId|CA2230|
|Категория|Microsoft. Usage|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный тип содержит открытый или защищенный метод, использующий `VarArgs` соглашение о вызовах.

## <a name="rule-description"></a>Описание правила
 `VarArgs`Соглашение о вызовах используется с определенными определениями методов, принимающими переменное число параметров. Метод, использующий `VarArgs` соглашение о вызовах, не совместим со спецификацией CLS и может быть недоступен для разных языков программирования.

 В C# `VarArgs` соглашение о вызовах используется, когда список параметров метода заканчивается `__arglist` ключевым словом. Visual Basic не поддерживает `VarArgs` соглашение о вызовах, и Visual C++ позволяет использовать его только в неуправляемом коде, который использует `...` нотацию эллипса.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила в C#, используйте ключевое слово [params](https://msdn.microsoft.com/library/1690815e-b52b-4967-8380-5780aff08012) вместо `__arglist` .

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показаны два метода: один, нарушающий правило, и другой, удовлетворяющий правилу.

 [!code-csharp[FxCop.Usage.UseParams#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.UseParams/cs/FxCop.Usage.UseParams.cs#1)]

## <a name="see-also"></a>См. также
 <xref:System.Reflection.CallingConventions?displayProperty=fullName>[Независимость от языка и независимые от языка компоненты](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
