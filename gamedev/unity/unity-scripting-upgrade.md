---
title: Использование .NET 4.x в Unity
description: Сведения о том, как использовать .NET 4.x в Unity. Включение среды выполнения скриптов .NET 4.x в Unity. Использование преимуществ совместимости с .NET. Знакомство с новыми возможностями синтаксиса и языка.
author: therealjohn
ms.author: johmil
ms.date: 08/29/2018
ms.topic: how-to
ms.assetid: E2C9420F-A5D5-4472-9020-2B63FB27A133
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.workload:
- unity
ms.openlocfilehash: 5b7e36d0f0c29e997b4b39506fb27d73ceb45146
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2020
ms.locfileid: "94341250"
---
# <a name="using-net-4x-in-unity"></a>Использование .NET 4.x в Unity

C# и .NET, технологии, лежащие в основе базовых сценариев Unity, получают обновления с тех пор, как корпорация Майкрософт выпустила их в 2002 году. При этом разработчики Unity могут не знать о постоянном потоке новых функций, добавляемых в язык C# и .NET Framework. Это связано с тем, что до выхода Unity 2017.1, в Unity использовалась среда выполнения сценариев, эквивалентная .NET 3.5, которая не обновлялась годами.

В выпуске Unity 2017.1 появилась экспериментальная версия среды выполнения сценариев, обновленная до версии, совместимой с .NET 4.6 и C# 6. В Unity 2018.1 аналогичная среда выполнения .NET 4.x уже не считается экспериментальный, а вот более ранняя аналогичная среда выполнения .NET 3.5 теперь считается устаревшей. Ожидается, что в версии Unity 2018.3 обновленная среда выполнения сценариев будет обновлена до C# 7 и станет использоваться по умолчанию. Дополнительную информацию и последние новости о стратегии этого продукта см. в [этой записи блога](https://blogs.unity3d.com/2018/07/11/scripting-runtime-improvements-in-unity-2018-2/) Unity и на [форуме о предварительных версиях экспериментальных сценариев](https://forum.unity.com/forums/experimental-scripting-previews.107/). А пока прочтите следующие разделы этой статьи и узнайте о новых функциях, появившихся в среде выполнения сценариев .NET 4.x.

## <a name="prerequisites"></a>Обязательные условия

