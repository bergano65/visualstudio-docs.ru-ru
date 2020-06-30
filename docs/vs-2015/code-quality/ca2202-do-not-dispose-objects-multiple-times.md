---
title: 'CA2202: не удалять объекты несколько раз | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2202
- Do not dispose objects multiple times
- DoNotDisposeObjectsMultipleTimes
helpviewer_keywords:
- CA2202
ms.assetid: fa85349a-cf1e-42c8-a86b-eacae1f8bd96
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 31bf7fe33aa59c3a713d2da81ddbd11ed6899723
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546293"
---
# <a name="ca2202-do-not-dispose-objects-multiple-times"></a>CA2202. Не ликвидируйте объекты несколько раз
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|Значение|
|-|-|
|TypeName|донотдиспосеобжектсмултиплетимес|
|CheckId|CA2202|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Реализация метода содержит пути кода, которые могут вызвать несколько вызовов <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> или эквивалента Dispose, например метод Close () для некоторых типов, для одного и того же объекта.

## <a name="rule-description"></a>Описание правила
 Правильно реализованный <xref:System.IDisposable.Dispose%2A> метод можно вызывать несколько раз, не вызывая исключение. Однако это не гарантируется, и чтобы избежать создания, <xref:System.ObjectDisposedException?displayProperty=fullName> не следует вызывать <xref:System.IDisposable.Dispose%2A> более одного раза для объекта.

## <a name="related-rules"></a>Связанные правила
 [CA2000. Ликвидируйте объекты перед потерей области](../code-quality/ca2000-dispose-objects-before-losing-scope.md)

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, измените реализацию так, чтобы независимо от пути кода <xref:System.IDisposable.Dispose%2A> вызывался только один раз для объекта.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует. Даже если <xref:System.IDisposable.Dispose%2A> известно, что для объекта безопасно вызываться несколько раз, реализация может измениться в будущем.

## <a name="example"></a>Пример
 Вложенные `using` инструкции ( `Using` в Visual Basic) могут вызвать нарушения предупреждения CA2202. Если ресурс IDisposable вложенного внутреннего `using` оператора содержит ресурс внешней `using` инструкции, `Dispose` метод вложенного ресурса освобождает автономный ресурс. При возникновении такой ситуации `Dispose` метод внешней `using` инструкции пытается освободить свой ресурс во второй раз.

 В следующем примере <xref:System.IO.Stream> объект, созданный во внешнем операторе using, освобождается в конце внутреннего оператора using в методе Dispose <xref:System.IO.StreamWriter> объекта, содержащего `stream` объект. В конце внешней `using` инструкции `stream` объект освобождается второй раз. Второй выпуск является нарушением CA2202.

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
 Чтобы устранить эту проблему, используйте `try` / `finally` блок, а не внешний `using` оператор. В `finally` блоке убедитесь, что ресурс не равен `stream` null.

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
 <xref:System.IDisposable?displayProperty=fullName> [Шаблон ликвидации](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
