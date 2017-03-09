---
title: "CA2230: используйте параметры для аргументов переменной | Microsoft Docs"
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
  - "UseParamsForVariableArguments"
  - "CA2230"
helpviewer_keywords: 
  - "CA2230"
  - "UseParamsForVariableArguments"
ms.assetid: bf98b733-4855-4110-9f16-eba5a9e79421
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2230: используйте параметры для аргументов переменной
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseParamsForVariableArguments|  
|CheckId|CA2230|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Открытый или защищенный тип содержит открытый или защищенный метод, в котором используется соглашение о вызовах `VarArgs`.  
  
## Описание правила  
 Соглашение о вызовах `VarArgs` используется для некоторых определений методов, принимающих переменное число параметров.  Метод, в котором используется соглашение о вызовах `VarArgs`, не соответствует спецификации CLS, и такие методы могут быть недоступны в некоторых языках программирования.  
  
 В C\# соглашение о вызовах `VarArgs` используется в том случае, если список параметров метода заканчивается ключевым словом `__arglist`.  В Visual Basic соглашение о вызовах `VarArgs` не поддерживается, а в Visual C\+\+ его можно применять только в неуправляемом коде, использующем нотацию многоточия `...`.  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила в C\#, используйте вместо ключевого слова `__arglist` ключевое слово [params](/dotnet/csharp/language-reference/keywords/params).  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## Пример  
 В следующем примере показаны два метода, один из которых нарушает данное правило, а другой удовлетворяет ему.  
  
 [!code-cs[FxCop.Usage.UseParams#1](../code-quality/codesnippet/CSharp/ca2230-use-params-for-variable-arguments_1.cs)]  
  
## См. также  
 <xref:System.Reflection.CallingConventions?displayProperty=fullName>   
 [Независимость от языка и независимые от языка компоненты](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)