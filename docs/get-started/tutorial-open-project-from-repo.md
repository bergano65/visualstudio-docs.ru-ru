---
title: Учебник. Открытие проекта из репозитория
description: Сведения об открытии проекта из репозитория Git или Azure DevOps с помощью Visual Studio.
ms.custom: get-started
ms.date: 03/30/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b1796ca10226e4aa5d0242bea89cc01f8452cf9e
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/30/2019
ms.locfileid: "66402076"
---
# <a name="tutorial-open-a-project-from-a-repo"></a>Учебник. Открытие проекта из репозитория

В этом руководстве вы примените Visual Studio для первичного подключения к репозиторию и открытия проекта.

::: moniker range="vs-2017"

Установите Visual Studio бесплатно со страницы [скачиваемых материалов Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download), если еще не сделали этого.

::: moniker-end

::: moniker range="vs-2019"

Установите Visual Studio бесплатно со страницы [скачиваемых материалов Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), если еще не сделали этого.

::: moniker-end

## <a name="open-a-project-from-a-github-repo"></a>Открытие проекта из репозитория GitHub

::: moniker range="vs-2017"

1. Откройте Visual Studio 2017.

1. В верхней строке меню выберите **Файл** > **Открыть** > **Открыть из системы управления версиями**.

   Откроется **панель подключения к Team Explorer**.

    ![Окно Team Explorer в интегрированной среде разработки Visual Studio](./media/open-proj-repo-team-explorer.png)

1. В разделе **Локальные репозитории Git** выберите действие **Клонировать**.

    ![Выбор действия клонирования из раздела локальных репозиториев Git](./media/open-proj-repo-local-git-repo-clone.png)

1. В поле с текстом ***Enter the URL of a Git repo to clone*** (Введите URL-адрес клонируемого репозитория Git) введите или вставьте URL-адрес нужного репозитория и нажмите клавишу **ВВОД**. (Если появится запрос на вход в GitHub, выполните его.)

   Завершив клонирование репозитория, Visual Studio закрывает Team Explorer и открывает обозреватель решений. Появится сообщение *Click on Solutions and Folders above to view a list of Solutions* (Щелкните выше "Решения и папки", чтобы просмотреть список решений). Щелкните **Решения и папки**.

   ![Выбор представления "Решения и папки" в обозревателе решений](./media/open-proj-repo-github-solutions-folders.png)

1. Если у вас есть файл решения, он будет отображаться в раскрывающемся меню "Решения и папки". Выберите его, и Visual Studio откроет нужное решение.

   ![Выбор элемента для отображения из раскрывающегося списка в обозревателе решений](./media/open-proj-repo-github-solutions-folders-picker.png)

   Если в используемом репозитории нет файла решения (SLN-файла), раскрывающееся меню будет содержать текст No Solutions Found (Решение не найдено). Но вы можете дважды щелкнуть любой файл в меню папок, чтобы открыть этот файл в редакторе кода Visual Studio.

### <a name="review-your-work"></a>Проверка работы

Просмотрите следующую анимацию для проверки работы, выполненной в предыдущем разделе.

   ![Анимация открытия проекта из репозитория GitHub с помощью Visual Studio](./media/open-project-from-github.gif)

::: moniker-end

::: moniker range="vs-2019"

1. Запустите Visual Studio 2019.

