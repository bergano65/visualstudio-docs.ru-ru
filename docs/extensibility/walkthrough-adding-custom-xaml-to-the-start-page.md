---
title: 'Прохождение: Добавление пользовательских XAML на стартовую страницу (ru) Документы Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom start page
- xaml start page
ms.assetid: 9af4d5f9-1cfc-4221-aea7-c8cd3f7571a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 4e2afc90dc96978e8a8290afaa2d3278e8b621b3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697678"
---
# <a name="walkthrough-add-custom-xaml-to-the-start-page"></a>Прохождение: Добавить пользовательский XAML на стартовую страницу

В этом пошаговом показании, как создать пользовательскую стартовую страницу Visual Studio, содержащую веб-браузер.

## <a name="add-custom-xaml"></a>Добавить пользовательский XAML

1. Создайте стартовую страницу, следуя инструкциям в [Создать пользовательскую стартовую страницу.](../extensibility/creating-a-custom-start-page.md)

2. В файле *MainWindow.xaml* \<найдите раздел Grid>.

3. Добавьте \<элемент> TabControl и \<> \< TabItem внутри элемента сетки>, как показано в следующем примере.

    ```xml
    <Grid>
        <TabControl>
            <TabItem Header="Bing" Height="Auto">
                <Frame Source="http://www.bing.com" />
            </TabItem>
        </TabControl>
    </Grid>
    ```

4. Добавьте \<вторую> TabItem с элементом \<> кнопки, который открывает новый проект:

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

## <a name="test-the-custom-start-page"></a>Проверьте пользовательскую страницу запуска

1. Нажмите клавишу **F5**.

     Экспериментальный экземпляр Visual Studio открывается, с пользовательской стартовой страницы установлен, но не выбран.

2. В экспериментальном экземпляре Visual Studio откройте страницу **«Инструменты/Варианты / Окружающая среда».**

3. Выберите **запуск**. В списке **настраиваемых стартовых страниц** выберите файл *.xaml* и **нажмите OK.**

4. В меню **Вид** выберите пункт **Начальная страница**.

5. Нажмите на вкладку **Bing.**

     Вы должны увидеть веб-страницу Bing.

6. Нажмите на вкладку **MyButton.**

     Вы должны увидеть кнопку **MyProject,** которая открывает диалог **нового проекта.**

7. Закройте экспериментальный экземпляр.

Чтобы применить пользовательскую страницу запуска, в**среде****параметры** >  **инструментов** > , выберите **Запуск**. В списке **настраиваемых стартовых страниц** выберите файл *.xaml* и **нажмите OK.**

## <a name="next-steps"></a>Следующие шаги

Стартовая страница Visual Studio теперь содержит вкладку, которая отображает вкладку веб-браузера и вкладку MyButton. Вы можете создать пользовательские стартовые страницы, которые имеют другие функциональные возможности, используя модель *сзади кода,* чтобы добавить пользовательский .dll, как показано в [добавлении управления пользователем на стартовую страницу.](../extensibility/adding-user-control-to-the-start-page.md) Вы можете поделиться пользовательскими стартовыми страницами с другими пользователями, опубликовав полученный файл .vsix на веб-узел [Visual Studio Marketplace](https://marketplace.visualstudio.com/) или на другой веб-узел или общую сеть. Для получения дополнительной информации см. [Deploying Custom Start Pages](../extensibility/deploying-custom-start-pages.md).

## <a name="see-also"></a>См. также

- [Настройка стартовой страницы](../ide/customizing-the-start-page-for-visual-studio.md)
- [Контроль контейнеров WPF](https://msdn.microsoft.com/library/a0177167-d7db-4205-9607-8ae316952566)
