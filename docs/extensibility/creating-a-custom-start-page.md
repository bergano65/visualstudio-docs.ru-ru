---
title: "Создание пользовательской начальной страницы | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d67e0c53-9f5a-45fb-a929-b9d2125c3c82
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: c358bf79945b4f4eef5b19c60cad0bd866c175b3
ms.openlocfilehash: 2902ac3b5cd4fd038bdaf277a8390d5eb9e96b28
ms.lasthandoff: 02/22/2017

---
# <a name="creating-a-custom-start-page"></a>Создание настраиваемой начальной страницы
На пользовательской странице можно создать, выполнив действия, описанные в этом документе.  
  
## <a name="creating-a-blank-start-page"></a>Создание пустой начальной страницы  
 Во-первых сделайте пустым начальной страницы, создав XAML-файл, который имеет структуру тегов, Visual Studio распознает. Затем добавьте разметки и кода для создания внешний вид и функциональность.  
  
#### <a name="to-create-a-blank-start-page"></a>Чтобы создать пустой начальной страницы  
  
1.  Создайте новый проект типа **приложение WPF** (**Visual C# / рабочий стол Windows**.  
  
2.  Добавьте ссылку на `Microsoft.VisualStudio.Shell.14.0`.  
  
3.  Откройте XAML-файл в редакторе XML и измените верхнего уровня \<окна настроек элемента \<UserControl настроек элемента без удаления любого объявления пространств имен.  
  
4.  Удалить `x:Class` объявление из элемента верхнего уровня. Это обеспечивает совместимость с окном инструментов Visual Studio, на котором размещается начальной страницы содержимого XAML.  
  
5.  Добавьте следующие объявления пространств имен верхнего уровня \<UserControl настроек элемента.  
  
    ```  
    xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
    xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
    ```  
  
     Эти пространства имен позволяют обращаться к команд Visual Studio, элементы управления и настройки пользовательского интерфейса. Дополнительные сведения см. в разделе [Добавление команды Visual Studio предоставляют начальную страницу](../extensibility/adding-visual-studio-commands-to-a-start-page.md).  
  
     В следующем примере показана разметка в XAML-файл пустая страница запуска. Любое пользовательское содержимое должно продолжаться во внутреннем <xref:System.Windows.Controls.Grid>элемент.</xref:System.Windows.Controls.Grid>  
  
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
  
6.  Добавление элементов управления в пустой \<UserControl настроек элемент для заполнения на пользовательской странице. Сведения о том, как добавить функциональные возможности, относящиеся к Visual Studio см. в разделе [Добавление команды Visual Studio предоставляют начальную страницу](../extensibility/adding-visual-studio-commands-to-a-start-page.md).  
  
## <a name="testing-and-applying-the-custom-start-page"></a>Тестирование и применение настраиваемой начальной страницы  
 Не устанавливайте первичного экземпляра Visual Studio для запуска пользовательских начальной страницы, пока не убедитесь, что она не дает сбоя Visual Studio. Вместо этого тестирование в экспериментальном экземпляре.  
  
#### <a name="to-test-a-manually-created-custom-start-page"></a>Для тестирования созданного вручную настроенную начальную страницу  
  
1.  Скопируйте файл XAML и любые вспомогательные текстовые файлы или разметки файлы, в **%USERPROFILE%\My 2015\StartPages документы\Visual Studio\\ ** папки.  
  
2.  Если стартовая страница ссылается на все элементы или типы в сборках, которые не установлены в Visual Studio, скопируйте сборки и затем вставить их в *папка установки Visual Studio***\Common7\IDE\PrivateAssemblies\\**.  
  
3.  Введите в командную строку Visual Studio **devenv/rootsuffix Exp** открываемого в экспериментальном экземпляре Visual Studio.  
  
4.  В экспериментальном экземпляре, перейдите к **Сервис / Параметры / среды и запуска** и выберите свой XAML-файл из **настроить начальную страницу** раскрывающегося списка.  
  
5.  В меню **Вид** выберите пункт **Начальная страница**.  
  
     Отображать пользовательской начальной страницы. Если вы хотите изменить любые файлы, необходимо Закройте экспериментальный экземпляр, внесите необходимые изменения, скопируйте и вставьте измененных файлов и повторно открыть экспериментальный экземпляр для просмотра изменений.  
  
#### <a name="to-apply-the-custom-start-page-in-the-primary-instance-of-visual-studio"></a>Чтобы применить пользовательский начальная страница в основной экземпляр Visual Studio  
  
-   После тестирования начальной страницей и нашли стабильной используйте **настроить начальную страницу** параметр в **параметры** диалоговое окно выбрать ее в качестве начальной страницы в основной экземпляр Visual Studio  
  
## <a name="see-also"></a>См. также  
 [Пошаговое руководство: Добавление пользовательского XAML-файла начальной страницы](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)   
 [Добавление пользовательского элемента управления к домашней странице](../extensibility/adding-user-control-to-the-start-page.md)   
 [Добавление команд Visual Studio на начальную страницу](../extensibility/adding-visual-studio-commands-to-a-start-page.md)   
 [Пошаговое руководство: Сохранение пользовательских параметров на начальной странице](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)   
 [Развертывание пользовательской начальной страницы](../extensibility/deploying-custom-start-pages.md)
