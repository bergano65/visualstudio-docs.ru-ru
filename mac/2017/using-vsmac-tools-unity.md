---
title: Применение инструментов Visual Studio для Mac для Unity
description: В этом руководстве описывается использование инструментов Visual Studio для Mac для Unity
author: therealjohn
ms.author: johmil
ms.date: 07/17/2017
ms.assetid: 83FDD7A3-5D16-4B4B-9080-078E3FB5C623
ms.openlocfilehash: d4df59273db1fab8492b36e87e48e0e770072f17
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "89315321"
---
# <a name="using-visual-studio-for-mac-tools-for-unity"></a>Применение инструментов Visual Studio для Mac для Unity

В этом разделе мы рассмотрим, как использовать возможности интеграции и повышения производительности инструментов Visual Studio для Mac для Unity, а также как использовать отладчик Visual Studio для Mac для разработки Unity.

## <a name="opening-unity-scripts-in-visual-studio-for-mac"></a>Открытие скриптов Unity в Visual Studio для Mac

После настройки Visual Studio для Mac [в качестве внешнего редактора скриптов для Unity](setup-vsmac-tools-unity.md#configure-unity-for-use-with-visual-studio-for-mac) открытие любого скрипта в редакторе Unity приводит к автоматическому запуску Visual Studio для Mac с выбранным скриптом.

Кроме того, Visual Studio для Mac можно запустить без открытия скрипта в редакторе исходного кода, выбрав элемент **Открыть проект C#** в меню **Активы** Unity.

![Открытие проекта C#](media/using-vsmac-tools-unity-image1.png)

## <a name="unity-documentation-access"></a>Доступ к документации по Unity

Инструменты Visual Studio для Mac для Unity включают в себя ярлык для доступа к документации по API Unity. Чтобы обратиться к документации по API Unity из Visual Studio для Mac, наведите курсор на соответствующий API Unity и нажмите **⌘ COMMAND+‘** .

## <a name="intellisense-for-unity-messages"></a>IntelliSense для сообщений Unity
Подсистема Unity осуществляет широковещательную передачу сообщений в скрипты MonoBehaviour, позволяя разработчикам писать код, который реагирует на сообщения, такие как OnMouseDown, OnTriggerEnter и т. д. Так как это не виртуальные методы в базовом классе MonoBehaviour, в некоторых IDE, например MonoDevelop, не хватает функций завершения кода для сообщений Unity.

Однако инструменты Visual Studio для Mac для Unity расширяют функциональные возможности IntelliSense для сообщений Unity. Это позволяет легко реализовать сообщения Unity в скриптах MonoBehaviour и помогает в изучении API Unity. Чтобы использовать IntelliSense для сообщений Unity, сделайте следующее:

1. Поместите курсор на новую строку внутри тела класса, производного от MonoBehaviour.

2. Начните вводить имя сообщения Unity, например `OnTriggerEnter`.

3. После ввода букв "**ont**" отображается список предложений IntelliSense.

   ![Using IntelliSense](media/using-vsmac-tools-unity-image2.png)

4. Выбранный элемент в списке можно изменить тремя способами:

   * с помощью клавиш со стрелками **ВВЕРХ** и **ВНИЗ**;

   * щелкая нужный элемент;

   * продолжив ввод имени нужного элемента.

5. IntelliSense может вставить выбранное сообщение Unity, включая все необходимые параметры:

   * при нажатии клавиши **TAB**;

   * при нажатии клавиши **ВВОД**;

   * при двойном щелчке выбранного элемента.

   ![Вставка сообщения Unity из IntelliSense](media/using-vsmac-tools-unity-image3.png)

## <a name="adding-new-unity-files-and-folders"></a>Добавление новых файлов и папок Unity

Хотя вы всегда можете добавить новые файлы в проект Unity с помощью редактора Unity, Visual Studio для Mac позволяет легко создавать новые скрипты, шейдеры и папки Unity с помощью Visual Studio.

### <a name="add-a-new-c-monobehaviour-script"></a>Добавление нового скрипта C# MonoBehaviour

Чтобы добавить новый скрипт C# MonoBehaviour, **щелкните правой кнопкой мыши папку "Активы"** или один из ее подкаталогов на панели решения и выберите **Добавить > Новый MonoBehaviour**.

![Добавление нового MonoBehaviour](media/using-vsmac-tools-unity-image4.png)

### <a name="add-a-new-unity-shader"></a>Добавление нового шейдера Unity

Чтобы добавить новый шейдер Unity, **щелкните правой кнопкой мыши папку "Активы"** или ее подкаталог на панели решения и выберите **Добавить > Новый шейдер**.

### <a name="add-a-new-folder"></a>Добавление новой папки

Чтобы добавить новую папку, **щелкните правой кнопкой мыши папку "Активы"** или ее подкаталог на панели решения и выберите **Добавить > Новая папка**.

Эти добавления отражаются в окне проекта в редакторе Unity.

### <a name="to-rename-a-file-or-folder"></a>Переименование файла или папки
**Щелкните правой кнопкой мыши** элемент, который требуется переименовать, на панели решения и выберите пункт **Переименовать...**

> [!NOTE]
> Если вы работаете с новым проектом Unity без скриптов, а папка "Активы" не отображается на панели решения в Visual Studio для Mac, добавьте из редактора Unity начальный скрипт C#.

## <a name="unity-debugging"></a>Отладка Unity

Отладку проектов Unity можно осуществлять с помощью Visual Studio для Mac.

### <a name="start-debugging"></a>Начать отладку

Начало отладки

1. Подключите Visual Studio к Unity, нажав кнопку **Воспроизвести**, клавиши **COMMAND+ВВОД** или клавишу **F5**.

   ![Нажатие кнопки "Воспроизвести" в Visual Studio](media/using-vsmac-tools-unity-image5.png)

2. Переключитесь в Unity и нажмите кнопку **Воспроизвести**, чтобы запустить игру в редакторе.

   ![Нажатие кнопки "Воспроизвести" в Unity](media/using-vsmac-tools-unity-image6.png)

3. Когда игра запущена в редакторе Unity при подключении к Visual Studio, все проходимые точки останова будут приостанавливать выполнение игры и выводить соответствующую строку кода в Visual Studio для Mac.

### <a name="stop-debugging"></a>Остановка отладки

Чтобы остановить отладку, сделайте следующее:

1. Нажмите кнопку **Остановить** в Visual Studio для Mac или клавиши **SHIFT+COMMAND+ВВОД**.

   ![Нажатие кнопки "Остановить" в Visual Studio](media/using-vsmac-tools-unity-image7.png)

Дополнительные сведения об отладке в Visual Studio для Mac см. в разделе [Использование отладчика](debugging.md).
