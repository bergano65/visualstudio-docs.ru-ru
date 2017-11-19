---
title: "CA2202: Не удаляйте объекты несколько раз | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2202
- Do not dispose objects multiple times
- DoNotDisposeObjectsMultipleTimes
helpviewer_keywords: CA2202
ms.assetid: fa85349a-cf1e-42c8-a86b-eacae1f8bd96
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ab5acc92df96c416cd614ac18ac66ff34d142a22
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca2202-do-not-dispose-objects-multiple-times"></a>CA2202: не удаляйте объекты несколько раз
|||  
|-|-|  
|TypeName|DoNotDisposeObjectsMultipleTimes|  
|CheckId|CA2202|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Реализация метода содержит пути кода, которые могли стать причиной многократного вызова <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> или эквивалентного метода Dispose, например, метода Close() для некоторых типов того же объекта.  
  
## <a name="rule-description"></a>Описание правила  
 A правильно реализована <xref:System.IDisposable.Dispose%2A> метод может вызываться несколько раз без вызова исключения. Однако это не гарантируется и для предотвращения создания <xref:System.ObjectDisposedException?displayProperty=fullName> не следует вызывать <xref:System.IDisposable.Dispose%2A> более чем один раз на объект.  
  
## <a name="related-rules"></a>Связанные правила  
 [CA2000: удалите объекты до того, как будет потеряна область действия](../code-quality/ca2000-dispose-objects-before-losing-scope.md)  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, измените реализацию таким образом, независимо от того, путь кода <xref:System.IDisposable.Dispose%2A> вызывается только один раз для объекта.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует. Даже если <xref:System.IDisposable.Dispose%2A> для объекта известно, что можно безопасно вызывать несколько раз, его реализация может измениться в будущем.  
  
## <a name="example"></a>Пример  
 Вложенные `using` инструкций (`Using` в Visual Basic) может привести к нарушения CA2202 предупреждения. Если ресурс IDisposable вложенного внутреннего `using` инструкция содержит ресурс внешнего `using` инструкции `Dispose` метод вложенного ресурса освобождает содержащегося ресурса. При возникновении такой ситуации `Dispose` метод внешнего `using` оператор пытается ликвидировать свой ресурс еще раз.  
  
 В следующем примере <xref:System.IO.Stream> объект, создаваемый во внешнем инструкцией освобождается в конце внутренний, с помощью инструкции в методе Dispose <xref:System.IO.StreamWriter> , содержащий `stream` объекта. В конце внешнего `using` инструкции `stream` объект освобождается еще раз. Второй выпуск является нарушением CA2202.  
  
```  
using (Stream stream = new FileStream("file.txt", FileMode.OpenOrCreate))  
{  
    using (StreamWriter writer = new StreamWriter(stream))  
    {  
        // Use the writer object...  
    }  
}  
  
```  
  
## <a name="example"></a>Пример  
 Чтобы устранить эту проблему, используйте `try` / `finally` блок вместо внешнего `using` инструкции. В `finally` блока, убедитесь, что `stream` ресурса не имеет значение null.  
  
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
  
## <a name="see-also"></a>См. также  
 <xref:System.IDisposable?displayProperty=fullName>   
 [Шаблон удаления](/dotnet/standard/design-guidelines/dispose-pattern)