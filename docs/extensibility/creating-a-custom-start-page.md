---
title: Создание настраиваемой начальной страницы | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d67e0c53-9f5a-45fb-a929-b9d2125c3c82
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 96b1d55ee31c08f51ab62e799dac843fff55fb67
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54997888"
---
# <a name="creating-a-custom-start-page"></a>Создание настраиваемой начальной страницы
Настраиваемой начальной страницы можно создать, выполнив действия, описанные в этом документе.  
  
## <a name="create-a-blank-start-page"></a>Создание пустой начальной страницы  
 Во-первых, обеспечить пустую начальную страницу с помощью создания *.xaml* файл, который имеет структуру тег, который Visual Studio распознает. Затем добавьте разметки и кода для создания внешний вид и функциональность.  
  
### <a name="to-create-a-blank-start-page"></a>Чтобы создать пустую начальную страницу  
  
1.  Создайте новый проект типа **приложение WPF** (**Visual C#** > **Windows Desktop**).  
  
2.  Добавьте ссылку на `Microsoft.VisualStudio.Shell.14.0`.  
  
3.  Откройте файл XAML в редакторе XML и измените верхнего уровня \<окна > элемент \<UserControl > элемента без удаления любой из объявления пространств имен.  
  
4.  Удалить `x:Class` объявление из элемента верхнего уровня. Это обеспечивает совместимость с окном инструментов Visual Studio, на котором размещена начальная страница содержимого XAML.  
  
5.  Добавьте следующие объявления пространств имен верхнего уровня \<UserControl > элемента.  
  
    ```vb  
    xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
    xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
    ```  
  
     Эти пространства имен позволяют получить доступ к команд Visual Studio, элементы управления и параметры пользовательского интерфейса. Дополнительные сведения см. в разделе [команд Visual Studio, добавьте начальную страницу](../extensibility/adding-visual-studio-commands-to-a-start-page.md).  
  
     В следующем примере показано разметки в *.xaml* файл для пустой начальной страницы. Любое пользовательское содержимое должны перейти во внутреннем <xref:System.Windows.Controls.Grid> элемент.  
  
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
  
6.  Добавление элементов управления на пустой \<UserControl > элемент для заполнения в вашей настраиваемой начальной страницы. Сведения о том, как добавить функциональные возможности, относящиеся к Visual Studio, см. в разделе [команд Visual Studio, добавьте начальную страницу](../extensibility/adding-visual-studio-commands-to-a-start-page.md).  
  
## <a name="test-and-apply-the-custom-start-page"></a>Тестирование и применение настраиваемой начальной страницы  
 Не устанавливайте основной экземпляр Visual Studio для выполнения настраиваемой начальной страницы, пока не убедитесь, что она работает без сбоев Visual Studio. Вместо этого проверьте его в экспериментальном экземпляре.  
  
### <a name="to-test-a-manually-created-custom-start-page"></a>Чтобы проверить, созданных вручную настраиваемой начальной страницы  
  
1.  Скопируйте файл XAML и все вспомогательные текстовые файлы или разметки файлы, к *%USERPROFILE%\My Documents\Visual Studio 2015\StartPages\\*  папки.  
  
2.  Если начальная страница ссылается на все элементы или типы в сборках, которые не установлены в Visual Studio, скопируйте сборки, а затем вставьте их в *\Common7\IDE\PrivateAssemblies {папка установки Visual Studio}\\* .  
  
3.  В командной строке Visual Studio, введите **devenv/rootsuffix Exp** открыть экспериментальный экземпляр Visual Studio.  
  
4.  В экспериментальном экземпляре выберите **средства** > **параметры** > **среды** > **запуска** страницы и выберите свой файл XAML из **настроить начальную страницу** раскрывающегося списка.  
  
5.  В меню **Вид** выберите пункт **Начальная страница**.  
  
     Отображать пользовательской начальной страницы. Если вы хотите изменить любые файлы, необходимо закрыть экспериментальный экземпляр, внесите изменения, скопируйте и вставьте измененных файлов и повторно открыть экспериментальный экземпляр, чтобы просмотреть изменения.  
  
### <a name="to-apply-the-custom-start-page-in-the-primary-instance-of-visual-studio"></a>Чтобы применить пользовательский начальной страницы в основном экземпляре Visual Studio  
  
-   После тестирования к начальной странице и найти его, чтобы быть нестабильным, использовать **настроить начальную страницу** в диалоговом окне **параметры** диалоговое окно, чтобы выбрать ее в качестве начальной страницы в основном экземпляре Visual Studio  
  
## <a name="see-also"></a>См. также  
 [Пошаговое руководство: Добавление пользовательского XAML начальной страницы](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)   
 [Добавить пользовательский элемент управления на начальную страницу](../extensibility/adding-user-control-to-the-start-page.md)   
 [Добавление команд Visual Studio для начальной страницы](../extensibility/adding-visual-studio-commands-to-a-start-page.md)   
 [Пошаговое руководство: Сохранить настройки пользователя на начальной странице](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)   
 [Развернуть настраиваемые начальные страницы](../extensibility/deploying-custom-start-pages.md)