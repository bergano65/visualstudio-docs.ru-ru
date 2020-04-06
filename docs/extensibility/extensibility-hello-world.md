---
title: Привет Мир расширение учебник (ru) Документы Майкрософт
ms.date: 03/14/2019
ms.topic: conceptual
ms.assetid: f74e1ad1-1ee5-4360-9bd5-d82467b884ca
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c66f48a4b3c5948393e10f34810f3cb87c78c924
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711662"
---
# <a name="create-your-first-extension-hello-world"></a>Создайте свое первое расширение: Hello World

Этот пример Hello World провезрал вас через создавать ваше первое расширение для визуальной студии. В этом уроке показано, как добавить новую команду в Visual Studio.

В процессе вы узнаете, как:

* **[Создание проекта по расширяемости](#create-an-extensibility-project)**
* **[Добавление пользовательской команды](#add-a-custom-command)**
* **[Изменение исходного кода](#modify-the-source-code)**
* **[Выполните команду.](#run-it)**

В этом примере вы будете использовать Visual C, чтобы добавить пользовательскую кнопку меню под названием "Скажи привет Мир!" , который выглядит следующим образом:

![Команда Hello World](media/hello-world-say-hello-world.png)

> [!NOTE]
> Эта статья относится к Visual Studio на Windows. Для Visual Studio для Mac, [см.](/visualstudio/mac/extending-visual-studio-mac-walkthrough)

## <a name="prerequisites"></a>Предварительные требования

Перед запуском убедитесь, что вы установили рабочую нагрузку по **разработке расширения Visual Studio,** которая включает в себя шаблон VSIX, который вам понадобится, и образец кода.

> [!NOTE]
> Вы можете использовать любое издание Visual Studio (Сообщество, Профессиональный или Предприятие) для создания проекта по разъяснению визуальной студии.

## <a name="create-an-extensibility-project"></a>Создание проекта по расширяемости

::: moniker range="vs-2017"

Шаг 1. В меню **Файл** выберите пункт **Создать** > **Проект**.

Шаг 2. В поле поиска в правом верхнем углу введите "vsix" и выберите проект Visual C' **VSIX.** Введите "HelloWorld" для **имени** в нижней части диалога и выберите **OK.**

![создание проекта](media/hello-world-new-project.png)

Теперь вы должны увидеть страницу Getting Started и некоторые примеры ресурсов.

Если вам нужно оставить этот учебник и вернуться к нему, вы можете найти свой новый проект HelloWorld на **стартовой странице** в **недавнем** разделе.

::: moniker-end

::: moniker range=">=vs-2019"

Шаг 1. В меню **Файл** выберите пункт **Создать** > **Проект**. Поиск "vsix" и выберите визуальный **C' VSIX проекта,** а затем **далее**.

Шаг 2. Введите "HelloWorld" для **названия проекта** и выберите **Создать**.

![создание проекта](media/hello-world-new-project-2019.png)

Теперь вы должны увидеть проект HelloWorld в **Solution Explorer**.

::: moniker-end

## <a name="add-a-custom-command"></a>Добавление пользовательской команды

Шаг 1. При выборе файла *манифеста .vsixmanifest* можно увидеть, какие параметры изменчивы, например описание, автор и версия.

Шаг 2. Нажмите правой кнопкой мыши проекта (не решение). В контекстном меню выберите **Добавить,** а затем **новый элемент**.

Шаг 3. Выберите раздел **Расширяемые возможности,** а затем выберите **команду.**

Шаг 4. В поле **Имени** внизу введите имя файла, например, *Command.cs*.

![пользовательская команда](media/hello-world-vsix-command.png)

Новый командный файл отображается в **Solution Explorer.** Под узелом **ресурсов** вы найдете другие файлы, связанные с вашей командой. Например, если вы хотите изменить изображение, файл PNG здесь.

## <a name="modify-the-source-code"></a>Изменение исходного кода

На данный момент, команда и кнопка текста являются автоматически генерируемыми и не очень интересно. Вы можете изменить файл VSCT и файл CS, если вы хотите внести изменения.

* Файл VSCT — это место, где можно переименовать команды, а также определить, куда они идут в командной системе Visual Studio. При изучении файла VSCT вы заметите комментарии, объясняющие, что контролирует каждый раздел кода VSCT.

* Файл CS — это место, где можно определить действия, такие как обработчик клика.

::: moniker range="vs-2017"

Шаг 1. В **Solution Explorer**найдите файл VSCT для новой команды. В этом случае он будет называться *CommandPackage.vsct*.

![пакет команд против](media/hello-world-command-package-vsct.png)

::: moniker-end

::: moniker range=">=vs-2019"

Шаг 1. В **Solution Explorer**найдите файл VSCT для пакета расширения VS. В этом случае он будет называться *HelloWorldPackage.vsct*.

::: moniker-end

Шаг 2. Изменение `ButtonText` параметра `Say Hello World!`на .

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

Шаг 3. Вернитесь к **Solution Explorer** и найдите *Command.cs* файл. В `Execute` методе измените `message` `string.Format(..)` строку с . `Hello World!`

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

Убедитесь в том, чтобы сохранить ваши изменения в каждом файле.

## <a name="run-it"></a>Выполните команду.

Теперь можно запустить исходный код в экспериментальной инстанции Visual Studio.

Шаг 1. Нажмите **F5,** чтобы выполнить команду **Start Debugging.** Эта команда строит ваш проект и запускает отладчик, запуская новый экземпляр Visual Studio под названием **Experimental Instance.**

::: moniker range="vs-2017"

Вы увидите слова **Experimental Instance** в заглавной панели Visual Studio.

![экспериментальный пример заголовок бар](media/hello-world-exp-instance.png)

::: moniker-end

Шаг 2. В меню **Инструменты** **экспериментальной инстанции,** нажмите **Say Hello World!**.

![конечный результат](media/hello-world-final-result.png)

Вы должны увидеть выход из вашей новой пользовательской команды, в этом случае диалог в центре экрана, который дает вам **Hello World!** .

## <a name="next-steps"></a>Следующие шаги

Теперь, когда вы знаете основы работы с Visual Studio Extensibility, вот где вы можете узнать больше:

* [Начните разрабатывать расширения Visual Studio](starting-to-develop-visual-studio-extensions.md) - Образцы, учебники. и публикация вашего расширения
* [Что нового в Визуальной студии 2017 SDK](what-s-new-in-the-visual-studio-2017-sdk.md) - Новые Возможности в Visual Studio 2017
* [Что нового в Visual Studio 2019 SDK](whats-new-visual-studio-2019-sdk.md) - Новые Известия
* [Внутри визуальной студии SDK](internals/inside-the-visual-studio-sdk.md) - Узнайте подробности Визуальной студии Расширяемость
