---
title: "CA2102: перехватывайте исключения, не являющиеся CLSCompliant, с помощью общих обработчиков | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2102"
  - "CatchNonClsCompliantExceptionsInGeneralHandlers"
helpviewer_keywords: 
  - "CA2102"
ms.assetid: bf2df68f-d386-4379-ad9e-930a2c2e930d
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2102: перехватывайте исключения, не являющиеся CLSCompliant, с помощью общих обработчиков
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CatchNonClsCompliantExceptionsInGeneralHandlers|  
|CheckId|CA2102|  
|Категория|Microsoft.Security|  
|Критическое изменение|Не критическое|  
  
## Причина  
 Член в сборке, не помеченной атрибутом <xref:System.Runtime.CompilerServices.RuntimeCompatibilityAttribute> или помеченной атрибутом `RuntimeCompatibility(WrapNonExceptionThrows = false)`, содержит блок catch, который обрабатывает исключения <xref:System.Exception?displayProperty=fullName>, однако непосредственно за этим блоком не следует общий блок catch.  Данное правило пропускает сборки [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].  
  
## Описание правила  
 Блок catch, обрабатывающий исключения <xref:System.Exception>, перехватывает все исключения, совместимые со спецификацией CLS.  Однако, он не перехватывает исключения, не совместимые с CLS.  CLS\-несовместимые исключения могут вызываться в машинном коде или в управляемом коде, создаваемом ассемблером MSIL.  Обратите внимание, что в языках C\# и [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] запрещается создавать CLS\-несовместимые исключения, а в языке [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] такие исключения не перехватываются.  Если блок catch предназначен для обработки всех исключений, используйте следующий синтаксис общего блока catch.  
  
-   В C\#: `catch {}`  
  
-   C\+\+: `catch(...) {}` или `catch(Object^) {}`  
  
 Необработанные исключения, несовместимые с CLS, создают угрозу безопасности, если в блоке catch удаляются ранее предоставленные разрешения.  Поскольку CLS\-несовместимые исключения не перехватываются, злоумышленный метод, создавший такое исключение, может получить возможность выполнения с повышенными привилегиями.  
  
## Устранение нарушений  
 Если предполагается перехватывать все исключения, то для устранения нарушения данного правила необходимо добавить общий блок catch или заменить им существующий блок. Можно также пометить сборку атрибутом `RuntimeCompatibility(WrapNonExceptionThrows = true)`.  Если в блоке catch удаляются разрешения, повторно реализуйте эту функциональную возможность в общем блоке catch.  Если не планируется перехватывать все исключения, замените блок catch, который обрабатывает исключения <xref:System.Exception>, блоками catch, обрабатывающими отдельные типы исключений.  
  
## Отключение предупреждений  
 Отключение предупреждений о нарушении данного правила безопасно в том случае, если блок try не содержит операторов, которые могут создавать исключения, несовместимые со спецификацией CLS.  Поскольку CLS\-несовместимые исключения могут вызываться в любом машинном или управляемом коде, необходимо тщательно изучить весь код, выполняемый в каждой из ветвей блока try.  Обратите внимание, что CLS\-несовместимые исключения не вызываются средой CLR.  
  
## Пример  
 В следующем примере показан класс MSIL, который вызывает исключение, несовместимое со спецификацией CLS.  
  
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
  
## Пример  
 В следующем примере показан метод, содержащий общий блок catch, который удовлетворяет данному правилу.  
  
 [!code-cs[FxCop.Security.CatchNonClsCompliantException#1](../code-quality/codesnippet/CSharp/ca2102-catch-non-clscompliant-exceptions-in-general-handlers_1.cs)]  
  
 Выполните компиляцию предыдущих примеров следующим образом.  
  
```  
ilasm /dll ThrowNonClsCompliantException.il  
csc /r:ThrowNonClsCompliantException.dll CatchNonClsCompliantException.cs  
```  
  
## Связанные правила  
 [CA1031: не перехватывайте типы общих исключений](../Topic/CA1031:%20Do%20not%20catch%20general%20exception%20types.md)  
  
## См. также  
 [Исключения и обработка исключений](/dotnet/csharp/programming-guide/exceptions/exceptions-and-exception-handling)   
 [Ilasm.exe \(IL Assembler\)](../Topic/Ilasm.exe%20\(IL%20Assembler\).md)   
 [Overriding Security Checks](http://msdn.microsoft.com/ru-ru/4acdeff5-fc05-41bf-8505-7387cdbfca28)   
 [Независимость от языка и независимые от языка компоненты](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)