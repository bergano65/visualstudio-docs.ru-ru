---
title: "CA2202: не удаляйте объекты несколько раз | Microsoft Docs"
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
  - "CA2202"
  - "Do not dispose objects multiple times"
  - "DoNotDisposeObjectsMultipleTimes"
helpviewer_keywords: 
  - "CA2202"
ms.assetid: fa85349a-cf1e-42c8-a86b-eacae1f8bd96
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2202: не удаляйте объекты несколько раз
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotDisposeObjectsMultipleTimes|  
|CheckId|CA2202|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Не критическое|  
  
## Причина  
 Реализация метода содержит пути кода, которые могли стать причиной многократного вызова метода <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> или эквивалентного метода Dispose \(например, метода Close\(\) для некоторых типов\) для одного и того же объекта.  
  
## Описание правила  
 Правильно реализованный метод <xref:System.IDisposable.Dispose%2A> можно вызывать несколько раз, и при этом не создается исключение.  Однако это нельзя гарантировать, и чтобы не допустить создания исключения <xref:System.ObjectDisposedException?displayProperty=fullName>, не следует вызывать метод <xref:System.IDisposable.Dispose%2A> для какого\-либо объекта более одного раза.  
  
## Связанные правила  
 [CA2000: удалите объекты до того, как будет потеряна область действия](../code-quality/ca2000-dispose-objects-before-losing-scope.md)  
  
## Устранение нарушений  
 Чтобы исправить нарушение этого правила, измените реализацию так, чтобы независимо от пути кода метод <xref:System.IDisposable.Dispose%2A> вызывался для объекта только один раз.  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  Если известно, что можно безопасно вызывать метод <xref:System.IDisposable.Dispose%2A> для данного объекта несколько раз, его реализация может измениться в будущем.  
  
## Пример  
 Вложенные инструкции `using` \(`Using` в Visual Basic\) могут привести к нарушениям предупреждений CA2202.  Если ресурс IDisposable вложенного внутреннего оператора `using` содержит ресурс другого оператора `using`, метод `Dispose` вложенного ресурса освобождает содержащийся в нем ресурс.  При возникновении такой ситуации метод `Dispose` внешнего оператора `using` пытается во второй раз ликвидировать свой ресурс.  
  
 В следующем примере объект <xref:System.IO.Stream> , который создается во внешнем операторе using, освобождается в конце внутреннего оператора using в методе Dispose объекта <xref:System.IO.StreamWriter>, который содержит объект `stream`.  В конце внешней инструкции `using` объект `stream` освобождается во второй раз.  Второй выпуск является нарушением CA2202.  
  
```  
using (Stream stream = new FileStream("file.txt", FileMode.OpenOrCreate))  
{  
    using (StreamWriter writer = new StreamWriter(stream))  
    {  
        // Use the writer object...  
    }  
}  
  
```  
  
## Пример  
 Чтобы устранить эту проблему, воспользуйтесь блоком `try`\/`finally` вместо внешнего оператора `using`.  В блоке `finally` убедитесь, что ресурс `stream` не равен null.  
  
```  
Stream stream = null;  
try  
{  
    stream = new FileStream("file.txt", FileMode.OpenOrCreate);  
    using (StreamWriter writer = new StreamWriter(stream))  
    {  
        stream = null;  
        // Use the writer object...  
    }  
}  
finally  
{  
    if(stream != null)  
        stream.Dispose();  
}  
  
```  
  
## См. также  
 <xref:System.IDisposable?displayProperty=fullName>   
 [Шаблон удаления](../Topic/Dispose%20Pattern.md)