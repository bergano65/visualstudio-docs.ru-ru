---
title: CA2007. Не следует напрямую ожидать Task
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
ms.openlocfilehash: 3f35e450f17a671b800d003b94ceb5ebc2321c90
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2019
ms.locfileid: "65841393"
---
# <a name="ca2007-do-not-directly-await-a-task"></a>CA2007. Не следует напрямую ожидать Task

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

## <a name="configurability"></a>Возможность настройки

Вы можете настроить ли вы хотите исключить асинхронные методы, которые не возвращают значение из этого правила. Чтобы исключить эти типы методов, добавьте следующую пару "ключ значение" файла editorconfig в проект:

```ini
# Package version 2.9.0 and later
dotnet_code_quality.CA2007.exclude_async_void_methods = true

# Package version 2.6.3 and earlier
dotnet_code_quality.CA2007.skip_async_void_methods = true
```

Можно также настроить, какие выходные данные типов сборки для применения данного правила. Например для этого правила применяются только к коду, формирующий консольного приложения или библиотеки динамической компоновки (то есть не, пользовательского интерфейса приложения), добавьте следующую пару "ключ значение" файла editorconfig в проект:

```ini
dotnet_code_quality.CA2007.output_kind = ConsoleApplication, DynamicallyLinkedLibrary
```

Дополнительные сведения см. в разделе [анализаторы FxCop, Настройка](configure-fxcop-analyzers.md).

## <a name="see-also"></a>См. также

- [Следует ли ожидать задачу с ConfigureAwait(false)?](https://github.com/Microsoft/vs-threading/blob/master/doc/cookbook_vs.md#should-i-await-a-task-with-configureawaitfalse)
- [Установка анализаторы FxCop в Visual Studio](install-fxcop-analyzers.md)