---
title: "Создание пользовательской начальной страницы | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d67e0c53-9f5a-45fb-a929-b9d2125c3c82
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d9782e51688ae1ef4fda3ed52636de54149fa79e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="creating-a-custom-start-page"></a>Создание настраиваемой начальной страницы
Выполнив действия, описанные в этом документе, можно создать настраиваемую начальную страницу.  
  
## <a name="creating-a-blank-start-page"></a>Создание пустой начальной страницы  
 Во-первых необходимо предоставить пустую начальную страницу путем создания XAML-файл, который имеет структуру тег, Visual Studio распознает. Затем добавьте разметки и кода для создания внешний вид и функциональные возможности, которые нужно.  
  
#### <a name="to-create-a-blank-start-page"></a>Чтобы создать пустую начальную страницу  
  
1.  Создайте новый проект типа **приложение WPF** (**Visual C# / рабочий стол Windows**.  
  
2.  Добавьте ссылку на `Microsoft.VisualStudio.Shell.14.0`.  
  
3.  Откройте XAML-файл в редакторе XML и измените верхнего уровня \<окна > элемент \<UserControl > элемента без удаления любых объявлений пространств имен.  
  
4.  Удалить `x:Class` объявление из элемента верхнего уровня. Это обеспечивает совместимость с окном инструментов Visual Studio, на котором размещена начальной страницы в содержимое XAML.  
  
5.  Добавьте следующие объявления пространства имен верхнего уровня \<UserControl > элемент.  
  
    ```  
    xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
    xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
    ```  
  
     Эти пространства имен позволяют получить доступ к командам Visual Studio, элементы управления и настройки пользовательского интерфейса. Дополнительные сведения см. в разделе [Добавление команды Visual Studio предоставляют начальную страницу](../extensibility/adding-visual-studio-commands-to-a-start-page.md).  
  
     В следующем примере показана разметка в XAML-файл для пустую начальную страницу. Любое пользовательское содержимое должны перейти во внутреннем <xref:System.Windows.Controls.Grid> элемента.  
  
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
  
6.  Добавление элементов управления в пустом \<UserControl > элемента, который требуется заполнить настраиваемую начальную страницу. Сведения о том, как добавить функциональные возможности, относящиеся к Visual Studio см. в разделе [Добавление команды Visual Studio предоставляют начальную страницу](../extensibility/adding-visual-studio-commands-to-a-start-page.md).  
  
## <a name="testing-and-applying-the-custom-start-page"></a>Тестирование и применение настраиваемой начальной страницы  
 Не устанавливайте основном экземпляре Visual Studio, чтобы выполнить начальную страницу, пока не убедитесь в том, что он не приводит к сбою Visual Studio. Вместо этого тестирование в экспериментальном экземпляре.  
  
#### <a name="to-test-a-manually-created-custom-start-page"></a>Тестирование созданного вручную настраиваемой начальной страницы  
  
1.  Скопируйте файл XAML и все вспомогательные текстовые файлы или разметки файлы, к **%USERPROFILE%\My документы\Visual Studio 2015\StartPages\\**  папки.  
  
2.  Если начальная страница ссылается на все элементы или типы в сборках, которые не установлены в Visual Studio, скопируйте сборки, а затем вставьте их в *папка установки Visual Studio***\Common7\IDE\ PrivateAssemblies\\**.  
  
3.  Введите в командную строку Visual Studio **devenv/rootsuffix Exp** открыть экспериментальный экземпляр Visual Studio.  
  
4.  В экспериментальном экземпляре, перейдите в **Сервис / Параметры / Среда / запуска** и выберите файл XAML из **настроить начальную страницу** раскрывающегося списка.  
  
5.  В меню **Вид** выберите пункт **Начальная страница**.  
  
     Отображать вашей настраиваемой начальной страницы. Если вы хотите изменить все файлы, необходимо Закройте экспериментальный экземпляр, внести изменения, скопируйте и вставьте измененных файлов и повторно открыть экспериментальный экземпляр, чтобы просмотреть изменения.  
  
#### <a name="to-apply-the-custom-start-page-in-the-primary-instance-of-visual-studio"></a>Чтобы применить пользовательский начальную страницу в основном экземпляре Visual Studio  
  
-   После тестирования к начальной странице и получалось стабильный средство **настроить начальную страницу** в диалоговом окне **параметры** диалоговое окно «», чтобы выбрать его в качестве начальной страницы в основном экземпляре Visual Studio  
  
## <a name="see-also"></a>См. также  
 [Пошаговое руководство: Добавление пользовательского XAML-файла начальной страницы](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)   
 [Добавление пользовательского элемента управления на начальную страницу](../extensibility/adding-user-control-to-the-start-page.md)   
 [Добавление команд Visual Studio на начальную страницу](../extensibility/adding-visual-studio-commands-to-a-start-page.md)   
 [Пошаговое руководство: Сохранение пользовательских параметров на начальной странице](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)   
 [Развертывание настраиваемой начальной страницы](../extensibility/deploying-custom-start-pages.md)