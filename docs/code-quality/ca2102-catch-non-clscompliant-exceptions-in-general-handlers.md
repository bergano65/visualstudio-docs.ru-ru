---
title: 'CA2102: Перехватывайте исключения, не являющиеся CLSCompliant, с помощью общих обработчиков | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
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
ms.openlocfilehash: cff8d36cd80a31cf05ca461730d51703afc106ee
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ca2102-catch-non-clscompliant-exceptions-in-general-handlers"></a>CA2102: перехватывайте исключения, не являющиеся CLSCompliant, с помощью общих обработчиков
|||  
|-|-|  
|TypeName|CatchNonClsCompliantExceptionsInGeneralHandlers|  
|CheckId|CA2102|  
|Категория|Microsoft.Security|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Элемент в сборке, не помеченной атрибутом <xref:System.Runtime.CompilerServices.RuntimeCompatibilityAttribute> либо помечен `RuntimeCompatibility(WrapNonExceptionThrows = false)` содержит блок catch, обрабатывающий <xref:System.Exception?displayProperty=fullName> и не содержит немедленно следующий общий блок catch. Это правило не учитывает [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] сборки.  
  
## <a name="rule-description"></a>Описание правила  
 Блок catch, обрабатывающий <xref:System.Exception> перехватывает все исключения с общеязыковой спецификацией (CLS). Тем не менее не перехватывает исключения несовместимое с CLS. Несовместимое с CLS исключения могут создаваться из машинного кода или из управляемого кода, который был создан корпорацией Майкрософт промежуточного языка MSIL Assembler. Обратите внимание, что в C# и [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] компиляторов не разрешает несовместимое с CLS исключение исключения и [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] не перехватывает исключения несовместимое с CLS. Если цель блока catch должен обрабатывать все исключения, используйте следующий синтаксис общего блока catch.  
  
-   В C#: `catch {}`  
  
-   C++: `catch(...) {}` или `catch(Object^) {}`  
  
 Необработанное несовместимое с CLS исключение становится угрозу безопасности, если в блоке catch удаляются ранее предоставленные разрешения. Так как CLS-совместимые исключения не перехватываются, вредоносных метод, который создает исключение не являющиеся CLS-совместимые может запустить с повышенными разрешениями.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение этого правила, если предполагается перехватывать все исключения, заменить или добавить общий блок catch или пометить сборку `RuntimeCompatibility(WrapNonExceptionThrows = true)`. Если в блоке catch удаляются разрешения, повторяющиеся функциональность в общий блок catch. Если не планируется обрабатывать все исключения, замените блок catch, который обрабатывает <xref:System.Exception> с блоками catch, которые обрабатывают исключения определенных типов.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Это безопасно подавить предупреждение из этого правила, если блок try не содержит операторов, которые могут вызвать несовместимое с CLS исключение. Так как любой машинный или управляемый код может вызывать несовместимое с CLS исключение, необходимо тщательно изучить весь код, который может выполняться во всех путях кода внутри блока try. Обратите внимание, что CLS-совместимые исключения не вызываются средой CLR.  
  
## <a name="example"></a>Пример  
 В следующем примере класс MSIL, который создает исключение, несовместимое с CLS исключение.  
  
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
 В следующем примере показано метод, который содержит общий блок catch, соответствующий правилу.  
  
 [!code-csharp[FxCop.Security.CatchNonClsCompliantException#1](../code-quality/codesnippet/CSharp/ca2102-catch-non-clscompliant-exceptions-in-general-handlers_1.cs)]  
  
 Скомпилируйте приведенных выше примерах следующим образом.  
  
```  
ilasm /dll ThrowNonClsCompliantException.il  
csc /r:ThrowNonClsCompliantException.dll CatchNonClsCompliantException.cs  
```  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1031: не перехватывайте типы общих исключений](../code-quality/ca1031-do-not-catch-general-exception-types.md)  
  
## <a name="see-also"></a>См. также  
 [Исключения и обработка исключений](/dotnet/csharp/programming-guide/exceptions/exceptions-and-exception-handling)   
 [Ilasm.exe (ассемблер IL)](/dotnet/framework/tools/ilasm-exe-il-assembler)   
 [Независимость от языка и независимые от языка компоненты](/dotnet/standard/language-independence-and-language-independent-components)