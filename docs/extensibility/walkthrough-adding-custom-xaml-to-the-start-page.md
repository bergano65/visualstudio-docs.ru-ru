---
title: Пошаговое руководство. Добавление пользовательского XAML начальную страницу | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom start page
- xaml start page
ms.assetid: 9af4d5f9-1cfc-4221-aea7-c8cd3f7571a6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 543faf9cf122e77cce6242f95008b777cd5666b2
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322782"
---
# <a name="walkthrough-add-custom-xaml-to-the-start-page"></a>Пошаговое руководство. Добавление пользовательского XAML на начальную страницу

В этом пошаговом руководстве показано, как создать пользовательский начальной страницы Visual Studio, который содержит веб-браузер.

## <a name="add-custom-xaml"></a>Добавление пользовательского XAML

1. Создание начальной страницы, следуя инструкциям в [Создание настраиваемой начальной страницы](../extensibility/creating-a-custom-start-page.md).

2. В *MainWindow.xaml* найдите \<сетки > раздела.

3. Добавить \<TabControl > элемент и \<TabItem > внутри \< сетки > элемента, как показано в следующем примере.

    ```xml
    <Grid>
        <TabControl>
            <TabItem Header="Bing" Height="Auto">
                <Frame Source="http://www.bing.com" />
            </TabItem>
        </TabControl>
    </Grid>
    ```

4. Добавьте второй \<TabItem >, с помощью \<кнопку > элемент, который открывает новый проект:

    ```xml
    <Grid>
        <TabControl>
            <TabItem Header="MyButton" Height="Auto">
                <Button Name="btnNewProj" Content="New Project"
                    Command="{x:Static vscom:VSCommands.ExecuteCommand}"
                    CommandParameter="File.NewProject" >
                </Button>
            </TabItem>
            <TabItem Header="Bing" Height="Auto">
                <Frame Source="http://www.bing.com" />
            </TabItem>
        </TabControl>
    </Grid>
    ```

## <a name="test-the-custom-start-page"></a>Тестирование настраиваемой начальной страницы

1. Нажмите клавишу **F5**.

     Откроется экспериментальный экземпляр Visual Studio, начальная страница установлена, но не выбраны.

2. В экспериментальном экземпляре Visual Studio, откройте **Tools/Options / среды** страницы.

3. Выберите **запуска**. На **настроить начальную страницу** выберите ваш *.xaml* файла и нажмите кнопку **ОК**.

4. В меню **Вид** выберите пункт **Начальная страница**.

5. Нажмите кнопку **Bing** вкладки.

     Вы увидите веб-странице Bing.

6. Нажмите кнопку **MyButton** вкладки.

     Вы должны увидеть **MyProject** кнопку, чтобы открыть **новый проект** диалоговое окно.

7. Закройте экспериментальный экземпляр.

Чтобы применить настраиваемую начальную страницу, в **средства** > **параметры** > **среды**выберите **запуска**. На **настроить начальную страницу** выберите ваш *.xaml* файла и нажмите кнопку **ОК**.

## <a name="next-steps"></a>Следующие шаги

Начальной страницы Visual Studio теперь содержит вкладку, которая отображает вкладку веб-браузера и MyButton вкладки. Можно создать настраиваемые начальные страницы, которые имеют другие функциональные возможности с помощью *кода* модели для добавления настраиваемой библиотеки DLL, как показано в [Добавление пользовательского элемента управления на начальной странице](../extensibility/adding-user-control-to-the-start-page.md). Настраиваемые начальные страницы можно поделиться с другими пользователями путем публикации полученный файл .vsix в [Visual Studio Marketplace](https://marketplace.visualstudio.com/) веб-сайт или на другой веб-сайт или сети в общую папку. Для получения дополнительной информации см. [Deploying Custom Start Pages](../extensibility/deploying-custom-start-pages.md).

## <a name="see-also"></a>См. также

- [Настройка начальной страницы](../ide/customizing-the-start-page-for-visual-studio.md)
- [Контейнерные элементы управления WPF](https://msdn.microsoft.com/library/a0177167-d7db-4205-9607-8ae316952566)