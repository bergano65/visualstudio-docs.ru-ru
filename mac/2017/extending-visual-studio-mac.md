---
title: Расширение Visual Studio для Mac
description: Возможности и функции Visual Studio для Mac можно расширить с помощью модулей, называемых пакетами расширения. В первой части этого руководства создается простой пакет расширения Visual Studio для Mac для вставки даты и времени в документ. Во второй части руководства описаны базовые принципы работы системы пакетов расширения, а также некоторые основные API, составляющие основу Visual Studio для Mac.
author: conceptdev
ms.author: crdun
ms.date: 04/14/2017
ms.technology: vs-ide-sdk
ms.assetid: D5245AB0-8404-426B-B538-F49125E672B2
ms.openlocfilehash: 3465ef29ca732cd26c03919082052d8b26a83ba1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62998228"
---
# <a name="extending-visual-studio-for-mac"></a>Расширение Visual Studio для Mac

Visual Studio для Mac состоит из набора модулей, называемых *пакетами расширения*. Пакеты расширения можно использовать для добавления в Visual Studio для Mac новых функциональных возможностей, таких как поддержка дополнительных языков или нового шаблона проекта.

Пакеты расширения основываются на точках *расширения* других пакетов расширения. Точки расширения — это заполнители для областей, которые могут быть расширены, таких как меню или список команд интегрированной среды разработки. Пакет расширения может использовать точку расширения, зарегистрировав узел структурированных данных, называемый расширением, например новый элемент меню или новую команду. Каждая точка расширения принимает определенные типы расширений, например *Command*, *Pad* или *FileTemplate*. Модуль, содержащий точки расширения, называется *узлом надстройки*, так как он может быть расширен с помощью других пакетов расширения.

Чтобы настроить Visual Studio для Mac, можно создать пакет расширения, который использует точки расширения, содержащиеся в узлах надстройки в существующих библиотеках Visual Studio для Mac, как показано на следующей схеме:

![Архитектура надстройки](media/extending-visual-studio-mac-addin1.png)

Чтобы пакет расширения использовал Visual Studio для Mac, он должен иметь расширения, основанные на существующих точках расширения в интегрированной среде разработки Visual Studio для Mac. Когда пакет расширения основывается на точке расширения, определенной в узле надстройки, считается, что он имеет  _зависимость_  от этого пакета расширения.

Преимуществом такой модульной конструкции является расширяемость Visual Studio для Mac — существует множество точек расширения, которые можно использовать в пользовательских пакетах расширения. К примерам текущих пакетов расширения относится поддержка C# и F#, инструментов отладчика и шаблонов проектов.

