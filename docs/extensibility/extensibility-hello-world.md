---
title: Руководство по расширению Hello World | Документация Майкрософт
ms.date: 03/14/2019
ms.topic: conceptual
ms.assetid: f74e1ad1-1ee5-4360-9bd5-d82467b884ca
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0345d67a4202b8b267d213e0c288847e2774f722
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/25/2019
ms.locfileid: "75404136"
---
# <a name="create-your-first-extension-hello-world"></a>Создайте свое первое расширение: Hello World

В этом Hello World примере рассматривается создание первого расширения для Visual Studio. В этом руководстве показано, как добавить новую команду в Visual Studio.

В процессе вы узнаете, как выполнять следующие задачи:

* **[Создание проекта расширения среды](#create-an-extensibility-project)**
* **[Добавление пользовательской команды](#add-a-custom-command)**
* **[Изменение исходного кода](#modify-the-source-code)**
* **[Запустите его](#run-it)**

В этом примере используется визуальный C# элемент для добавления пользовательской кнопки меню с именем «скажите Hello World!». Это выглядит следующим образом:

![Команда Hello World](media/hello-world-say-hello-world.png)

> [!NOTE]
> Эта статья относится к Visual Studio в Windows. Visual Studio для Mac см. [в разделе Пошаговое руководство по расширению среды в Visual Studio для Mac](/visualstudio/mac/extending-visual-studio-mac-walkthrough).

## <a name="prerequisites"></a>Prerequisites

Прежде чем начать, убедитесь, что вы установили рабочую нагрузку **разработки расширений Visual Studio** , которая включает НУЖНЫЙ шаблон VSIX и пример кода.

> [!NOTE]
> Для создания проекта расширения Visual Studio можно использовать любой выпуск Visual Studio (Community, Professional или Enterprise).

## <a name="create-an-extensibility-project"></a>Создание проекта расширения среды

::: moniker range="vs-2017"

Шаг 1. В меню **Файл** выберите **Создать**  > **Проект**.

Шаг 2. В поле поиска в правом верхнем углу введите "VSIX" и выберите C# **проект Visual VSIX**. Введите "HelloWorld" в качестве **имени** в нижней части диалогового окна и нажмите кнопку " **ОК**".

![новый проект](media/hello-world-new-project.png)

Теперь вы увидите страницу начало работы и некоторые примеры ресурсов.

Если вам нужно выйти из этого учебника и вернуться к нему, можно найти новый проект HelloWorld на **начальной странице** в разделе **последних** .

::: moniker-end

::: moniker range=">=vs-2019"

Шаг 1. В меню **Файл** выберите **Создать**  > **Проект**. Выполните поиск по запросу "VSIX" и выберите C# **проект Visual VSIX** , а затем нажмите кнопку **Далее**.

Шаг 2. Введите "HelloWorld" в качестве **имени проекта** и нажмите кнопку " **создать**".

![новый проект](media/hello-world-new-project-2019.png)

Теперь вы увидите проект HelloWorld в **Обозреватель решений**.

::: moniker-end

## <a name="add-a-custom-command"></a>Добавление пользовательской команды

Шаг 1. Если выбрать файл манифеста *vsixmanifest* , можно увидеть, какие параметры могут быть изменены, например описание, автор и версия.

Шаг 2. Щелкните проект правой кнопкой мыши (не решение). В контекстном меню выберите **Добавить**, а затем **новый элемент**.

Шаг 3. Выберите раздел **расширяемость** , а затем выберите **команду**.

Шаг 4. В поле **Name (имя** ) в нижней части экрана введите имя файла, например *Command.CS*.

![Настраиваемая команда](media/hello-world-vsix-command.png)

Новый командный файл отображается в **Обозреватель решений**. В узле **ресурсы** найдите другие файлы, связанные с вашей командой. Например, если вы хотите изменить образ, PNG-файл будет здесь.

## <a name="modify-the-source-code"></a>Изменение исходного кода

На этом этапе текст команды и кнопки создается автоматически и не очень интересно. Если вы хотите внести изменения, вы можете изменить файл VSCT и файл CS.

* В файле VSCT можно переименовать команды, а также определить, где они находятся в командной системе Visual Studio. Просматривая файл VSCT, вы увидите комментарии, объясняющие, что из каждого раздела элементов управления "код VSCT".

* В файле CS можно определить действия, например обработчик щелчка.

::: moniker range="vs-2017"

Шаг 1. В **Обозреватель решений**найдите файл VSCT для новой команды. В этом случае он будет называться *коммандпаккаже. vsct*.

![пакет команд vsct](media/hello-world-command-package-vsct.png)

::: moniker-end

::: moniker range=">=vs-2019"

Шаг 1. В **Обозреватель решений**найдите файл VSCT для пакета vs. В этом случае он будет называться *хелловорлдпаккаже. vsct*.

::: moniker-end

Шаг 2. Измените параметр `ButtonText` на `Say Hello World!`.

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

Шаг 3. Вернитесь к **Обозреватель решений** и найдите файл *Command.CS* . В методе `Execute` измените строку `message` с `string.Format(..)` на `Hello World!`.

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

Не забудьте сохранить изменения в каждом файле.

## <a name="run-it"></a>Выполните команду.

Теперь можно запустить исходный код в экспериментальном экземпляре Visual Studio.

Шаг 1. Нажмите клавишу **F5** , чтобы выполнить команду **начать отладку** . Эта команда выполняет сборку проекта и запускает отладчик, запуская новый экземпляр Visual Studio, который называется **экспериментальным экземпляром**.

::: moniker range="vs-2017"

В строке заголовка Visual Studio вы увидите слова **экспериментальный экземпляр** .

![Строка заголовка экспериментального экземпляра](media/hello-world-exp-instance.png)

::: moniker-end

Шаг 2. В меню **Сервис** **экспериментального экземпляра**щелкните **сказать Hello World!** .

![Окончательный результат](media/hello-world-final-result.png)

Вы должны увидеть выходные данные новой пользовательской команды, в данном случае это диалоговое окно в центре экрана, которое предоставляет **Hello World!** !".

## <a name="next-steps"></a>Следующие шаги

Теперь, когда вы знакомы с основами работы с расширяемостью Visual Studio, здесь можно узнать больше:

* [Начните разрабатывать расширения Visual Studio](starting-to-develop-visual-studio-extensions.md) — примеры, учебники. и публикация расширения
* Новые возможности [пакета SDK для Visual studio 2017](what-s-new-in-the-visual-studio-2017-sdk.md) — новые функции расширяемости в visual Studio 2017
* Новые возможности [пакета SDK для Visual studio 2019](whats-new-visual-studio-2019-sdk.md) — новые функции расширяемости в visual Studio 2019
* В [пакете SDK для Visual Studio](internals/inside-the-visual-studio-sdk.md) — дополнительные сведения о расширяемости Visual Studio
