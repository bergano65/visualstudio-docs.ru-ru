---
title: Создание элемента управления панели элементов WPF | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- toolbox control
- toolbox
- wpf
ms.assetid: 9cc34db9-b0d1-4951-a02f-7537fbbb51ad
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0785ebf5177e892bd5c450525af10dd61d381fc1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47560876"
---
# <a name="creating-a-wpf-toolbox-control"></a>Создание элемента управления панели инструментов WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [Создание элемента управления панели элементов WPF](https://docs.microsoft.com/visualstudio/extensibility/creating-a-wpf-toolbox-control).  
  
Шаблон элемента управления панели элементов WPF (Windows Presentation Framework) позволяет создавать элементы управления WPF, которые автоматически добавляются в **элементов** при установке расширения. В этом разделе показано, как использовать шаблон для создания **элементов** элемента управления, который можно передавать другим пользователям.  
  
 Начиная с Visual Studio 2015, не следует устанавливать пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-wpf-toolbox-control"></a>Создание элемента управления панели инструментов WPF  
  
#### <a name="create-an-extension-with-a-wpf-toolbox-control"></a>Создание расширения с помощью элемента управления панели элементов WPF  
  
1.  Создайте проект VSIX с именем `MyToolboxControl`. Вы найдете шаблон проекта VSIX в **новый проект** диалоговое окно, в разделе **Visual C# / Extensibility**.  
  
2.  При открытии проекта добавьте **элемента управления панели элементов WPF** шаблон элемента с именем `MyToolboxControl`. В **обозревателе решений**, щелкните правой кнопкой мыши узел проекта и выберите **добавить / новый элемент**. В **Добавление нового элемента** диалоговое окно, перейдите к **Visual C# / Extensibility** и выберите **элемента управления панели элементов WPF**. В **имя** в нижней части окна, измените имя командного файла для `MyToolboxControl.cs`.  
  
     Теперь решение содержит пользовательский элемент управления, `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> , добавляющий элемент управления **элементов**и **Microsoft.VisualStudio.ToolboxControl** запись ресурса в манифест VSIX для  развертывание.  
  
#### <a name="to-create-the-control-ui"></a>Создание элемента управления пользовательского интерфейса  
  
1.  Откройте MyToolboxControl.xaml в конструкторе.  
  
     Конструкторе показан <xref:System.Windows.Controls.Grid> элемент управления, содержащий <xref:System.Windows.Controls.Button> элемента управления.  
  
2.  Упорядочите макет сетки. При выборе <xref:System.Windows.Controls.Grid> управлять, отображаются панели синяя элементов управления на верхнего и левого краев сетки. Щелкая столбцы можно добавить строки и столбцы в сетку.  
  
3.  Добавление дочерних элементов управления в сетку. Можно разместить дочерний элемент управления, перетащив его из **элементов** в раздел сетки, или установив его `Grid.Row` и `Grid.Column` атрибутов в XAML. В следующем примере добавляется две метки в верхней строке сетки и кнопки на второй строке.  
  
    ```xaml  
    <Grid>  
        <Label Grid.Row="0" Grid.Column="0" Name="label1" />  
        <Label Grid.Row="0" Grid.Column="1" Name="label2" />  
        <Button Name="button1" Click="button1_Click" Grid.Row="1" Grid.ColumnSpan="2" />  
    </Grid>  
    ```  
  
## <a name="renaming-the-control"></a>Переименование элемента управления  
 По умолчанию элемент управления отображается в **элементов** как **MyToolboxControl** в группу с именем **MyToolboxControl.MyToolboxControl**. Можно изменить эти имена в файле MyToolboxControl.xaml.cs.  
  
1.  Откройте MyToolboxControl.xaml.cs в представлении кода.  
  
2.  Найдите класс MyToolboxControl и переименуйте его в TestControl. (Самый быстрый способ сделать это является переименование класса, затем выберите **Переименовать** в контекстном меню и следуйте инструкциям. (Дополнительные сведения о **Переименовать** команды, см. в разделе [Переименовать рефакторинг (C#)](../csharp-ide/rename-refactoring-csharp.md).)  
  
3.  Перейдите к `ProvideToolboxControl` атрибут и измените значение первого параметра для **теста**. Это имя группы, которая будет содержать элемент управления в **элементов**.  
  
     Итоговый код должен выглядеть следующим образом:  
  
    ```csharp  
    [ProvideToolboxControl("Test", true)]  
    public partial class TestControl : UserControl  
    {  
        public TestControl()  
        {  
            InitializeComponent();  
        }  
    }  
    ```  
  
## <a name="building-testing-and-deployment"></a>Сборка, тестирование и развертывание  
 При отладке проекта, вы увидите, элементом управления, установленным в **элементов** экспериментального экземпляра Visual Studio.  
  
#### <a name="to-build-and-test-the-control"></a>Сборка и тестирование элемента управления  
  
1.  Перестройте проект и начните отладку.  
  
2.  В новом экземпляре Visual Studio создайте проект приложения WPF. Убедитесь, что открыт конструктор XAML.  
  
3.  Найдите свой элемент управления в **панели элементов** и перетащите его в рабочую область конструирования.  
  
4.  Начните отладку приложения WPF.  
  
5.  Убедитесь, что отображается элемент управления.  
  
#### <a name="to-deploy-the-control"></a>Развертывание элемента управления  
  
1.  После сборки протестированного проекта VSIX-файл можно найти в папке \bin\debug\ проекта.  
  
2.  Его можно установить на локальном компьютере, дважды щелкните VSIX-файл и выполнив процедуру установки. Чтобы удалить элемент управления, выберите **средства / расширения и обновления** и искать расширения элемента управления, а затем нажмите кнопку **удаления**.  
  
3.  Отправьте VSIX-файл в сеть или на веб-сайт.  
  
     Если вы отправите файл [коллекции Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) веб-сайт, другие пользователи могли использовать **средства / расширения и обновления** в Visual Studio для поиска элемента управления в Интернете и установите его.

