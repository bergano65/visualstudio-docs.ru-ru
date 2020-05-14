---
title: Создание управления wPF Toolbox (ru) Документы Майкрософт
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- toolbox control
- toolbox
- wpf
ms.assetid: 9cc34db9-b0d1-4951-a02f-7537fbbb51ad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c1400efb0095760bf1cee302dd33dcf6ebb90152
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739565"
---
# <a name="create-a-wpf-toolbox-control"></a>Создание управления ящиком инструментов WPF

Шаблон управления набором инструментов WPF (Windows Presentation Framework) позволяет создавать элементы управления WPF, которые автоматически добавляются в **набор инструментов** при установке расширения. В этом пошаговом показании, как использовать шаблон для создания элемента управления **Toolbox,** который можно распространять среди других пользователей.

Начиная с Visual Studio 2015, вы не устанавливаете Visual Studio SDK из центра загрузки. Он включен в качестве дополнительной функции в Visual Studio установки. Вы также можете установить VS SDK позже. Для получения дополнительной информации, [см.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-the-toolbox-control"></a>Создание управления набором инструментов

### <a name="create-an-extension-with-a-wpf-toolbox-control"></a>Создание расширения с помощью управления wPF Toolbox

1. Создайте проект VSIX под названием `MyToolboxControl`. Шаблон проекта VSIX можно найти в диалоге **нового проекта,** ища "vsix".

2. Когда проект откроется, добавьте шаблон **элемента Управления WPF Toolbox** под названием. `MyToolboxControl` В **Solution Explorer**, правой кнопкой мыши узла проекта и выберите **Добавить** > **новый пункт**. В диалоге **Добавить новый элемент** перейдите на **Visual C'** > **Extensibility** и выберите **управление WPF Toolbox.** В поле **«Имя»** в нижней части окна измените имя файла команды на *MyToolboxControl.cs.*

    Теперь решение содержит пользовательский `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> элемент управления, который добавляет элемент управления в **Toolbox**и запись **актива Microsoft.VisualStudio.ToolboxControl** Asset в манифесте VSIX для развертывания.

#### <a name="to-create-the-control-ui"></a>Для создания контрольного uI

1. Откройте *MyToolboxControl.xaml* в дизайнере.

    В конструкторе показан элемент управления <xref:System.Windows.Controls.Grid>, содержащий элемент управления <xref:System.Windows.Controls.Button>.

2. Упорядочить расположение сетки. При выборе <xref:System.Windows.Controls.Grid> элемента управления синие полосы управления отображаются в верхнем и левом краях сетки. Вы можете добавить строки и столбцы в сетку, нажав на бары.

3. Добавление элементов управления детьми в сетку. Вы можете расположить элемент управления ребенка, перетащив его из панели `Grid.Row` `Grid.Column` **инструментов** в раздел сетки или установив его и атрибуты в XAML. Следующий пример добавляет две метки в верхнем ряду сетки и кнопку на втором ряду.

    ```xaml
    <Grid>
        <Label Grid.Row="0" Grid.Column="0" Name="label1" />
        <Label Grid.Row="0" Grid.Column="1" Name="label2" />
        <Button Name="button1" Click="button1_Click" Grid.Row="1" Grid.ColumnSpan="2" />
    </Grid>
    ```

## <a name="renaming-the-control"></a>Переименование элемента управления

 По умолчанию ваш элемент управления появится в **Toolbox** как **MyToolboxControl** в группе **myToolboxControl.MyToolboxControl**. Вы можете изменить эти имена в *файле MyToolboxControl.xaml.cs.*

1. Откройте *MyToolboxControl.xaml.cs* в представлении кода.

2. Найдите `MyToolboxControl` класс и переименуйте его в TestControl. (Самый быстрый способ сделать это , чтобы переименовать класс, а затем выбрать **переименовать** из меню контекста и завершить шаги. (Для получения дополнительной информации об команде **Rename** см. [Rename refactoring (C)](../ide/reference/rename.md).)

3. Перейдите `ProvideToolboxControl` к атрибуту и измените значение первого параметра для **тестирования.** Это название группы, которая будет содержать элемент управления в **Toolbox.**

    Полученный код должен выглядеть следующим образом:

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

## <a name="build-test-and-deployment"></a>Сборка, тестирование и развертывание

 При отладке проекта необходимо найти элемент управления, установленный в **toolbox** экспериментального экземпляра Visual Studio.

### <a name="to-build-and-test-the-control"></a>Сборка и тестирование элемента управления

1. Перестроить проект и начать отладку.

2. В новом экземпляре Visual Studio создайте проект приложения WPF. Убедитесь, что конструктор XAML открыт.

3. Найдите свой элемент управления в **панели элементов** и перетащите его в рабочую область конструирования.

4. Начать отладку приложения WPF.

5. Убедитесь, что отображается элемент управления.

### <a name="to-deploy-the-control"></a>Развертывание элемента управления

1. После создания проверенного проекта можно найти файл *.vsix* в папке «Бин-отладка»\* проекта.

2. Вы можете установить его на локальном компьютере, дважды нажав на файл *.vsix* и следуя процедуре установки. Чтобы удалить элемент управления, перейдите на **инструменты** > **расширения и обновления** и искать расширение управления, а затем нажмите **Uninstall**.

3. Загрузите файл *.vsix* в сеть или на веб-узел.

    При загрузке файла на веб-сайт [Visual Studio Marketplace](https://marketplace.visualstudio.com/) другие пользователи могут использовать расширения и обновления **инструментов** > **Extensions and Updates** в Visual Studio, чтобы найти элемент управления в Интернете и установить его.
