---
title: 'CA2102: перехват исключений, не являющихся CLSCompliant, в общих обработчиках | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2102
- CatchNonClsCompliantExceptionsInGeneralHandlers
helpviewer_keywords:
- CA2102
ms.assetid: bf2df68f-d386-4379-ad9e-930a2c2e930d
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 051b59183a761477476269480ecdf83ccbf0cb37
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652174"
---
# <a name="ca2102-catch-non-clscompliant-exceptions-in-general-handlers"></a>CA2102: перехватывайте исключения, не являющиеся CLSCompliant, с помощью общих обработчиков
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|катчнонклскомплиантексцептионсинженералхандлерс|
|CheckId|CA2102|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Член в сборке, не помеченной <xref:System.Runtime.CompilerServices.RuntimeCompatibilityAttribute> или помеченный `RuntimeCompatibility(WrapNonExceptionThrows = false)` содержит блок catch, который обрабатывает <xref:System.Exception?displayProperty=fullName> и не содержит сразу следующий общий блок catch. Это правило игнорирует [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] сборки.

## <a name="rule-description"></a>Описание правила
 Блок catch, обрабатывающий <xref:System.Exception>, перехватывает все исключения, совместимые со спецификацией CLS. Однако он не перехватывает несовместимые с CLS исключения. Исключения, несовместимые с CLS, могут быть вызваны из машинного кода или из управляемого кода, созданного ассемблером MSIL. Обратите внимание C# , что компиляторы и [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] не допускают возникновения исключений, несовместимых с CLS, и [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] не перехватывает исключения, несовместимые с CLS. Если цель блока catch заключается в обработке всех исключений, используйте следующий общий синтаксис блока catch.

- В C#: `catch {}`

- C++: `catch(...) {}` или `catch(Object^) {}`

  Необработанное исключение, несовместимое с CLS, стало проблемой безопасности, когда ранее разрешенные разрешения удаляются из блока catch. Так как несовместимые с CLS исключения не перехватываются, вредоносный метод, порождающий несовместимое с CLS исключение, может работать с повышенными разрешениями.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, когда цель заключается в перехвате всех исключений, замените или добавьте общий блок catch или пометьте сборку `RuntimeCompatibility(WrapNonExceptionThrows = true)`. Если разрешения удаляются в блоке catch, они дублируют функциональность в общем блоке catch. Если не нужно обрабатывать все исключения, замените блок catch, обрабатывающий <xref:System.Exception>, блоками catch, обрабатывающими определенные типы исключений.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Предупреждение из этого правила можно отключить, если блок try не содержит инструкций, которые могут привести к исключению, не совместимому с CLS. Поскольку любой машинный или управляемый код может вызывать исключение, несовместимое с CLS, для этого требуется знание всего кода, который может быть выполнен во всех путях кода внутри блока try. Обратите внимание, что несовместимые с CLS исключения не вызываются средой CLR.

## <a name="example"></a>Пример
 В следующем примере показан класс MSIL, который вызывает исключение, не совместимое с CLS.

```
.assembly ThrowNonClsCompliantException {}
.class public auto ansi beforefieldinit ThrowsExceptions
{
   .method public hidebysig static void
         ThrowNonClsException() cil managed
   {
      .maxstack  1
      IL_0000:  newobj     instance void [mscorlib]System.Object::.ctor()
      IL_0005:  throw
   }
}
```

## <a name="example"></a>Пример
 В следующем примере показан метод, содержащий общий блок catch, который удовлетворяет правилу.

 [!code-csharp[FxCop.Security.CatchNonClsCompliantException#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.CatchNonClsCompliantException/cs/FxCop.Security.CatchNonClsCompliantException.cs#1)]

 Скомпилируйте предыдущие примеры следующим образом.

```
ilasm /dll ThrowNonClsCompliantException.il
csc /r:ThrowNonClsCompliantException.dll CatchNonClsCompliantException.cs
```

## <a name="related-rules"></a>Связанные правила
 [CA1031: не перехватывайте типы общих исключений](../code-quality/ca1031-do-not-catch-general-exception-types.md)

## <a name="see-also"></a>См. также раздел
 [Исключения и обработка исключений](https://msdn.microsoft.com/library/0001887f-4fa2-47e2-8034-2819477e2344) [Ilasm. exe (ассемблер IL)](https://msdn.microsoft.com/library/4ca3a4f0-4400-47ce-8936-8e219961c76f) [Переопределение безопасности проверяет](https://msdn.microsoft.com/4acdeff5-fc05-41bf-8505-7387cdbfca28) [независимость от языка и независимые от языка компоненты](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
