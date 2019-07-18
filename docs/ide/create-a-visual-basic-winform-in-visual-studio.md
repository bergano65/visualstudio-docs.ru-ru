---
title: Создание приложения Windows Forms на Visual Basic
description: Ознакомьтесь с пошаговыми инструкциями по созданию приложения Windows Forms на Visual Basic в Visual Studio.
ms.date: 03/23/2019
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: 4619a56bfe052a1fb191af8edfd1cef8b376617b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62976849"
---
# <a name="create-a-windows-forms-app-in-visual-studio-with-visual-basic"></a>Создание приложения Windows Forms на Visual Basic в Visual Studio

В рамках этого краткого знакомства с возможностями интегрированной среды разработки Visual Studio (IDE) вы создадите простое приложение на Visual Basic с пользовательским интерфейсом на основе Windows.

::: moniker range="vs-2017"

Установите Visual Studio бесплатно со страницы [скачиваемых материалов Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download), если еще не сделали этого.

::: moniker-end

::: moniker range="vs-2019"

Установите Visual Studio бесплатно со страницы [скачиваемых материалов Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), если еще не сделали этого.

> [!NOTE]
> На некоторых снимках экрана в этом учебнике используется темная тема. Если вы не используете темную тему, но хотите переключиться на нее, см. страницу [Персонализация интегрированной среды разработки и редактора Visual Studio](../ide/quickstart-personalize-the-ide.md).

::: moniker-end

## <a name="create-a-project"></a>Создание проекта

Сначала вы создадите проект приложения Visual Basic. Для этого типа проекта уже имеются все нужные файлы шаблонов, что избавляет вас от лишней работы.

::: moniker range="vs-2017"

1. Откройте Visual Studio 2017.

2. В верхней строке меню последовательно выберите **Файл** > **Создать** > **Проект**.

3. В левой области диалогового окна **Новый проект** разверните узел **Visual Basic** и выберите **Рабочий стол Windows**. На средней панели выберите **Приложение Windows Forms (.NET Framework)**. Назовите файл `HelloWorld`.

     Если шаблон проекта **Приложение Windows Forms (.NET Framework)** отсутствует, закройте диалоговое окно **Новый проект** и в верхней строке меню выберите **Сервис** > **Получить средства и компоненты**. Запускается Visual Studio Installer. Выберите рабочую нагрузку **.Разработка классических приложений .NET** и затем элемент **Изменить**.

     ![Рабочая нагрузка .NET Core в Visual Studio Installer](../ide/media/install-dot-net-desktop-env.png)

::: moniker-end

::: moniker range="vs-2019"

1. Запустите Visual Studio 2019.

