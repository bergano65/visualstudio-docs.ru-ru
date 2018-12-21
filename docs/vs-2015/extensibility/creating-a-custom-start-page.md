---
title: Создание настраиваемой начальной страницы | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d67e0c53-9f5a-45fb-a929-b9d2125c3c82
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 87f653a6ac745253ae86eb6bf8dfab92169ac4db
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51806065"
---
# <a name="creating-a-custom-start-page"></a>Создание настраиваемой начальной страницы
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Если не удается создать настраиваемой начальной страницы с помощью шаблона проекта начальной страницы, как описано в разделе [начальных страниц](../misc/creating-your-own-start-page.md), можно вручную создать его, выполнив следующие действия, описанные в этом документе.  
  
## <a name="creating-a-blank-start-page"></a>Создание пустой начальной страницы  
 Во-первых обеспечить пустую начальную страницу с помощью создания XAML-файл, который имеет структуру тег, который Visual Studio распознает. Затем добавьте разметки и кода для создания внешний вид и функциональность.  
  
#### <a name="to-create-a-blank-start-page"></a>Чтобы создать пустую начальную страницу  
  
1.  Создайте новый проект типа **приложение WPF** (**Visual C# / рабочий стол Windows**.  
  
2.  Добавьте ссылку на `Microsoft.VisualStudio.Shell.14.0`.  
  
3.  Откройте файл XAML в редакторе XML и измените верхнего уровня \<окна > элемент \<UserControl > элемента без удаления любой из объявления пространств имен.  
  
4.  Удалить `x:Class` объявление из элемента верхнего уровня. Это делает содержимое XAML, совместимым с окна инструментов Visual Studio, на котором размещена начальной страницы.  
  
5.  Добавьте следующие объявления пространств имен верхнего уровня \<UserControl > элемента.  
  
    ```  
    xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
    xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
    ```  
  
     Эти пространства имен позволяют получить доступ к команд Visual Studio, элементы управления и параметры пользовательского интерфейса. Дополнительные сведения см. в разделе [добавление к начальной странице команды на Visual Studio](../extensibility/adding-visual-studio-commands-to-a-start-page.md).  
  
     В следующем примере показана разметка в XAML-файл для пустой начальной страницы. Любое пользовательское содержимое должны перейти во внутреннем <xref:System.Windows.Controls.Grid> элемент.  
  
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
  
6.  Добавление элементов управления на пустой \<UserControl > элемент для заполнения в вашей настраиваемой начальной страницы. Сведения о том, как добавить функциональные возможности, относящиеся к Visual Studio, см. в разделе [добавление к начальной странице команды на Visual Studio](../extensibility/adding-visual-studio-commands-to-a-start-page.md).  
  
## <a name="testing-and-applying-the-custom-start-page"></a>Тестирование и применение настраиваемой начальной страницы  
 Не устанавливайте основной экземпляр Visual Studio для выполнения настраиваемой начальной страницы, пока не убедитесь, что она работает без сбоев Visual Studio. Вместо этого проверьте его в экспериментальном экземпляре.  
  
#### <a name="to-test-a-manually-created-custom-start-page"></a>Для тестирования созданного вручную настраиваемой начальной страницы  
  
1.  Скопируйте файл XAML и все вспомогательные текстовые файлы или разметки файлы, к **%USERPROFILE%\My Documents\Visual Studio 2015\StartPages\\**  папки.  
  
2.  Если начальная страница ссылается на все элементы или типы в сборках, которые не установлены в Visual Studio, скопируйте сборки, а затем вставьте их в _папка установки Visual Studio_**\Common7\IDE\ PrivateAssemblies\\**.  
  
3.  В командной строке Visual Studio, введите **devenv/rootsuffix Exp** открыть экспериментальный экземпляр Visual Studio.  
  
4.  В экспериментальном экземпляре выберите **Сервис / Параметры / Среда / запуска** страницы и выберите свой файл XAML из **настроить начальную страницу** раскрывающегося списка.  
  
5.  В меню **Вид** выберите пункт **Начальная страница**.  
  
     Отображать пользовательской начальной страницы. Если вы хотите изменить любые файлы, необходимо закрыть экспериментальный экземпляр, внесите изменения, скопируйте и вставьте измененных файлов и повторно открыть экспериментальный экземпляр, чтобы просмотреть изменения.  
  
#### <a name="to-apply-the-custom-start-page-in-the-primary-instance-of-visual-studio"></a>Чтобы применить пользовательский начальной страницы в основном экземпляре Visual Studio  
  
-   После тестирования к начальной странице и найти его, чтобы быть нестабильным, использовать **настроить начальную страницу** в диалоговом окне **параметры** диалоговое окно, чтобы выбрать ее в качестве начальной страницы в основном экземпляре Visual Studio  
  
## <a name="see-also"></a>См. также  
 [Пошаговое руководство: Добавление пользовательского XAML начальной страницы](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)   
 [Добавление пользовательского элемента управления на начальную страницу](../extensibility/adding-user-control-to-the-start-page.md)   
 [Добавление команд Visual Studio на начальную страницу](../extensibility/adding-visual-studio-commands-to-a-start-page.md)   
 [Пошаговое руководство: Сохранение пользовательских параметров на начальной странице](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)   
 [Развертывание настраиваемой начальной страницы](../extensibility/deploying-custom-start-pages.md)

