---
title: "CA2221: методы завершения должны быть защищены | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2221"
  - "FinalizersShouldBeProtected"
helpviewer_keywords: 
  - "CA2221"
  - "FinalizersShouldBeProtected"
ms.assetid: bda03aee-4cce-45d3-907d-17f4ee030acc
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2221: методы завершения должны быть защищены
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|FinalizersShouldBeProtected|  
|CheckId|CA2221|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Не критическое|  
  
## Причина  
 Открытый тип реализует метод завершения, для которого не указан доступ из семейства \(модификатор protected\).  
  
## Описание правила  
 В методах завершения должен использоваться модификатор доступа из семейства.  Данное правило принудительно применяется компиляторами языков C\#, Visual Basic и Visual C\+\+.  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, сделайте метод завершения доступным из семейства.  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## Пример  
 Данное правило не может быть нарушено в языках .NET верхнего уровня; нарушения возникают при написании кода на языке MSIL.  
  
```  
// =============== CLASS MEMBERS DECLARATION ===================  
//   note that class flags, 'extends' and 'implements' clauses  
//          are provided here for information only  
  
.namespace UsageLibrary  
{  
  .class public auto ansi beforefieldinit FinalizeMethodNotProtected  
         extends [mscorlib]System.Object  
  {  
    .method public hidebysig instance void  
            Finalize() cil managed  
    {  
  
      // Code size       1 (0x1)  
      .maxstack  0  
      IL_0000:  ret  
    } // end of method FinalizeMethodNotProtected::Finalize  
  
    .method public hidebysig specialname rtspecialname  
            instance void  .ctor() cil managed  
    {  
      // Code size       7 (0x7)  
      .maxstack  1  
      IL_0000:  ldarg.0  
      IL_0001:  call       instance void [mscorlib]System.Object::.ctor()  
      IL_0006:  ret  
    } // end of method FinalizeMethodNotProtected::.ctor  
  
  } // end of class FinalizeMethodNotProtected  
} // end of namespace  
```  
  
## См. также  
 [Шаблон удаления](../Topic/Dispose%20Pattern.md)