1. На начальном экране выберите **Создать проект**.

   ![Просмотр окна "Создание проекта"](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. В поле поиска окна **Создание проекта** введите *Windows Forms*. Затем выберите **Visual Basic** в списке языков и **Windows** в списке платформ. 

   Применив фильтры языка и платформы, выберите шаблон **Приложение Windows Forms (.NET Framework)** и нажмите кнопку **Далее**.

   ![Выбор шаблона Visual Basic для приложения Windows Forms (.NET Framework)](../get-started/visual-basic/media/vs-2019/vb-create-new-project-search-winforms-filtered.png)

   > [!NOTE]
   > Если шаблон **Приложение Windows Forms (.NET Framework)** отсутствует, его можно установить из окна **Создание проекта**. В сообщении **Не нашли то, что искали?** выберите ссылку **Установка других средств и компонентов**.
   >
   > ![Ссылка "Установка других средств и компонентов" из сообщения "Не нашли то, что искали?" в окне "Создание проекта"](../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > После этого в Visual Studio Installer выберите рабочую нагрузку **Разработка классических приложений .NET**.
   > 
   > ![Рабочая нагрузка .NET Core в Visual Studio Installer](../ide/media/install-dot-net-desktop-env.png)
   >
   > Затем нажмите кнопку **Изменить** в Visual Studio Installer. Вам может быть предложено сохранить результаты работы; в таком случае сделайте это. Выберите **Продолжить**, чтобы установить рабочую нагрузку. После этого вернитесь к шагу 2 в процедуре [Создание проекта](#create-a-project).

1. В поле **Имя проекта** окна **Настроить новый проект** введите *HelloWorld*. Затем нажмите **Создать**.

   ![В окне "Настроить новый проект" назовите проект "HelloWorld"](../get-started/visual-basic/media/vs-2019/vb-name-your-winform-project-helloworld.png)

   Новый проект открывается в Visual Studio.

::: moniker-end

## <a name="create-the-application"></a>Создание приложения

Когда вы выберете шаблон проекта Visual Basic и зададите имя файла, Visual Studio открывает форму. Форма является пользовательским интерфейсом Windows. Мы создадим приложение "Hello World", добавив элементы управления на форму, а затем запустим его.

### <a name="add-a-button-to-the-form"></a>Добавление кнопки на форму

1. Щелкните **Панель элементов**, чтобы открыть всплывающее окно "Панель элементов".

     ![Щелкните "Панель элементов", чтобы открыть окно "Панель элементов"](../ide/media/vb-toolbox-toolwindow.png)

     (Если параметр для всплывающего окна **Панель элементов** отсутствует, его можно открыть, нажав клавиши **CTRL**+**ALT**+**X**.)

2. Щелкните значок **Закрепить**, чтобы закрепить окно **Панель элементов**.

     ![Щелкните значок "Закрепить", чтобы закрепить окно "Панель элементов" в интегрированной среде разработки](../ide/media/vb-pin-the-toolbox-window.png)

3. Щелкните элемент управления **Кнопка** и перетащите его на форму.

     ![Добавление кнопки на форму](../ide/media/vb-add-a-button-to-form1.png)

4. В разделе **Внешний вид** (или **Шрифты**) окна **Свойства** введите `Click this` и нажмите клавишу **ВВОД**.

     ![Добавление текста для кнопки на форме](../ide/media/vb-button-control-text.png)

     (Если окно **Свойства** не отображается, его можно открыть в строке меню.) Для этого щелкните **Вид** > **Окно свойств**. Или нажмите клавишу **F4**.)

5. В разделе **Проектирование** окна **Свойства** измените имя с **Button1** на `btnClickThis`, а затем нажмите клавишу **ВВОД**.

     ![Добавление функции для кнопки на форме](../ide/media/vb-button-control-function.png)

### <a name="add-a-label-to-the-form"></a>Добавление метки на форму

Теперь, когда мы добавили элемент управления ''Кнопка'' для создания действия, давайте добавим элемент управления "Метка", куда можно отправлять текст.

1. Выберите элемент управления **Метка** в окне **Панель элементов**, а затем перетащите его на форму и расположите под кнопкой **Нажмите это**.

2. В разделе **Проектирование** окна **Свойства** измените имя с **Label1** на `lblHelloWorld`, а затем нажмите клавишу **ВВОД**.

### <a name="add-code-to-the-form"></a>Добавление кода на форму

1. В окне **Form1.vb &#91;Design&#93;** дважды щелкните кнопку **Нажмите это**, чтобы открыть окно **Form1.vb**.

      (Кроме того, можно развернуть узел **Form1.vb** в **обозревателе решений**, а затем выбрать **Form1**.)

2. В окне **Form1.vb** между строками **Private Sub** и **End Sub** (или между строками **Public Class Form1** и **End Class**) введите следующий код.

     ![Добавление кода на форму](../ide/media/vb-add-code-to-the-form.png)

## <a name="run-the-application"></a>Запуск приложения

1. Нажмите кнопку **Запустить**, чтобы запустить приложение.

     ![Нажмите кнопку "Запустить" для отладки и запуска приложения](../ide/media/vb-click-start-hello-world.png)

   Будет выполнено несколько операций. В интегрированной среде разработки Visual Studio откроются окна **Средства диагностики** и **Вывод**. Кроме того, вне этой среды откроется диалоговое окно **Form1**. Оно будет содержать вашу кнопку **Нажмите это** и текст **Label1**.

2. Нажмите кнопку **Нажмите это** в диалоговом окне **Form1**. Обратите внимание, что текст **Label1** меняется на **Hello World!**.

    ![Диалоговое окно Form1 с текстом Label1 ](../ide/media/vb-form1-dialog-hello-world.png)

Поздравляем с завершением этого краткого руководства! Надеемся, что вы узнали нечто новое о Visual Basic и интегрированной среде разработки Visual Studio. Если вы хотите изучить все более подробно, продолжите работу с руководством из раздела **Руководства** в содержании.

## <a name="see-also"></a>См. также

* [Краткое руководство. Создание консольного приложения на Visual Basic в Visual Studio](quickstart-visual-basic-console.md)
* [Дополнительные сведения об IntelliSense в Visual Basic](visual-basic-specific-intellisense.md)
