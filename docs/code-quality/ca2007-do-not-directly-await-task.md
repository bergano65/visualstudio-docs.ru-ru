---
title: 'CA2007: Не следует напрямую ожидать задачу'
ms.date: 03/08/2019
ms.topic: reference
f1_keywords:
- CA2007
- DoNotDirectlyAwaitATaskAnalyzer
helpviewer_keywords:
- CA2007
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
ms.openlocfilehash: 8e94b67d1924e2144f658cd6bcd5989751efdb85
ms.sourcegitcommit: 1024f336dcd8e8a4c50b9a9ad8ec85b6e70073a8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/09/2019
ms.locfileid: "57699683"
---
# <a name="ca2007-do-not-directly-await-a-task"></a>CA2007: Не следует напрямую ожидать задачу

|||
|-|-|
|TypeName|DoNotDirectlyAwaitATaskAnalyzer|
|CheckId|CA2007|
|Категория|Microsoft.Reliability|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Асинхронный метод [ожидает](/dotnet/csharp/language-reference/keywords/await) <xref:System.Threading.Tasks.Task> напрямую.

## <a name="rule-description"></a>Описание правила

Когда асинхронный метод ожидает <xref:System.Threading.Tasks.Task> напрямую, продолжение происходит в том же потоке, который создал задачу. Это поведение может быть дорогостоящей с точки зрения производительности и может привести к взаимоблокировке в потоке пользовательского интерфейса. Рассмотрите возможность вызова <xref:System.Threading.Tasks.Task.ConfigureAwait(System.Boolean)?displayProperty=nameWithType> сигнала вы собираетесь для продолжения.

Это правило входит в состав [анализаторы FxCop](install-fxcop-analyzers.md) и не существует в «традиционные» (анализ статического кода) FxCop.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушения, вызовите <xref:System.Threading.Tasks.Task.ConfigureAwait%2A> на свою <xref:System.Threading.Tasks.Task>. Можно передать или `true` или `false` для `continueOnCapturedContext` параметра.

- Вызов `ConfigureAwait(true)` задачи действует так же, как и вызов явно не <xref:System.Threading.Tasks.Task.ConfigureAwait%2A>. Путем явного вызова этого метода, вы даете читателей о том, что намеренно нужно выполнить продолжение в исходный контекст синхронизации.

- Вызовите `ConfigureAwait(false)` задачи для планирования продолжений в пул потоков, что позволяет избежать взаимоблокировки в потоке пользовательского интерфейса. Передача `false` — хороший вариант для приложений независимых библиотек.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Вы можете отключить это предупреждение, если вы знаете, что потребитель не в приложении графический пользовательский интерфейс (GUI) или если потребитель не имеет <xref:System.Threading.SynchronizationContext>.

## <a name="example"></a>Пример

В следующем фрагменте кода приводит к возникновению предупреждения:

```csharp
public async Task Execute()
{
    Task task = null;
    await task;
}
```

Чтобы устранить нарушение, вызовите <xref:System.Threading.Tasks.Task.ConfigureAwait%2A> на свою <xref:System.Threading.Tasks.Task>:

```csharp
public async Task Execute()
{
    Task task = null;
    await task.ConfigureAwait(false);
}
```

## <a name="see-also"></a>См. также

- [Следует ли ожидать задачу с ConfigureAwait(false)?](https://github.com/Microsoft/vs-threading/blob/master/doc/cookbook_vs.md#should-i-await-a-task-with-configureawaitfalse)
- [Установка анализаторы FxCop в Visual Studio](install-fxcop-analyzers.md)