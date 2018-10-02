---
title: 'CA2202: Не удаляйте объекты несколько раз | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2202
- Do not dispose objects multiple times
- DoNotDisposeObjectsMultipleTimes
helpviewer_keywords:
- CA2202
ms.assetid: fa85349a-cf1e-42c8-a86b-eacae1f8bd96
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0c71f7338ee8dc7a5c7dbdeb6c560cd59abc4197
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591126"
---
# <a name="ca2202-do-not-dispose-objects-multiple-times"></a>CA2202: не удаляйте объекты несколько раз
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA2202: не удаляйте объекты несколько раз](https://docs.microsoft.com/visualstudio/code-quality/ca2202-do-not-dispose-objects-multiple-times).

|||
|-|-|
|TypeName|DoNotDisposeObjectsMultipleTimes|
|CheckId|CA2202|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Реализация метода содержит пути кода, которые могут стать причиной многократного вызова <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> или эквивалентного метода Dispose, например, метода Close() для некоторых типов, на тот же объект.

## <a name="rule-description"></a>Описание правила
 Объект правильно реализована <xref:System.IDisposable.Dispose%2A> метод может вызываться несколько раз без вызова исключения. Тем не менее, это не гарантируется и для предотвращения создания <xref:System.ObjectDisposedException?displayProperty=fullName> не следует вызывать <xref:System.IDisposable.Dispose%2A> более чем один раз для объекта.

## <a name="related-rules"></a>Связанные правила
 [CA2000: удалите объекты до того, как будет потеряна область действия](../code-quality/ca2000-dispose-objects-before-losing-scope.md)

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, измените реализацию таким образом, независимо от того, путь кода, <xref:System.IDisposable.Dispose%2A> вызывается только один раз для объекта.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует. Даже если <xref:System.IDisposable.Dispose%2A> для объекта известно, можно безопасно вызывать несколько раз, его реализация может измениться в будущем.

## <a name="example"></a>Пример
 Вложенные `using` инструкций (`Using` в Visual Basic) может вызвать нарушения CA2202 предупреждения. Если ресурс IDisposable вложенного внутреннего `using` инструкция содержит ресурс внешнего `using` инструкции `Dispose` метод вложенного ресурса освобождает содержимом ресурсе. При возникновении такой ситуации, `Dispose` метод, внешнего `using` оператор пытается ликвидировать свой ресурс еще раз.

 В следующем примере <xref:System.IO.Stream> объект, создаваемый во внешнем инструкцией освобождается в конце внутреннего использования оператора в методе Dispose <xref:System.IO.StreamWriter> , содержащий `stream` объекта. В конце внешний `using` инструкции `stream` объект освобождается во второй раз. Второй выпуск является нарушением CA2202.

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
 Чтобы устранить эту проблему, используйте `try` / `finally` блока вместо внешнего `using` инструкции. В `finally` block, убедитесь, что `stream` ресурс не имеет значение null.

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
 <xref:System.IDisposable?displayProperty=fullName> [Шаблон ликвидации](http://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)



