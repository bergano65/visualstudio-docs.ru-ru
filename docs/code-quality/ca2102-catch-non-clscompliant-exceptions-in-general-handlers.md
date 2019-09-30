---
title: CA2102. Перехватывайте исключения, не являющиеся CLSCompliant, с помощью общих обработчиков
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2102
- CatchNonClsCompliantExceptionsInGeneralHandlers
helpviewer_keywords:
- CA2102
ms.assetid: bf2df68f-d386-4379-ad9e-930a2c2e930d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f62ad97bbb96f49a7263edd29f0f8a7c263bec4c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233013"
---
# <a name="ca2102-catch-non-clscompliant-exceptions-in-general-handlers"></a>CA2102. Перехватывайте исключения, не являющиеся CLSCompliant, с помощью общих обработчиков

|||
|-|-|
|TypeName|катчнонклскомплиантексцептионсинженералхандлерс|
|CheckId|CA2102|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина:

Член в сборке, не помеченной <xref:System.Runtime.CompilerServices.RuntimeCompatibilityAttribute> как или, помечен как `RuntimeCompatibility(WrapNonExceptionThrows = false)` , содержит блок catch, который обрабатывает <xref:System.Exception?displayProperty=fullName> и не содержит сразу следующий общий блок catch. Это правило игнорирует [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] сборки.

## <a name="rule-description"></a>Описание правила

Блок catch, обрабатывающий <xref:System.Exception> перехват всех исключений, совместимых со спецификацией CLS. Однако он не перехватывает несовместимые с CLS исключения. Исключения, несовместимые с CLS, могут быть вызваны из машинного кода или из управляемого кода, созданного ассемблером MSIL. Обратите внимание C# , [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] что компиляторы и не допускают возникновения исключений, несовместимых с [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] CLS, и не перехватывают несовместимые с CLS исключения. Если цель блока catch заключается в обработке всех исключений, используйте следующий общий синтаксис блока catch.

- В C#: `catch {}`

- C++: `catch(...) {}` или`catch(Object^) {}`

Необработанное исключение, несовместимое с CLS, стало проблемой безопасности, когда ранее разрешенные разрешения удаляются из блока catch. Так как несовместимые с CLS исключения не перехватываются, вредоносный метод, порождающий несовместимое с CLS исключение, может работать с повышенными разрешениями.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, когда цель заключается в перехвате всех исключений, замените или добавьте общий блок catch или пометьте сборку `RuntimeCompatibility(WrapNonExceptionThrows = true)`. Если разрешения удаляются в блоке catch, они дублируют функциональность в общем блоке catch. Если не нужно обрабатывать все исключения, замените блок catch, обрабатывающий <xref:System.Exception> блоки catch, обрабатывающие определенные типы исключений.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Предупреждение из этого правила можно отключить, если блок try не содержит инструкций, которые могут привести к исключению, не совместимому с CLS. Поскольку любой машинный или управляемый код может вызывать исключение, несовместимое с CLS, для этого требуется знание всего кода, который может быть выполнен во всех путях кода внутри блока try. Обратите внимание, что несовместимые с CLS исключения не вызываются средой CLR.

## <a name="example-1"></a>Пример 1

В следующем примере показан класс MSIL, который вызывает исключение, не совместимое с CLS.

```cpp
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

## <a name="example-2"></a>Пример 2

В следующем примере показан метод, содержащий общий блок catch, который удовлетворяет правилу.

[!code-csharp[FxCop.Security.CatchNonClsCompliantException#1](../code-quality/codesnippet/CSharp/ca2102-catch-non-clscompliant-exceptions-in-general-handlers_1.cs)]

Скомпилируйте предыдущие примеры следующим образом.

```cpp
ilasm /dll ThrowNonClsCompliantException.il
csc /r:ThrowNonClsCompliantException.dll CatchNonClsCompliantException.cs
```

## <a name="related-rules"></a>Связанные правила

[CA1031 Не перехватывайте типы общих исключений](../code-quality/ca1031-do-not-catch-general-exception-types.md)

## <a name="see-also"></a>См. также

- [Исключения и обработка исключений](/dotnet/csharp/programming-guide/exceptions/exceptions-and-exception-handling)
- [Ilasm.exe (ассемблер IL)](/dotnet/framework/tools/ilasm-exe-il-assembler)
- [Независимость от языка и независимые от языка компоненты](/dotnet/standard/language-independence-and-language-independent-components)