* [Unity 2017.1 или более поздней версии](https://unity3d.com/) (рекомендуется 2018.2)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

## <a name="enabling-the-net-4x-scripting-runtime-in-unity"></a>Включение среды выполнения сценариев .NET 4.x в Unity

Чтобы включить среду выполнения сценариев .NET 4.x, выполните следующие действия.

1. Откройте "Параметры проигрывателя" в инспекторе Unity, выбрав параметры **Правка > Параметры проигрывателя > Проигрыватель**.

1. В разделе **Конфигурация** откройте раскрывающийся список **Версия среды выполнения сценариев** и выберите пункт **Эквивалент .NET 4.x**. Программа предложит перезагрузить Unity.

![Выберите эквивалент .NET 4.x.](media/vs/vstu-scripting-runtime-version.png)

## <a name="choosing-between-net-4x-and-net-standard-20-profiles"></a>Выбор между профилями .NET 4.x и .NET Standard 2.0

После переключения на эквивалентную среду выполнения сценариев .NET 4.x можно указать **Уровень совместимости API** с помощью раскрывающегося списка в "Параметрах проигрывателя" ( **Правка > Параметры проигрывателя > Проигрыватель** ). Существует два варианта.

* **.NET Standard 2.0**. Этот профиль соответствует [профилю .NET Standard 2.0](https://github.com/dotnet/standard/blob/master/docs/versions/netstandard2.0.md), опубликованному .NET Foundation. Unity рекомендует использовать для новых проектов .NET Standard 2.0. Эта версия ниже, чем .NET 4.x, что полезно для платформ ограниченного размера. Кроме того, Unity обеспечивает поддержку этого профиля на всех поддерживаемых Unity платформах.

* **.NET 4.x**. Этот профиль предоставляет доступ к последней версии API .NET 4. Он включает все коды, доступные в библиотеках классов .NET Framework, и поддерживает профили .NET Standard 2.0. Выбирайте профиль .NET 4.x, если для вашего проекта требуется та часть API, которая не входит в профиль .NET Standard 2.0. При этом некоторые части этого API могут поддерживаться не на всех платформах Unity.

Дополнительные сведения об этих вариантах см. в [этой записи блога](https://blogs.unity3d.com/2018/03/28/updated-scripting-runtime-in-unity-2018-1-what-does-the-future-hold/) Unity.

### <a name="adding-assembly-references-when-using-the-net-4x-api-compatibility-level"></a>Добавление ссылок на сборки при использовании уровня совместимости API .NET 4.x

Если в раскрывающемся меню **Уровень совместимости API** будет выбран параметр .NET Standard 2.0, все сборки в профиле API станут ссылаемыми и доступными для использования. При выборе профиля более поздней версии .NET 4.x ссылки на некоторые сборки, которые входят в Unity, по умолчанию не включаются. Чтобы использовать эти API, необходимо добавить ссылку на сборку вручную. Вы можете просмотреть сборки, которые входят в каталог **MonoBleedingEdge/lib/mono** вашей установки редактора Unity:

![Каталог MonoBleedingEdge](media/vs/vstu-monobleedingedge.png)

Например, если вы используете профиль .NET 4.x и хотите использовать `HttpClient`, необходимо добавить ссылку на сборку System.Net.Http.dll. Если этого не сделать, компилятор выдаст сообщение об отсутствующей ссылке на сборку:

![отсутствует ссылка на сборку](media/vs/vstu-missing-reference.png)

Visual Studio создает файлы.csproj и .sln для проектов Unity каждый раз, когда они открываются. Это значит, что добавить ссылки на сборки в Visual Studio напрямую нельзя, поскольку при повторном открытии проекта они будут потеряны. Вместо этого необходимо использовать специальный текстовый файл с именем **mcs.rsp** :

1. Создайте текстовый файл с именем **mcs.rsp** в корневом каталоге **Assets** проекта Unity.

1. В первой строке пустого текстового файла введите: `-r:System.Net.Http.dll`, а затем сохраните файл. Вместо System.Net.Http.dll можно указать любую добавленную сборку с отсутствующей ссылкой.

1. Перезапустите редактор Unity.

## <a name="taking-advantage-of-net-compatibility"></a>Преимущества совместимости с .NET

Помимо новых возможностей синтаксиса и языка C#, среда выполнения сценариев .NET 4.x предоставляет пользователям Unity доступ к огромной библиотеке пакетов .NET, несовместимых с устаревшей средой выполнения сценариев .NET 3.5.

### <a name="add-packages-from-nuget-to-a-unity-project"></a>Добавление пакетов из NuGet в проект Unity

[NuGet](https://www.nuget.org/) — это диспетчер пакетов для .NET. NuGet интегрирована в Visual Studio. При этом для добавления пакетов NuGet в проекты Unity требуется специальный процесс. Это связано с тем, что при открытии проекта в Unity все файлы проектов Visual Studio формируются заново, а ненужные конфигурации отменяются. Чтобы добавить пакет из NuGet в проект Unity, выполните следующие действия.

1. Откройте NuGet и найдите совместимый пакет, который вам нужно добавить (.NET Standard 2.0 или .NET 4.x). В этом примере показано добавление [Json.NET](https://www.nuget.org/packages/Newtonsoft.Json/) (популярного пакета для работы с JSON) в проект .NET Standard 2.0.

1. Нажмите кнопку **Загрузить** :

    ![кнопка "Загрузить"](media/vs/vstu-nuget-download.png)

1. Найдите загруженный файл и измените его расширение с **.nupkg** на **.zip**.

1. В ZIP-файле зайдите в каталог **lib/netstandard2.0** и скопируйте файл **Newtonsoft.Json.dll**.

1. В папке **Assets** в корневом каталоге проекта Unity создайте папку с именем **Plugins** (Подключаемые модули). В Unity "Plugins" — это имя специальной папки. Дополнительные сведения см. в [документации по Unity](https://docs.unity3d.com/Manual/Plugins.html).

1. Скопируйте файл **Newtonsoft.Json.dll** в каталог **Plugins** проекта Unity.

1. Создайте файл с именем **link.xml** в каталоге **Assets** проекта Unity и добавьте приведенный ниже код XML.  Это нужно для того, чтобы процесс удаления байт-кода в Unity не удалял необходимые данные при экспорте в платформу IL2CPP.  Несмотря на то что это действие относится только к данной библиотеке, проблемы могут возникнуть и с другими библиотеками, которые используют отражение подобным образом.  Дополнительные сведения на эту тему см. в [документации по Unity](https://docs.unity3d.com/Manual/IL2CPP-BytecodeStripping.html).

    ```xml
    <linker>
      <assembly fullname="System.Core">
        <type fullname="System.Linq.Expressions.Interpreter.LightLambda" preserve="all" />
      </assembly>
    </linker>
    ```

Теперь пакет Json.NET готов к работе.

```csharp
using Newtonsoft.Json;
using UnityEngine;

public class JSONTest : MonoBehaviour
{
    class Enemy
    {
        public string Name { get; set; }
        public int AttackDamage { get; set; }
        public int MaxHealth { get; set; }
    }
    private void Start()
    {
        string json = @"{
            'Name': 'Ninja',
            'AttackDamage': '40'
            }";

        var enemy = JsonConvert.DeserializeObject<Enemy>(json);

        Debug.Log($"{enemy.Name} deals {enemy.AttackDamage} damage.");
        // Output:
        // Ninja deals 40 damage.
    }
}
```

Это простой пример использования библиотеки без зависимостей. Если одни пакеты NuGet зависят от других, необходимо вручную загрузить эти зависимости и добавить их в проект таким же образом.

## <a name="new-syntax-and-language-features"></a>Новые возможности синтаксиса и языка

Обновленная среда выполнения сценариев предоставляет разработчикам Unity доступ к C# 6 и целому ряду новых возможностей синтаксиса и языка.

### <a name="auto-property-initializers"></a>Инициализаторы автосвойств

Синтаксис автосвойств в среде выполнения сценариев Unity .NET 3.5 позволял быстро определить неинициализированные свойства, но саму инициализацию нужно прописывать в сценарии отдельно. В среде выполнения .NET 4.x автосвойства можно инициализировать в той же строке:

```csharp
// .NET 3.5
public int Health { get; set; } // Health has to be initialized somewhere else, like Start()

// .NET 4.x
public int Health { get; set; } = 100;
```

### <a name="string-interpolation"></a>Интерполяция строк

В более ранней среде выполнения .NET 3.5 синтаксис объединения строк был громоздким. В новой среде выполнения .NET 4.x есть функция [`$`интерполяции строк](/dotnet/csharp/language-reference/tokens/interpolated), которая позволяет вставлять выражения в строки, используя более прямой и удобочитаемый синтаксис:

```csharp
// .NET 3.5
Debug.Log(String.Format("Player health: {0}", Health)); // or
Debug.Log("Player health: " + Health);

// .NET 4.x
Debug.Log($"Player health: {Health}");
```

### <a name="expression-bodied-members"></a>Элементы, воплощающие выражение

Новый синтаксис C# в среде выполнения .NET 4.x позволяет заменять тело функций на [лямбда-выражения](/dotnet/csharp/programming-guide/statements-expressions-operators/lambda-expressions) и, таким образом, делать их более краткими:

```csharp
// .NET 3.5
private int TakeDamage(int amount)
{
    return Health -= amount;
}

// .NET 4.x
private int TakeDamage(int amount) => Health -= amount;
```

Члены, заданные выражениями, теперь можно использовать также в свойствах, доступных только для чтения:

```csharp
// .NET 4.x
public string PlayerHealthUiText => $"Player health: {Health}";
```

### <a name="task-based-asynchronous-pattern-tap"></a>Асинхронный шаблон, основанный на задачах (TAP)

[Асинхронное программирование](/dotnet/csharp/async) позволяет выполнять длинные операции без зависания приложений. Кроме того, с помощью этой функции можно сделать так, чтобы код, в котором используются результаты ресурсоемких операций, выполнялся только после того, как будут выполнены эти операции, например после загрузки определенного файла или завершения сетевой операции.

В Unity асинхронное программирование обычно выполняется с [соподпрограммами](https://docs.unity3d.com/Manual/Coroutines.html). Однако начиная с C# 5 предпочтительным методом асинхронного программирования в среде разработки .NET стал [Асинхронный шаблон, основанный на задачах (TAP)](/dotnet/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap), с использованием ключевых слов `async` и `await` в [System.Threading.Task](/dotnet/api/system.threading.tasks.task). Таким образом, для функции `async` можно задать ожидание завершения задачи (`await`) без запрета обновлений в остальной части приложения:

```csharp
// Unity coroutine
using UnityEngine;
public class UnityCoroutineExample : MonoBehaviour
{
    private void Start()
    {
        StartCoroutine(WaitOneSecond());
        DoMoreStuff(); // This executes without waiting for WaitOneSecond
    }
    private IEnumerator WaitOneSecond()
    {
        yield return new WaitForSeconds(1.0f);
        Debug.Log("Finished waiting.");
    }
}
```

```csharp
// .NET 4.x async-await
using UnityEngine;
using System.Threading.Tasks;
public class AsyncAwaitExample : MonoBehaviour
{
    private async void Start()
    {
        Debug.Log("Wait.");
        await WaitOneSecondAsync();
        DoMoreStuff(); // Will not execute until WaitOneSecond has completed
    }
    private async Task WaitOneSecondAsync()
    {
        await Task.Delay(TimeSpan.FromSeconds(1));
        Debug.Log("Finished waiting.");
    }
}
```

TAP — это сложная тема с определенными характерными для Unity нюансами, которые разработчикам необходимо учитывать, поэтому его нельзя назвать универсальной заменой соподпрограммам в Unity. Тем не менее это полезный инструмент. Сфера применения этого компонента выходит за рамки данной статьи, но некоторые общие рекомендации и советы вы найдете ниже.

#### <a name="getting-started-reference-for-tap-with-unity"></a>Начало работы с TAP в Unity

Эти советы помогут вам приступить к работе с TAP в Unity.

* Асинхронные функции, выполнения которых код будет дожидаться, должны иметь тип возвращаемого значения [`Task`](/dotnet/api/system.threading.tasks.task) или [`Task<TResult>`](/dotnet/api/system.threading.tasks.task-1).
* К именам асинхронных функций, возвращающих задачу, необходимо добавлять суффикс **Async**. Суффикс Async означает, что эта функция требует ожидания.
* Используйте тип возвращаемого значения `async void` только для тех функций, которые запускают асинхронные функции из традиционного синхронного кода. Сами такие функции не могут требовать ожидания, а их имена не должны содержать суффикс Async.
* Чтобы асинхронные функции по умолчанию выполнялись в основном потоке, в Unity используется unitySynchronizationContext. API Unity за пределами основного потока недоступен.
* Можно выполнять задачи в фоновых потоках с помощью таких методов, как [`Task.Run`](/dotnet/api/system.threading.tasks.task.run) и [`Task.ConfigureAwait(false)`](/dotnet/api/system.threading.tasks.task.configureawait). Этот прием пригодится для выгрузки ресурсоемких операций из основного потока и повышения производительности. При этом использование фоновых потоков может привести к возникновению трудно устраняемых проблем, например привести к [состоянию гонки](https://wikipedia.org/wiki/Race_condition).
* API Unity за пределами основного потока недоступен.
* Задачи, использующие потоки, в сборках Unity WebGL не поддерживаются.

#### <a name="differences-between-coroutines-and-tap"></a>Различия между соподпрограммами и TAP

Между соподпрограммами и TAP (async-await) есть несколько важных различий.

* Соподпрограммы не могут возвращать значения, а `Task<TResult>` может.
* Вставить `yield` в оператор try-catch нельзя, что затрудняет обработку ошибок при использовании соподпрограмм. При этом try-catch работает с TAP.
* Функция соподпрограмм в Unity недоступна в классах, которые не являются производными от MonoBehaviour. Для асинхронного программирования в таких классах отлично подходит TAP.
* В настоящее время Unity не предлагает TAP как полную замену соподпрограмм. Узнать результаты применения одного или другого подхода для конкретного проекта можно только путем профилирования.

> [!NOTE]
> В Unity 2018.2 отладка асинхронных методов с использованием точек останова не поддерживается в полном объеме; [эта возможность будет реализована в Unity 2018.3](https://twitter.com/jbevain/status/900043560665235456).

### <a name="nameof-operator"></a>Оператор nameof

Оператор `nameof` получает строковое имя, тип или член переменной. В некоторых случаях `nameof` удобно использовать для регистрации ошибок и получения строкового имени перечисления.

```csharp
// Get the string name of an enum:
enum Difficulty {Easy, Medium, Hard};
private void Start()
{
    Debug.Log(nameof(Difficulty.Easy));
    RecordHighScore("John");
    // Output:
    // Easy
    // playerName
}
// Validate parameter:
private void RecordHighScore(string playerName)
{
    Debug.Log(nameof(playerName));
    if (playerName == null) throw new ArgumentNullException(nameof(playerName));
}
```

### <a name="caller-info-attributes"></a>Информационные атрибуты вызывающего объекта

[Информационные атрибуты вызывающего объекта](/dotnet/csharp/programming-guide/concepts/caller-information) содержат информацию о вызывающем объекте метода. Для каждого параметра, который вы хотите использовать c информационным атрибутом вызывающего объекта, необходимо указать значение по умолчанию.

```csharp
private void Start ()
{
    ShowCallerInfo("Something happened.");
}
public void ShowCallerInfo(string message,
        [System.Runtime.CompilerServices.CallerMemberName] string memberName = "",
        [System.Runtime.CompilerServices.CallerFilePath] string sourceFilePath = "",
        [System.Runtime.CompilerServices.CallerLineNumber] int sourceLineNumber = 0)
{
    Debug.Log($"message: {message}");
    Debug.Log($"member name: {memberName}");
    Debug.Log($"source file path: {sourceFilePath}");
    Debug.Log($"source line number: {sourceLineNumber}");
}
// Output:
// Something happened
// member name: Start
// source file path: D:\Documents\unity-scripting-upgrade\Unity Project\Assets\CallerInfoTest.cs
// source line number: 10
```

### <a name="using-static"></a>Директива using static

Директива [using static](/dotnet/csharp/language-reference/keywords/using-static) позволяет использовать статические функции, не указывая имя класса. Директива using static помогает сэкономить место и время при использовании нескольких статических функций одного класса.

```csharp
// .NET 3.5
using UnityEngine;
public class Example : MonoBehaviour
{
    private void Start ()
    {
        Debug.Log(Mathf.RoundToInt(Mathf.PI));
        // Output:
        // 3
    }
}
```

```csharp
// .NET 4.x
using UnityEngine;
using static UnityEngine.Mathf;
public class UsingStaticExample: MonoBehaviour
{
    private void Start ()
    {
        Debug.Log(RoundToInt(PI));
        // Output:
        // 3
    }
}
```

## <a name="il2cpp-considerations"></a>Рекомендации по IL2CPP

При экспорте ваших игр в такие платформы, как iOS, Unity с помощью IL2CPP "транскомпилирует" IL в код C++, который затем компилируется собственным компилятором целевой платформы. Некоторые функции .NET при этом не поддерживаются — это части функции отражения и ключевое слово `dynamic`. Вы можете использовать их для управления в собственном коде, но при работе с DLL и SDK других разработчиков, созданными без расчета на Unity и IL2CPP, вы можете столкнуться с проблемами. Дополнительные сведения на эту тему см. в документации об [ ограничениях сценариев](https://docs.unity3d.com/Manual/ScriptingRestrictions.html) на веб-сайте Unity.

Кроме того, как уже говорилось в приведенном выше примере Json.NET, во время экспорта IL2CPP Unity попытается удалить неиспользуемый код.  Обычно это не страшно, но в случае с библиотеками, где используется отражение, это может привести к случайному удалению свойств или методов, которые будут вызываться в среде выполнения и не могут быть заданы во время экспорта.  Для решения этой проблемы добавьте в свой проект файл **link.xml** , содержащий список сборок и пространств имен, к которым не нужно применять процесс удаления.  Дополнительные сведения см. в [документации Unity по удалению байт-кода](https://docs.unity3d.com/Manual/IL2CPP-BytecodeStripping.html).

## <a name="net-4x-sample-unity-project"></a>Образец проекта Unity в .NET 4.x

Данный образец содержит примеры использования нескольких функций .NET 4.x. Загрузить проект или просмотреть исходный код можно в [GitHub](https://github.com/Microsoft/unity-scripting-upgrade).

## <a name="additional-resources"></a>Дополнительные ресурсы

* [Блог Unity: усовершенствования среды выполнения сценариев в Unity 2018.2](https://blogs.unity3d.com/2018/07/11/scripting-runtime-improvements-in-unity-2018-2/)
* [История C#](/dotnet/csharp/whats-new/csharp-version-history)
* [Что нового в C# 6](/dotnet/csharp/whats-new/csharp-6)
* [Асинхронное программирование в Unity с использованием соподпрограмм и TAP](/archive/blogs/appconsult/unity-coroutine-tap-en-us)
* [Async-Await вместо соподпрограмм в Unity 2017](http://www.stevevermeulen.com/index.php/2017/09/using-async-await-in-unity3d-2017/)
* [Форум Unity: предварительные версии экспериментальных сценариев](https://forum.unity.com/forums/experimental-scripting-previews.107/)