1. В начальном окне выберите **Клонировать или извлечь без кода**.

   ![Просмотр окна "Создание проекта"](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. Введите или укажите расположение репозитория и выберите **Клонировать**.

   ![Просмотр окна "Клонирование или извлечение кода"](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Visual Studio откроет проект из репозитория.

1. Если у вас есть файл решения, он будет отображаться в раскрывающемся меню "Решения и папки". Выберите его, и Visual Studio откроет нужное решение.

   ![Выбор элемента для отображения из раскрывающегося списка в обозревателе решений](./media/open-proj-repo-github-solutions-folders-picker.png)

   Если в используемом репозитории нет файла решения (SLN-файла), раскрывающееся меню будет содержать текст No Solutions Found (Решение не найдено). Но вы можете дважды щелкнуть любой файл в меню папок, чтобы открыть этот файл в редакторе кода Visual Studio.

::: moniker-end

## <a name="open-a-project-from-an-azure-devops-repo"></a>Открытие проекта из репозитория Azure DevOps

::: moniker range="vs-2017"

1. Откройте Visual Studio 2017.

1. В верхней строке меню выберите **Файл** > **Открыть** > **Открыть из системы управления версиями**.

   Откроется **панель подключения к Team Explorer**.

    ![Окно Team Explorer в интегрированной среде разработки Visual Studio](./media/open-proj-repo-team-explorer.png)

1. Ниже описаны два способа подключиться к репозиторию Azure DevOps.

      - В разделе **Hosted Service Providers** (Поставщики размещенных служб) выберите **Connect...**  (Подключиться...).

        ![Раздел поставщиков размещенных служб в окне Team Explorer интегрированной среды разработки Visual Studio](./media/open-proj-repo-azure-devops.png)

      - В раскрывающемся списке **Управление соединениями** выберите **Подключиться к проекту...** .

        ![Раздел управления соединениями в окне Team Explorer интегрированной среды разработки Visual Studio](./media/open-proj-repo-azuredevops-manage-connections.png)

1. В диалоговом окне **Подключение к проекту** выберите репозиторий, к которому вы хотите подключиться, а затем щелкните **Клонировать**.

      ![Диалоговое окно "Подключение к проекту", созданное в Visual Studio](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > Содержимое этого списка зависит от того, какие репозитории Azure DevOps вам доступны.

1. Завершив клонирование репозитория, Visual Studio закрывает Team Explorer и открывает обозреватель решений. Появится сообщение *Click on Solutions and Folders above to view a list of Solutions* (Щелкните выше "Решения и папки", чтобы просмотреть список решений). Щелкните **Решения и папки**.

      ![Уведомление "Решения и папки" от Team Explorer в Visual Studio](./media/open-proj-repo-solutions-folders.png)

   Файл решения (SLN-файл) будет отображаться в раскрывающемся меню "Решения и папки". Выберите его, и Visual Studio откроет нужное решение.

   Если в используемом репозитории нет файла решения, раскрывающееся меню будет содержать текст No Solutions Found (Решение не найдено). Но вы можете дважды щелкнуть любой файл в меню папок, чтобы открыть этот файл в редакторе кода Visual Studio.

::: moniker-end

::: moniker range="vs-2019"

1. Запустите Visual Studio 2019.

1. В начальном окне выберите **Клонировать или извлечь без кода**.

   ![Просмотр окна "Создание проекта"](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. В разделе **Обзор репозитория** выберите **Azure DevOps**.

   ![Просмотр окна "Клонирование или извлечение кода"](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Если появится окно входа, войдите в свою учетную запись.

1. В диалоговом окне **Подключение к проекту** выберите репозиторий, к которому вы хотите подключиться, а затем щелкните **Клонировать**.

      ![Диалоговое окно "Подключение к проекту", созданное в Visual Studio](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > Содержимое этого списка зависит от того, какие репозитории Azure DevOps вам доступны.

   Visual Studio открывает **Team Explorer**, и после завершения клонирования появится уведомление.

     ![Окно Team Explorer в Visual Studio после завершения клонирования](./media/vs-2019/clone-complete-azure-devops.png)

1. Чтобы просмотреть папки и файлы, нажмите на ссылку **Показать представление папки**.

     ![Раздел "Решения" в окне Team Explorer в Visual Studio после завершения клонирования](./media/vs-2019/show-folder-view-azure-devops.png)

     Visual Studio откроет **обозреватель решений**.

1. Нажмите на ссылку **Решения и папки**, чтобы найти файл решения (SLN-файл), который нужно открыть.

      ![Уведомление "Решения и папки" от Team Explorer в Visual Studio](./media/open-proj-repo-solutions-folders.png)

   Если в используемом репозитории нет файла решения, появится сообщение "Решение не найдено". Но вы можете дважды щелкнуть любой файл в меню папок, чтобы открыть этот файл в редакторе кода Visual Studio.

::: moniker-end

## <a name="next-steps"></a>Следующие шаги

Если вы готовы создавать код в Visual Studio, переходите к любому из следующих учебников по конкретным языкам:

- [Учебники по Visual Studio | **C#** ](./csharp/index.yml)
- [Учебники по Visual Studio | **Visual Basic**](./visual-basic/index.yml)
- [Учебники по Visual Studio | **C++** ](/cpp/get-started/tutorial-console-cpp)
- [Учебники по Visual Studio | **Python**](/visualstudio/python/)
- [Учебники по Visual Studio | **JavaScript**, **TypeScript** и **Node.js**](/visualstudio/javascript/)

## <a name="see-also"></a>См. также

- [Azure DevOps Services: Get started with Azure Repos and Visual Studio](/azure/devops/repos/git/gitquickstart/) (Azure DevOps Services. Начало работы с Azure Repos и Visual Studio)
- [Microsoft Learn. Начало работы с Azure DevOps](/learn/modules/get-started-with-devops/)