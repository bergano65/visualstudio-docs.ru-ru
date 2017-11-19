---
title: "Здравствуй, мир! | Документы Microsoft"
ms.custom: 
ms.date: 07/10/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f74e1ad1-1ee5-4360-9bd5-d82467b884ca
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 18a0e18589574c689ebbddbaf28448cf5539ad96
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="creating-your-first-extension-hello-world"></a>Создание первого расширение: Hello World

В этом примере Hello World руководство по созданию вашей первой расширения для Visual Studio. Этого учебника показано, как добавить к ней новой команды в Visual Studio.

В процессе, вы узнаете, как:

* **[Создание проекта расширения](#create-an-extensibility-project)**
* **[Добавление пользовательской команды](#add-a-custom-command)**
* **[Изменить исходный код](#modify-the-source-code)**
* **[Запустите его](#run-it)**

В этом примере используется Visual C#, чтобы добавить пользовательскую кнопку с именем «Say Hello World!» выглядит следующим образом:

![Команда Hello world](media/hello-world-say-hello-world.png)

## <a name="prerequisites"></a>Предварительные требования

Прежде чем начать, убедитесь, что вы установили **разработки расширения Visual Studio** рабочей нагрузки, который включает VSIX шаблон будет нужно и пример кода.

Примечание: Можно использовать любой версии Visual Studio (Community, Professional или Enterprise) для создания проекта расширения среды Visual Studio.

## <a name="create-an-extensibility-project"></a>Создание проекта расширения

Шаг 1. Из **файл** меню, нажмите кнопку **новый проект**. В нижней части экрана можно ввести имя проекта.

Шаг 2. Из **шаблоны** меню, нажмите кнопку **Visual C#**, нажмите кнопку **расширяемости**, а затем нажмите кнопку **проект VSIX**.

![новый проект](media/hello-world-new-project.png)

Теперь вы увидите некоторые ресурсы примеров и странице начала работы.

Если необходимо оставить этот учебник и вернуться к нему нового проекта HelloWorld можно найти на **начальной страницы** в **последние** раздела.

## <a name="add-a-custom-command"></a>Добавление пользовательской команды

Шаг 1. При выборе манифеста, вы увидите, какие параметры упоминаемое для экземпляра, метаданных, описание и версии.

Шаг 2. Щелкните правой кнопкой мыши проект (не решения). В контекстном меню выберите **добавить**, а затем нажмите кнопку **пользовательский элемент управления**.

Шаг 3. Вернитесь к **расширяемости** , а затем выберите **настраиваемой команды**.

Шаг 4. В **имя** в нижней части, присвойте ему имя, например Command.cs.

![пользовательские команды](media/hello-world-custom-command.png)

Вашей новой командой будут перечислены в **обозревателе решений** под **ресурсов** ветви. Это также можно найти другие файлы, связанные с вашей команды, например файлы PNG и ICO, если вы хотите изменить изображение.

## <a name="modify-the-source-code"></a>Изменить исходный код

На этом этапе вы добавляете кнопки является довольно универсальным. Необходимо изменить в VSCT-файле и CS-файл, если вы хотите внести изменения.

* VSCT-файла — где вы можно переименовать вашей команды, а также определить, куда в систему команд Visual Studio. При просмотре файла VSCT, вы увидите много закомментированный код, объясняющий какие каждый раздел код элементов управления.

* Файл CS —, где можно определить действия, такие как обработчик щелчка.

Шаг 1. В **обозревателе решений**, найдите файл VSCT для вашей новой командой. В этом случае он будет вызван CommandPackage.vsct.

![Команда vsct пакета](media/hello-world-command-package-vsct.png)

Шаг 2. Изменение `ButtonText` параметр «Say Hello World!»

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

Шаг 3. Вернитесь к **обозревателе решений** и найти файл Command.cs. Изменить строку `message` команды `string.Format(..)` «Hello World!»

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

Теперь можно запустить код в экспериментальном экземпляре Visual Studio.

Шаг 1. Нажмите кнопку **запуска** на панели инструментов. Это построение проекта и запустите отладчик, запуска нового экземпляра Visual Studio при вызове **экспериментальный экземпляр**.

Вы увидите слова «Экспериментальный экземпляр» в заголовке окна Visual Studio.

![экспериментальный экземпляр заголовка](media/hello-world-exp-instance.png)

Шаг 2. На **средства** меню **экспериментальный экземпляр**, нажмите кнопку **Say Hello World!**.

![конечный результат](media/hello-world-final-result.png)

Вы увидите выходные данные из вашей новой пользовательской команды в этом случае окно в центре экрана, который дает «Hello World!» !".

## <a name="next-steps"></a>Следующие шаги

Теперь, когда вы знаете основы работы с Visual Studio расширения, вот, где можно узнать больше.

* [Начало разработки расширений Visual Studio](starting-to-develop-visual-studio-extensions.md) -примеры, учебники. и публикации расширения.
* [Новые возможности Visual Studio SDK 2017 г.](what-s-new-in-the-visual-studio-2017-sdk.md) -новых возможностей расширяемости Visual Studio 2017 г.
* [Внутри Visual Studio SDK](internals/inside-the-visual-studio-sdk.md) -подробные сведения о расширении среды Visual Studio