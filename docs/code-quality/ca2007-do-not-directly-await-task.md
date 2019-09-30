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
ms.openlocfilehash: cf07c997f933e6aacf3eff29ae204ecd0bedb036
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233076"
---
# <a name="ca2007-do-not-directly-await-a-task"></a>CA2007. Не следует напрямую ожидать Task

|||
|-|-|
|TypeName|донотдиректляваитатасканализер|
|CheckId|CA2007|
|Категория|Microsoft. надежность|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина:

Асинхронный метод [ожидает](/dotnet/csharp/language-reference/keywords/await) <xref:System.Threading.Tasks.Task> непосредственного.

## <a name="rule-description"></a>Описание правила

Когда асинхронный метод ожидает непосредственного <xref:System.Threading.Tasks.Task> выполнения, продолжение происходит в том же потоке, в котором была создана задача. Такое поведение может быть дорогостоящим в плане производительности и может привести к взаимоблокировке потока пользовательского интерфейса. Рассмотрите <xref:System.Threading.Tasks.Task.ConfigureAwait(System.Boolean)?displayProperty=nameWithType> возможность вызова, чтобы сообщить о намерении к продолжению.

Это правило было введено с помощью средств [FxCop Analyzer](install-fxcop-analyzers.md) и не существует в предыдущих анализах FxCop.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушения, вызовите <xref:System.Threading.Tasks.Task.ConfigureAwait%2A> в <xref:System.Threading.Tasks.Task>ожидании. Для `false` `true` параметраможно`continueOnCapturedContext` передать значение или.

- При `ConfigureAwait(true)` вызове в задаче происходит то же поведение, что <xref:System.Threading.Tasks.Task.ConfigureAwait%2A>и при явном вызове. При явном вызове этого метода читатели узнают, что вы намеренно хотите выполнить продолжение в исходном контексте синхронизации.

- Вызовите `ConfigureAwait(false)` задачу, чтобы запланировать продолжение для пула потоков, тем самым избегая взаимоблокировки в потоке пользовательского интерфейса. Передача `false` является хорошим вариантом для библиотек, независимых от приложений.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Это предупреждение можно отключить, если известно, что потребитель не является приложением графического пользовательского интерфейса (GUI) или если потребитель не имеет <xref:System.Threading.SynchronizationContext>.

## <a name="example"></a>Пример

В следующем фрагменте кода создается предупреждение:

```csharp
public async Task Execute()
{
    Task task = null;
    await task;
}
```

Чтобы устранить нарушение, вызовите <xref:System.Threading.Tasks.Task.ConfigureAwait%2A> в <xref:System.Threading.Tasks.Task>ожидаемом виде:

```csharp
public async Task Execute()
{
    Task task = null;
    await task.ConfigureAwait(false);
}
```

## <a name="configurability"></a>Возможности настройки

Можно настроить, следует ли исключать асинхронные методы, которые не возвращают значение из этого правила. Чтобы исключить эти типы методов, добавьте следующую пару "ключ-значение" в editorconfig-файл в проекте:

```ini
# Package version 2.9.0 and later
dotnet_code_quality.CA2007.exclude_async_void_methods = true

# Package version 2.6.3 and earlier
dotnet_code_quality.CA2007.skip_async_void_methods = true
```

Можно также настроить типы выходных сборок, к которым применяется это правило. Например, чтобы применить это правило только к коду, который создает консольное приложение или динамически связанную библиотеку (то есть не приложение пользовательского интерфейса), добавьте следующую пару "ключ-значение" в editorconfig-файл в проекте:

```ini
dotnet_code_quality.CA2007.output_kind = ConsoleApplication, DynamicallyLinkedLibrary
```

Дополнительные сведения см. в статье [Настройка средств FxCop Analyzer](configure-fxcop-analyzers.md).

## <a name="see-also"></a>См. также

- [Следует ли ожидать задачи с ConfigureAwait (false)?](https://github.com/Microsoft/vs-threading/blob/master/doc/cookbook_vs.md#should-i-await-a-task-with-configureawaitfalse)
- [Установка средств FxCop Analyzer в Visual Studio](install-fxcop-analyzers.md)