---
title: Hello World расширение руководство | Документация Майкрософт
ms.date: 03/14/2019
ms.topic: conceptual
ms.assetid: f74e1ad1-1ee5-4360-9bd5-d82467b884ca
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4c3bbafcf138c60b65940bcee73c74f56cf6e2fd
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66342860"
---
# <a name="create-your-first-extension-hello-world"></a>Создайте свое первое расширение: Hello World

В этом примере Hello World поможет создать свое первое расширение для Visual Studio. Этом руководстве показано, как добавить новую команду в Visual Studio.

В процессе, вы узнаете, как:

* **[Создание проекта расширения](#create-an-extensibility-project)**
* **[Добавление пользовательской команды](#add-a-custom-command)**
* **[Изменить исходный код](#modify-the-source-code)**
* **[Запустите его](#run-it)**

В этом примере вы используете Visual C# для добавления пользовательских меню кнопки с именем «Say Hello World!» Это выглядит следующим образом:

![Команду Hello World](media/hello-world-say-hello-world.png)

> [!NOTE]
> Эта статья относится к Visual Studio в Windows. Visual Studio для Mac см. в разделе [Пошаговое руководство по расширяемости в Visual Studio для Mac](/visualstudio/mac/extending-visual-studio-mac-walkthrough).

## <a name="prerequisites"></a>Предварительные требования

Перед началом работы убедитесь, что вы установили **разработка расширений Visual Studio** рабочую нагрузку, которая включает в себя шаблон VSIX, вы должны и пример кода.

> [!NOTE]
> Можно использовать любой выпуск Visual Studio (Community, Professional или Enterprise) для создания проекта расширения Visual Studio.

## <a name="create-an-extensibility-project"></a>Создание проекта расширения

::: moniker range="vs-2017"

Шаг 1. В меню **Файл** выберите пункт **Создать** > **Проект**.

Шаг 2. В поле поиска в правом верхнем углу, введите «vsix» и выберите визуальный элемент C# **проект VSIX**. Введите «HelloWorld» **имя** в нижней части диалогового окна и выберите **ОК**.

![новый проект](media/hello-world-new-project.png)

Теперь вы увидите страницу Приступая к работе и некоторые примеры ресурсов.

Если вам нужно оставить в этом руководстве и вернитесь к ней, можно найти ваш новый проект Hello World на **начальная страница** в **последние** раздел.

::: moniker-end

::: moniker range=">=vs-2019"

Шаг 1. В меню **Файл** выберите пункт **Создать** > **Проект**. Поиск «vsix» и выберите визуальный элемент C# **проект VSIX** и затем **Далее**.

Шаг 2. Введите «HelloWorld» **имя_проекта** и выберите **создать**.

![новый проект](media/hello-world-new-project-2019.png)

Теперь вы увидите проекта HelloWorld в **обозревателе решений**.

::: moniker-end

## <a name="add-a-custom-command"></a>Добавление пользовательской команды

Шаг 1. При выборе *.vsixmanifest* файл манифеста, можно увидеть, какие параметры являются изменяемыми, таких как описание, автора и версии.

Шаг 2. Щелкните правой кнопкой мыши проект (не решение). В контекстном меню выберите **добавить**, а затем **новый элемент**.

Шаг 3. Выберите **расширяемости** раздела, а затем выберите **настраиваемой команды**.

Шаг 4. В **имя** в нижней части, введите имя файла, например *Command.cs*.

![Пользовательская команда](media/hello-world-custom-command.png)

Ваш новый командный файл отображается в **обозревателе решений**. В разделе **ресурсы** узла, вы найдете другие файлы, относящиеся к вашей команды. Например если вы хотите изменить образ, PNG-файл является здесь.

## <a name="modify-the-source-code"></a>Изменить исходный код

На этом этапе команда и текст кнопки формируются автоматически и не очень интересна. Если вы хотите внести изменения, можно изменить файл VSCT и CS-файле.

* Файл VSCT является, где вы можно переименовать вашей команды, а также определить, куда в системе команд Visual Studio. При просмотре файла VSCT, можно заметить, что комментарии с объяснениями какие каждый раздел кода VSCT элементов управления.

* CS-файле является то, где можно определить действия, такие как обработчик щелчка.

::: moniker range="vs-2017"

Шаг 1. В **обозревателе решений**, найдите файл VSCT для вашей новой командой. В этом случае он будет вызываться *CommandPackage.vsct*.

![команды пакета vsct](media/hello-world-command-package-vsct.png)

::: moniker-end

::: moniker range=">=vs-2019"

Шаг 1. В **обозревателе решений**, найдите файл VSCT для пакета расширений VS. В этом случае он будет вызываться *HelloWorldPackage.vsct*.

::: moniker-end

Шаг 2. Изменение `ButtonText` параметр `Say Hello World!`.

```xml
  ...
  <Button guid="guidCommandPackageCmdSet" id="CommandId" priority="0x0100" type="Button">
     <Parent guid="guidCommandPackageCmdSet" id="MyMenuGroup" />
     <Icon guid="guidImages" id="bmpPic1" />
     <Strings>
        <ButtonText>Say Hello World!</ButtonText>
     </Strings>
  </Button>
  ...
```

Шаг 3. Вернитесь к **обозревателе решений** и найти *Command.cs* файла. В `Execute` метод, измените строку `message` из `string.Format(..)` для `Hello World!`.

```csharp
  ...
  private void Execute(object sender, EventArgs e)
  {
    ThreadHelper.ThrowIfNotOnUIThread();
    string message = "Hello World!";
    string title = "Command";

    // Show a message box to prove we were here
    VsShellUtilities.ShowMessageBox(
        this.ServiceProvider,
        message,
        title,
        OLEMSGICON.OLEMSGICON_INFO,
        OLEMSGBUTTON.OLEMSGBUTTON_OK,
        OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST);
  }
  ...
```

Убедитесь в том сохранить изменения для каждого файла.

## <a name="run-it"></a>Запустите его

Теперь можно запустить исходный код в экспериментальном экземпляре Visual Studio.

Шаг 1. Нажмите клавишу **F5** для запуска **начать отладку** команды. Эта команда выполнит сборку проекта и запускает отладчик, запустив новый экземпляр Visual Studio, которые называются **экспериментальный экземпляр**.

::: moniker range="vs-2017"

Вы увидите слова **экспериментальный экземпляр** в заголовке окна Visual Studio.

![Заголовок экспериментальный экземпляр](media/hello-world-exp-instance.png)

::: moniker-end

Шаг 2. На **средства** меню **экспериментальный экземпляр**, нажмите кнопку **Say Hello World!** .

![конечный результат](media/hello-world-final-result.png)

Вы должны увидеть выходные данные из вашей новой пользовательской команды, в данном случае в диалоговом окне в центре экрана, позволяющий **Hello World!** !".

## <a name="next-steps"></a>Следующие шаги

Теперь, когда вы знаете основы работы с Visual Studio расширения, Вот где Дополнительные сведения:

* [Приступить к разработке расширений Visual Studio](starting-to-develop-visual-studio-extensions.md) -примеры, учебники. и публикации расширения
* [Новые возможности в Visual Studio 2017 SDK](what-s-new-in-the-visual-studio-2017-sdk.md) -новые возможности расширяемости в Visual Studio 2017
* [Новые возможности в Visual Studio 2019 SDK](whats-new-visual-studio-2019-sdk.md) -новые возможности расширяемости в Visual Studio 2019 г.
* [Внутри Visual Studio SDK](internals/inside-the-visual-studio-sdk.md) -подробные сведения о расширении среды Visual Studio