---
title: Здравствуй, мир! | Документация Майкрософт
ms.custom: ''
ms.date: 07/10/2017
ms.topic: conceptual
ms.assetid: f74e1ad1-1ee5-4360-9bd5-d82467b884ca
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8a0d5ab3c86c454a547ea80307c5440441424b1c
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2018
ms.locfileid: "39499569"
---
# <a name="create-your-first-extension-hello-world"></a>Создайте свое первое расширение: Hello World

В этом примере Hello World поможет создать свое первое расширение для Visual Studio. Этом учебнике показано, как добавить новую команду в Visual Studio.

В процессе, вы узнаете, как:

* **[Создание проекта расширения](#create-an-extensibility-project)**
* **[Добавление пользовательской команды](#add-a-custom-command)**
* **[Изменить исходный код](#modify-the-source-code)**
* **[Запустите его](#run-it)**

В этом примере вы используете Visual C# для добавления пользовательских меню кнопки с именем «Say Hello World!» Это выглядит следующим образом:

![Команду Hello World](media/hello-world-say-hello-world.png)

## <a name="prerequisites"></a>Предварительные требования

Перед началом работы убедитесь, что вы установили **разработка расширений Visual Studio** рабочей нагрузки, который включает VSIX шаблона, вы должны и пример кода.

Примечание: Можно использовать любую версию Visual Studio (Community, Professional или Enterprise) для создания проекта расширения Visual Studio.

## <a name="create-an-extensibility-project"></a>Создание проекта расширения

Шаг 1. Из **файл** меню, щелкните **новый проект**. В нижней части экрана можно ввести имя проекта.

Шаг 2. Из **шаблоны** меню, щелкните **Visual C#**, нажмите кнопку **расширяемости**, а затем нажмите кнопку **проект VSIX**.

![новый проект](media/hello-world-new-project.png)

Теперь вы увидите страницу Приступая к работе и некоторые примеры ресурсов.

Если вам нужно оставить в этом руководстве и вернитесь к ней, можно найти ваш новый проект Hello World на **начальная страница** в **последние** раздел.

## <a name="add-a-custom-command"></a>Добавление пользовательской команды

Шаг 1. Если выбрать манифест, вы увидите, возможностях, возможность изменения, для экземпляра, метаданные, описание и версии.

Шаг 2. Щелкните правой кнопкой мыши проект (не решение). В контекстном меню, щелкните **добавить**, а затем нажмите кнопку **пользовательский элемент управления**.

Шаг 3. Вернитесь к **расширяемости** раздела и выберите команду **настраиваемой команды**.

Шаг 4. В **имя** в нижней части, присвойте ему имя, например *Command.cs*.

![Пользовательская команда](media/hello-world-custom-command.png)

Вашей новой командой будут перечислены в **обозревателе решений** под **ресурсы** ветви. Это также можно найти другие файлы, относящиеся к вашей команды, например файлы PNG и ICO, если вы хотите изменить образ.

## <a name="modify-the-source-code"></a>Изменить исходный код

На этом этапе вы добавляете кнопки довольно универсальным. Вам придется изменить файл VSCT и CS-файле, если вы хотите внести изменения.

* Файл VSCT является, где вы можно переименовать вашей команды, а также определить, куда в системе команд Visual Studio. При просмотре файла VSCT, можно заметить много комментариями код, чтобы понять какие каждый раздел элементов кода.

* CS-файле является то, где можно определить действия, такие как обработчик щелчка.

Шаг 1. В **обозревателе решений**, найдите файл VSCT для вашей новой командой. В этом случае он будет вызываться *CommandPackage.vsct*.

![команды пакета vsct](media/hello-world-command-package-vsct.png)

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

Шаг 3. Вернитесь к **обозревателе решений** и найти *Command.cs* файла. Изменить строку `message` для команды `string.Format(..)` для `Hello World!`.

```csharp
  ...
  private void MenuItemCallback(object sender, EventArgs e)
  {
    string message = "Hello World!";
    string title = "Command1";

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

Шаг 1. Нажмите кнопку **запустить** на панели инструментов. Это создаст проект и запустите отладчик, запустив новый экземпляр Visual Studio, которые называются **экспериментальный экземпляр**.

Вы увидите слова **экспериментальный экземпляр** в заголовке окна Visual Studio.

![Заголовок экспериментальный экземпляр](media/hello-world-exp-instance.png)

Шаг 2. На **средства** меню **экспериментальный экземпляр**, нажмите кнопку **Say Hello World!**.

![конечный результат](media/hello-world-final-result.png)

Вы должны увидеть выходные данные из вашей новой пользовательской команды, в данном случае в диалоговом окне в центре экрана, позволяющий **Hello World!** !".

## <a name="next-steps"></a>Следующие шаги

Теперь, когда вы знаете основы работы с Visual Studio расширения, Вот где Дополнительные сведения:

* [Приступить к разработке расширений Visual Studio](starting-to-develop-visual-studio-extensions.md) -примеры, учебники. и публикации расширения.
* [Новые возможности в Visual Studio 2017 SDK](what-s-new-in-the-visual-studio-2017-sdk.md) -новые возможности расширяемости в Visual Studio 2017
* [Внутри Visual Studio SDK](internals/inside-the-visual-studio-sdk.md) -подробные сведения о расширении среды Visual Studio