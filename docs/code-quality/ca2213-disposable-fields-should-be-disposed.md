---
title: CA2213. Следует высвобождать высвобождаемые поля
ms.date: 05/14/2019
ms.topic: reference
f1_keywords:
- DisposableFieldsShouldBeDisposed
- CA2213
helpviewer_keywords:
- CA2213
- DisposableFieldsShouldBeDisposed
ms.assetid: e99442c9-70e2-47f3-b61a-d8ac003bc6e5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 675206bb58e27110af79c46b1d61e9489f7661f2
ms.sourcegitcommit: 0f44ec8ba0263056ad04d2d0dc904ad4206ce8fc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2019
ms.locfileid: "70766086"
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213. Следует высвобождать высвобождаемые поля

|||
|-|-|
|TypeName|DisposableFieldsShouldBeDisposed|
|CheckId|CA2213|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Тип, реализующий <xref:System.IDisposable?displayProperty=fullName> объявление полей, имеющих типы, которые также реализуют <xref:System.IDisposable>. Метод этого поля не вызывается <xref:System.IDisposable.Dispose%2A> методом объявляющего типа. <xref:System.IDisposable.Dispose%2A>

## <a name="rule-description"></a>Описание правила

Тип отвечает за удаление всех неуправляемых ресурсов. Правило CA2213 проверяет, объявляет ли удаляемый тип (то есть, один <xref:System.IDisposable>из реализаций `T` ) поле `F` , которое является экземпляром высвобождаемого типа `FT`. Для каждого поля `F` , которому назначается локально созданный объект в методах или инициализаторах содержащего типа `T`, правило пытается нахождение вызова `FT.Dispose`. Правило ищет методы, вызываемые `T.Dispose` , и один уровень ниже (то есть методы, вызываемые методами `T.Dispose`, вызываемыми).

> [!NOTE]
> Кроме [особых случаев](#special-cases), правило CA2213 срабатывает только для полей, которым назначен локально созданный удаляемый объект в методах и инициализаторах содержащего типа. Если объект создан или назначен вне типа `T`, правило не срабатывает. Это уменьшает шум в случаях, когда вмещающий тип не владеет ответственностью за удаление объекта.

### <a name="special-cases"></a>Особые случаи

Правило CA2213 также может срабатывать для полей следующих типов, даже если объект, которому они назначены, не создается локально:

- <xref:System.IO.Stream?displayProperty=nameWithType>
- <xref:System.IO.TextReader?displayProperty=nameWithType>
- <xref:System.IO.TextWriter?displayProperty=nameWithType>
- <xref:System.Resources.IResourceReader?displayProperty=nameWithType>

Передача объекта одного из этих типов в конструктор, а затем присваивание его полю указывает на *передачу владения владельцем* вновь сформированного типа. То есть вновь сконструированный тип теперь отвечает за удаление объекта. Если объект не удален, возникает нарушение CA2213.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, вызовите <xref:System.IDisposable.Dispose%2A> для полей, имеющих типы, реализующие. <xref:System.IDisposable>

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Предупреждение из этого правила можно отключить, если:

- Помеченный тип не отвечает за освобождение ресурса, удерживаемого полем (то есть тип не имеет *владельца*)
- Вызов <xref:System.IDisposable.Dispose%2A> выполняется на более глубоком уровне, чем проверка правила

## <a name="example"></a>Пример

В следующем фрагменте кода показан `TypeA` тип, <xref:System.IDisposable>реализующий интерфейс.

[!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_1.cs)]

В следующем фрагменте кода показан `TypeB` тип, нарушающий правило CA2213 путем объявления поля `aFieldOfADisposableType` как высвобождаемого типа (`TypeA`) и не обращающегося <xref:System.IDisposable.Dispose%2A> к полю.

[!code-csharp[FxCop.Usage.IDisposableFields#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_2.cs)]

Чтобы устранить нарушение, вызовите `Dispose()` в поле для уничтожения:

```csharp
protected virtual void Dispose(bool disposing)
{
   if (!disposed)
   {
      // Dispose of resources held by this instance.
      aFieldOfADisposableType.Dispose();

      disposed = true;

      // Suppress finalization of this disposed instance.
      if (disposing)
      {
          GC.SuppressFinalize(this);
      }
   }
}
```

## <a name="see-also"></a>См. также

- <xref:System.IDisposable?displayProperty=fullName>
- [Шаблон удаления](/dotnet/standard/design-guidelines/dispose-pattern)