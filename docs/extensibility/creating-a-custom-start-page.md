---
title: Создание пользовательской стартовой страницы (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d67e0c53-9f5a-45fb-a929-b9d2125c3c82
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 3ac0abfe9eedf1c03a8be3bacddbe06ff5698380
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739640"
---
# <a name="creating-a-custom-start-page"></a>Создание пользовательской страницы «Старт»

Вы можете создать пользовательскую стартовую страницу, выдвинув следующие действия в этом документе.

## <a name="create-a-blank-start-page"></a>Создание пустой стартовой страницы

Во-первых, сделать пустую стартовую страницу, создав файл *.xaml,* который имеет структуру тегов, которую распознает Visual Studio. Затем добавьте разметку и код-позади, чтобы создать нужный внешний вид и функциональность.

1. Создайте новый проект типа **приложения WPF** **(Visual C'** > **Windows Desktop**).

2. Добавьте ссылку на `Microsoft.VisualStudio.Shell.14.0`.

3. Откройте файл XAML в редакторе XML \<и измените \<элемент window> верхнего уровня на элемент UserControl> элемент без удаления ни одной из деклараций пространства имен.

4. Удалите декларацию `x:Class` из элемента верхнего уровня. Это делает содержимое XAML совместимым с окном инструмента Visual Studio, в котором размещается Start Page.

5. Добавьте следующие декларации пространства имен \<в элемент пользовательского контроля верхнего уровня>.

    ```vb
    xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
    xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
    ```

     Эти области имен позволяют получить доступ к командам, элементам управления и настройкам uI Visual Studio. Для получения дополнительной информации смотрите [Дополнительные команды Visual Studio на стартовую страницу](../extensibility/adding-visual-studio-commands-to-a-start-page.md).

     Ниже приводится разметка в файле *.xaml* для пустой стартовой страницы. Любое пользовательское содержимое <xref:System.Windows.Controls.Grid> должно идти во внутреннем элементе.

    ```vb
    <UserControl
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:MyNamespace="clr-namespace:ManualStartPage;assembly=ManualStartPage"
        xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
                xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
        xmlns:local="clr-namespace:StartPageHost"
        mc:Ignorable="d"
         Height="350" Width="525">
        <Grid>
        <!--Add content here.-->
        </Grid>
    </UserControl>
    ```

6. Добавьте элемент \<управления в пустой элемент UserControl> для заполнения пользовательской страницы Start Page. Для получения информации о том, как добавить функциональность, которая характерна для Visual Studio, [см.](../extensibility/adding-visual-studio-commands-to-a-start-page.md)

## <a name="test-and-apply-the-custom-start-page"></a>Проверьте и примените пользовательскую страницу Start Page

Не устанавливайте основной экземпляр Visual Studio для запуска пользовательской страницы Start Page до тех пор, пока вы не проверите, что она не разрушит Visual Studio. Вместо этого, проверить его в экспериментальном экземпляре.

### <a name="to-test-a-manually-created-custom-start-page"></a>Для тестирования созданной вручную пользовательской страницы Start Page

1. Копируйте свой файл XAML, а также любые вспомогательные текстовые файлы или файлы разметки, в *"%USERPROFILE%"Мои документы-Visual Studio 2015-StartPages\\ * папку.

2. Если на стартовой странице ссылки на любые элементы управления или типы в сборках, которые не установлены Visual Studio, скопируйте сборки, а затем вставьте их в *папку\\установки Visual Studio.*

3. В команде Visual Studio введите **devenv/rootsuffix Exp,** чтобы открыть экспериментальный экземпляр Visual Studio.

4. В экспериментальном примере перейдите на страницу**запуска**  > **среды** > параметры > **инструментов**и выберите файл XAML из момента отбрасывания **стартовой страницы.** **Tools**

5. В меню **Вид** выберите пункт **Начальная страница**.

     Ваша пользовательская стартовая страница должна отображаться. Если требуется изменить любые файлы, необходимо закрыть экспериментальный экземпляр, внести изменения, скопировать и вставить измененные файлы, а затем повторно открыть экспериментальный экземпляр для просмотра изменений.

### <a name="to-apply-the-custom-start-page-in-the-primary-instance-of-visual-studio"></a>Для применения пользовательской стартовой страницы в основном экземпляре Visual Studio

- После того как вы протестировали страницу start Page и обнаружили, что она стабильна, используйте опцию **Настройка Start Page** в диалоговом поле **Options,** чтобы выбрать ее в качестве стартовой страницы в основном экземпляре Visual Studio

## <a name="see-also"></a>См. также

- [Прохождение: Добавить пользовательский XAML на стартовую страницу](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)
- [Добавление элемента управления пользователем в страницу «Старт»](../extensibility/adding-user-control-to-the-start-page.md)
- [Добавление команд Visual Studio в стартовую страницу](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
- [Прохождение: Сохранение настроек пользователя на стартовой странице](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)
- [Развертывание пользовательских страниц запуска](../extensibility/deploying-custom-start-pages.md)
