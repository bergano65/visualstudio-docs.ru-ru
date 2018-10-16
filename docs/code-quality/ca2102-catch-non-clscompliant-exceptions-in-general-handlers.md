---
title: 'CA2102: перехватывайте исключения, не являющиеся CLSCompliant, с помощью общих обработчиков'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2102
- CatchNonClsCompliantExceptionsInGeneralHandlers
helpviewer_keywords:
- CA2102
ms.assetid: bf2df68f-d386-4379-ad9e-930a2c2e930d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4f424ec6585119619cc7fa64efe5d436779b8a65
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547458"
---
# <a name="ca2102-catch-non-clscompliant-exceptions-in-general-handlers"></a>CA2102: перехватывайте исключения, не являющиеся CLSCompliant, с помощью общих обработчиков

|||
|-|-|
|TypeName|CatchNonClsCompliantExceptionsInGeneralHandlers|
|CheckId|CA2102|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Член в сборке, которая не помечен атрибутом <xref:System.Runtime.CompilerServices.RuntimeCompatibilityAttribute> или помечен `RuntimeCompatibility(WrapNonExceptionThrows = false)` содержит блок catch, обрабатывающий <xref:System.Exception?displayProperty=fullName> и не содержит сразу после общий блок catch. Это правило не учитывает [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] сборок.

## <a name="rule-description"></a>Описание правила
 Блок catch, обрабатывающий <xref:System.Exception> перехватывает все исключения с общеязыковой спецификацией (CLS). Тем не менее она не перехватывает несовместимые с CLS исключения. Несовместимое с CLS исключения могут создаваться из машинного кода или из управляемого кода, который был создан корпорацией Майкрософт промежуточного языка MSIL Assembler. Обратите внимание, что C# и [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] компиляторов не разрешает несовместимые с CLS исключения исключение и [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] не перехватывает несовместимые с CLS исключения. Если предполагается блока catch обрабатывать все исключения, используйте следующий синтаксис блока общего перехвата.

- В C#: `catch {}`

- C++: `catch(...) {}` или `catch(Object^) {}`

 Необработанное несовместимые с CLS исключения, несовместимые с проблемой безопасности при удалении ранее предоставленные разрешения в блоке catch. Так как несовместимые с CLS исключения не перехватываются, с повышенным уровнем разрешений может запустить вредоносный метод, который создает несовместимые с CLS исключение.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, когда цель состоит в том, чтобы перехватывать все исключения, заменить или добавить общий блок catch или пометить сборку `RuntimeCompatibility(WrapNonExceptionThrows = true)`. Если в блоке catch удаляются разрешения, повторяющиеся функциональные возможности в целом блок catch. Если это не должны обрабатывать все исключения, замените блок catch, который обрабатывает <xref:System.Exception> с блоки catch, которые обрабатывают исключения определенных типов.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение из этого правила, если в блок try не содержит операторов, которые могут создавать несовместимые с CLS исключение. Так как любой машинный или управляемый код может вызвать несовместимые с CLS исключение, это требует знания весь код, который может выполняться во всех путях кода внутри блока try. Обратите внимание, что несовместимые с CLS исключения не вызываются средой CLR.

## <a name="example-1"></a>Пример 1
 Следующий пример показывает класс MSIL, который создает исключение совместимые с CLS.

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

## <a name="example-2"></a>Пример 2
 Пример метода, содержащего общий блок catch, соответствующий правилу.

 [!code-csharp[FxCop.Security.CatchNonClsCompliantException#1](../code-quality/codesnippet/CSharp/ca2102-catch-non-clscompliant-exceptions-in-general-handlers_1.cs)]

 Скомпилируйте предыдущих примерах следующим образом.

```
ilasm /dll ThrowNonClsCompliantException.il
csc /r:ThrowNonClsCompliantException.dll CatchNonClsCompliantException.cs
```

## <a name="related-rules"></a>Связанные правила
 [CA1031: не перехватывайте типы общих исключений](../code-quality/ca1031-do-not-catch-general-exception-types.md)

## <a name="see-also"></a>См. также

- [Исключения и обработка исключений](/dotnet/csharp/programming-guide/exceptions/exceptions-and-exception-handling)
- [Ilasm.exe (ассемблер IL)](/dotnet/framework/tools/ilasm-exe-il-assembler)
- [Независимость от языка и независимые от языка компоненты](/dotnet/standard/language-independence-and-language-independent-components)