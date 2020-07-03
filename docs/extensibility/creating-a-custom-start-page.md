---
title: Создание настраиваемой начальной страницы | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d67e0c53-9f5a-45fb-a929-b9d2125c3c82
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: ed35948158866b7d0bbb2e458c8f8bc2f7b3f844
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903678"
---
# <a name="creating-a-custom-start-page"></a>Создание настраиваемой начальной страницы

Вы можете создать настраиваемую начальную страницу, выполнив действия, описанные в этом документе.

## <a name="create-a-blank-start-page"></a>Создать пустую начальную страницу

Сначала создайте пустую начальную страницу, создав *XAML* -файл с структурой тегов, которую будет распознать Visual Studio. Затем добавьте разметку и код программной части, чтобы получить необходимый внешний вид и функциональность.

1. Создайте новый проект типа **приложение WPF** (**Visual C#**  >  **Windows Desktop**).

2. Добавьте ссылку на `Microsoft.VisualStudio.Shell.14.0`.

3. Откройте XAML-файл в редакторе XML и измените элемент верхнего уровня \<Window> на \<UserControl> элемент без удаления каких-либо объявлений пространств имен.

4. Удалите `x:Class` объявление из элемента верхнего уровня. Это делает содержимое XAML совместимым с окном инструментов Visual Studio, в котором размещается Начальная страница.

5. Добавьте следующие объявления пространств имен в элемент верхнего уровня \<UserControl> .

    ```vb
    xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
    xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
    ```

     Эти пространства имен позволяют получать доступ к командам, элементам управления и параметрам пользовательского интерфейса Visual Studio. Дополнительные сведения см. [в разделе Добавление команд Visual Studio на начальную страницу](../extensibility/adding-visual-studio-commands-to-a-start-page.md).

     В следующем примере показана разметка в *XAML* -файле для пустой начальной страницы. Любое пользовательское содержимое должно проходить во внутреннем <xref:System.Windows.Controls.Grid> элементе.

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

6. Добавьте элементы управления в пустой \<UserControl> элемент, чтобы заполнить настраиваемую начальную страницу. Дополнительные сведения о добавлении функций, характерных для Visual Studio, см. [в разделе Добавление команд Visual Studio на начальную страницу](../extensibility/adding-visual-studio-commands-to-a-start-page.md).

## <a name="test-and-apply-the-custom-start-page"></a>Тестирование и применение настраиваемой начальной страницы

Не устанавливайте основной экземпляр Visual Studio для запуска настраиваемой начальной страницы, пока не убедитесь, что она не выполняет аварийное завершение работы Visual Studio. Вместо этого протестируйте его в экспериментальном экземпляре.

### <a name="to-test-a-manually-created-custom-start-page"></a>Тестирование пользовательской начальной страницы, созданной вручную

1. Скопируйте файл XAML и все вспомогательные текстовые файлы или файлы разметки в папку *%UserProfile%\My Documents\Visual Studio 2015 \ startpages \\ * .

2. Если начальная страница ссылается на любые элементы управления или типы в сборках, которые не установлены в Visual Studio, скопируйте эти сборки и вставьте их в *{Папка установки Visual Studio \\ } \Common7\IDE\PrivateAssemblies*.

3. В командной строке Visual Studio введите команду **devenv/Рутсуффикс exp** , чтобы открыть экспериментальный экземпляр Visual Studio.

4. В экспериментальном экземпляре перейдите на страницу **Сервис**  >  **Параметры**  >  **Среда**  >  **Startup** и выберите файл XAML в раскрывающемся списке **настроить начальную страницу** .

5. В меню **Вид** выберите пункт **Начальная страница**.

     Должна отобразиться настраиваемая Начальная страница. Если вы хотите изменить какие-либо файлы, необходимо закрыть экспериментальный экземпляр, внести изменения, скопировать и вставить измененные файлы, а затем повторно открыть экспериментальный экземпляр для просмотра изменений.

### <a name="to-apply-the-custom-start-page-in-the-primary-instance-of-visual-studio"></a>Применение настраиваемой начальной страницы в основном экземпляре Visual Studio

- После проверки начальной страницы и обнаружения ее стабильности используйте параметр **настроить начальную страницу** в диалоговом окне **Параметры** , чтобы выбрать его в качестве начальной страницы в основном экземпляре Visual Studio.

## <a name="see-also"></a>Дополнительно

- [Пошаговое руководство. Добавление пользовательского XAML-кода на начальную страницу](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)
- [Добавление пользовательского элемента управления на начальную страницу](../extensibility/adding-user-control-to-the-start-page.md)
- [Добавление команд Visual Studio на начальную страницу](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
- [Пошаговое руководство. Сохранение параметров пользователя на начальной странице](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)
- [Развертывание настраиваемых начальных страниц](../extensibility/deploying-custom-start-pages.md)