> [!NOTE]
> **Примечание**. Если у вас есть проект Add-in Maker, созданный в версии, предшествующей Add-in Maker 1.2, нужно перенести этот проект согласно приведенному [здесь](https://mhut.ch/addinmaker/1.2) описанию.

<!---The [Walkthrough](~/extending-visual-studio-mac-walkthrough.md) topic explains how to build an extension package that uses a *Command* to insert the date and time into an open text document.--->

В этом разделе описаны различные файлы, создаваемые Add-in Maker, а также данные, требуемые расширению команд.

## <a name="attribute-files"></a>Файлы атрибутов

Пакеты расширения хранят метаданные о своем имени, версии, зависимостях и другие сведения в атрибутах C#. Add-in Maker создает два файла — `AddinInfo.cs` и `AssemblyInfo.cs` — для хранения и упорядочивания этих сведений. Пакеты расширения должны иметь в своем *атрибуте Addin* уникальный идентификатор и пространство имен:

```csharp
[assembly:Addin (
   "DateInserter",
   Namespace = "DateInserter",
   Version = "1.0"
)]
```

Пакеты расширения также должны объявлять зависимости для пакетов расширения, владеющих точками расширения, к которым они подключаются. Ссылки на них автоматически задаются во время сборки.

Кроме того, дополнительные ссылки могут добавляться через узел ссылок надстройки на панели решения для проекта, как показано на следующем рисунке:

![Снимок экрана со вставкой даты](media/extending-visual-studio-mac-addin13.png)

Кроме того, во время сборки также добавляются соответствующие им атрибуты `assembly:AddinDependency`. После объявления метаданных и зависимостей можно сосредоточиться на важных стандартных блоках пакета расширения.

## <a name="extensions-and-extension-points"></a>Расширения и точки расширения

Точка расширения — это заполнитель, определяющий структуру данных (тип), тогда как расширение определяет данные, соответствующие структуре, которая указана конкретной точкой расширения. Точки расширения указывают, какой тип расширения они могут принять в своем объявлении. Расширения объявляются с помощью имен типов или путей расширения. Более подробные сведения о создании требуемой точки расширения см. в разделе [Ссылка на точку расширения](https://github.com/mono/mono-addins/wiki/Extension-Points).

Архитектура на базе точек расширения и расширений делает разработку в Visual Studio для Mac быстрой и модульной.

<!--Since there are a large number of extension types, this article focuses on the ones used in the extension package that was built in the [Walkthrough](~/extending-visual-studio-mac-walkthrough.md).-->

### <a name="command-extensions"></a>Расширения команд

<!--[Walkthrough](~/extending-visual-studio-mac-walkthrough.md) uses a Command Extension - an extension that points to methods that are called every time it is executed. -->

Расширения команды — это расширения, которые указывают на методы, вызываемые при каждом выполнении.

Расширения команд определяются путем добавления записей в точку расширения `/MonoDevelop/Ide/Commands`. Мы определили расширение в `Manifest.addin.xml`, используя следующий код:

 ```xml
<Extension path="/MonoDevelop/Ide/Commands/Edit">
  <command id="DateInserter.DateInserterCommands.InsertDate"
            _label="Insert Date"
            _description="Insert the current date"
            defaulthandler="DateInserter.InsertDateHandler" />
</Extension>
```

Узел расширения содержит атрибут пути, указывающий точку расширения, к которому он подключен, в данном случае это `/MonoDevelop/Ide/Commands/Edit`. Кроме того, он выступает в качестве родительского узла для команды. Узел команды имеет следующие атрибуты:

* **id** — задает идентификатор для этой команды. Идентификаторы команд должны объявляться как члены перечисления и используются для подключения команд к элементам CommandItem.
* **_label** — текст, отображаемый в меню.
* **_description** — текст, отображаемый в качестве подсказки для кнопок на панели инструментов.
* **defaultHandler** — указывает класс `CommandHandler`, на котором основана команда.

<!--To invoke the command from the Edit Menu, the walkthrough creates a CommandItem extension that plugs into the `/MonoDevelop/Ide/MainMenu/Edit` extension point:-->

Расширение CommandItem, которое подключается к точке расширения `/MonoDevelop/Ide/MainMenu/Edit`, показано в следующем фрагменте кода:

```xml
<Extension path="/MonoDevelop/Ide/MainMenu/Edit">
  <commanditem id="DateInserter.DateInserterCommands.InsertDate" />
</Extension>
```

CommandItem помещает команду, указанную в его атрибуте идентификатора, в меню. Этот CommandItem расширяет точку расширения `/MonoDevelop/Ide/MainMenu/Edit`, что приводит к отображению метки команды в **меню правки**. Обратите внимание, что **идентификатор** в CommandItem соответствует идентификатору узла команды `InsertDate`. Если удалить CommandItem, параметр **Insert Date** (Вставить дату) исчез бы из меню правки.

### <a name="command-handlers"></a>Обработчики команд

`InsertDateHandler` является расширением класса `CommandHandler`. Он переопределяет два метода — `Update` и `Run`. Метод `Update` запрашивается каждый раз, когда команда отображается в меню или выполняется с помощью настраиваемых сочетаний клавиш. Изменив объект info, вы можете отключить команду, сделать ее невидимой, заполнить команды массива и т. п. Это метод `Update` отключает команды, если не удается найти активный *документ* с *TextEditor* для вставки текста:

```csharp
protected override void Update (CommandInfo info)
{
    info.Enabled = IdeApp.Workbench.ActiveDocument?.Editor != null;
}
```

Переопределять метод `Update` требуется лишь в том случае, когда имеется специальная логика для включения или скрытия команды. Метод `Run` выполняется каждый раз, когда пользователь выполняет команду, что в данном случае происходит, когда пользователь выбирает команду в меню правки. Этот метод вставляет дату и время в позиции курсора в текстовом редакторе:

```csharp
protected override void Run ()
{
  var editor = IdeApp.Workbench.ActiveDocument.Editor;
  var date = DateTime.Now.ToString ();
  editor.InsertAtCaret (date);
}
```

Объявите тип Command в качестве члена перечисления в `DateInserterCommands`:

```csharp
public enum DateInserterCommands
{
  InsertDate,
}
```

Это объединяет Command и CommandItem — CommandItem вызывает Command при выборе CommandItem в **меню правки**.

## <a name="ide-apis"></a>API интегрированной среды разработки

<!--The extension package detailed in the [Walkthrough](~/extending-visual-studio-mac-walkthrough.md) deals with the Text Editor in Visual Studio for Mac, but this is only one of many possible areas for customization. -->

Сведения об областях, доступных для разработки, см. в разделах [Ссылки на дерево расширений](http://monodevelop.com/Developers/Articles/Extension_Tree_Reference) и [Обзор API](http://monodevelop.com/Developers/Articles/API_Overview). При сборке более сложных пакетов расширения также обратитесь к [статьям разработчиков](http://monodevelop.com/Developers/Articles). Ниже приведен неполный список областей для настройки:

* Панели
* Схемы настраиваемых сочетаний клавиш
* Политики
* Модули форматирования кода
* Форматы файлов проекта
* Панели предпочтений
* Панели параметров
* Протоколы отладчика
* Визуализаторы отладчика
* Макеты рабочей области
* Узлы дерева панели решения
* Поля редактора исходного кода
* Подсистемы модульных тестов
* Генераторы кода
* Фрагменты кода
* Требуемые версии .NET Framework
* Целевая среда выполнения
* Серверные компоненты VCS
* Рефакторинг
* Обработчики выражения
* Подсветка синтаксиса

## <a name="additional-information"></a>Дополнительные сведения

> [!NOTE]
> Сейчас мы работаем над улучшением сценариев расширения для Visual Studio для Mac. Если вы создаете расширения и нуждаетесь в дополнительной помощи или информации или хотите оставить отзыв, заполните форму [создания расширений Visual Studio для Mac](https://aka.ms/vsmac-extensions-survey).

## <a name="see-also"></a>См. также

- [Разработка расширений Visual Studio (в Windows)](/visualstudio/extensibility/starting-to-develop-visual-studio-extensions)