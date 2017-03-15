---
title: "Пошаговое руководство. Динамическая настройка конфигурации элемента на панели элементов | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "панель элементов [пакет SDK для Visual Studio], добавление элементов управления (настраиваемые форматы)"
ms.assetid: 761f44b7-c748-4ff5-921f-fc4f71784b0e
caps.latest.revision: 45
caps.handback.revision: 45
manager: "douge"
---
# Пошаговое руководство. Динамическая настройка конфигурации элемента на панели элементов
В этом пошаговом руководстве показано, как управляемый пакет VSPackage может обеспечить поддержку динамической настройки объектов <xref:System.Drawing.Design.ToolboxItem>.  
  
> [!NOTE]
>  Самый простой способ добавления пользовательских элементов управления на панель элементов — использовать шаблоны элементов управления панели элементов, включенные в пакет SDK для Visual Studio. Этот раздел посвящен расширенной разработке панели элементов.  
>   
>  Дополнительные сведения о создании элементов управления панели элементов с помощью шаблонов см. в разделах [Практическое руководство. Создание элемента управления панели элементов, использующего Windows Forms](../misc/how-to-create-a-toolbox-control-that-uses-windows-forms.md) и [Создание элементов управления WPF](../extensibility/creating-a-wpf-toolbox-control.md).  
  
 В этом пошаговом руководстве рассматриваются перечисленные ниже действия.  
  
1.  Добавление и правильная регистрация всех элементов управления **панели элементов** в объектах VSPackage с помощью классов <xref:System.ComponentModel.ToolboxItemAttribute> и <xref:System.Drawing.ToolboxBitmapAttribute>.  
  
2.  Создание следующих двух элементов управления и добавление значков для каждого из них на **панель элементов**:  
  
    -   один элемент управления, который объявляет связанный объект <xref:System.Drawing.Design.ToolboxItem> по умолчанию;  
  
    -   один элемент управления, который объявляет связанный настраиваемый элемент **панели элементов**, производный от класса <xref:System.Drawing.Design.ToolboxItem>.  
  
3.  Создание реализации <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem> и ее регистрация путем выполнения следующих действий:  
  
    1.  определения класса фильтра, производного от класса <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem> и указывающего экземпляры <xref:System.Drawing.Design.ToolboxItem>, в отношении которых будет действовать эта реализация;  
  
    2.  применения атрибута <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemConfigurationAttribute>, который ссылается на класс фильтра, к классу, реализующему класс <xref:Microsoft.VisualStudio.Shell.Package> для VSPackage.  
  
4.  Регистрация VSPackage в качестве поставщика объектов <xref:System.Drawing.Design.ToolboxItem> путем применения <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemsAttribute> к классу, реализующему класс <xref:Microsoft.VisualStudio.Shell.Package> для VSPackage.  
  
5.  Использование отражения для создания списка всех объектов <xref:System.Drawing.Design.ToolboxItem>, предоставляемых пакетом VSPackage, во время загрузки пакета.  
  
6.  Создание обработчика для событий <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized> и <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded>. Это гарантирует правильную загрузку объектов <xref:System.Drawing.Design.ToolboxItem> пакета VSPackage.  
  
7.  Реализация в VSPackage команды для принудительной повторной инициализации **панели элементов**.  
  
## Обязательные компоненты  
 Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. Для получения дополнительной информации см. [SDK для Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## Расположения для шаблона Visual Studio Package  
 Шаблон проекта пакета Visual Studio можно найти в трех разных местах диалогового окна **Создание проекта**.  
  
1.  В разделе Visual Basic, "Расширяемость". Язык проекта по умолчанию — Visual Basic.  
  
2.  В разделе Visual C\#, "Расширяемость". Язык проекта по умолчанию — C\#.  
  
3.  В разделе "Другие типы проектов", "Расширяемость". Язык проекта по умолчанию — C\+\+.  
  
## Создание управляемого пакета VSPackage  
 Чтобы создать управляемый пакет VSPackage, выполните описанную ниже процедуру.  
  
#### Создание управляемого пакета VSPackage для предоставления элементов панели элементов  
  
1.  Создайте пакет VSPackage с именем `ItemConfiguration`. Для получения дополнительной информации см. [Пошаговое руководство. Создание команды меню с помощью шаблона пакета Visual Studio](../Topic/Walkthrough:%20Creating%20a%20Menu%20Command%20By%20Using%20the%20Visual%20Studio%20Package%20Template.md).  
  
2.  В шаблон **Пакет Visual Studio** добавьте команду меню.  
  
     Дайте этой команде имя `Initialize ItemConfigurationVB` для Visual Basic или `Initialize ItemConfigurationCS` для Visual C\#.  
  
3.  Для [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] добавьте следующие пространства имен в список импортированных пространств имен в созданном проекте:  
  
    -   Company.ItemConfiguration  
  
    -   Система  
  
    -   System.ComponentModel  
  
    -   System.Drawing  
  
    -   System.Windows.Forms  
  
4.  Добавьте ссылку на компонент <xref:System.Drawing.Design?displayProperty=fullName> платформы .NET Framework.  
  
 При выполнении этого пошагового руководства для нескольких языков необходимо обновить проект, чтобы устранить неоднозначность создаваемых сборок.  
  
#### Устранение неоднозначности пакетов VSPackage для Visual Basic и Visual C\#  
  
1.  Для [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]:  
  
    1.  Откройте свойства проекта и перейдите на вкладку **Приложение**.  
  
         Измените имя сборки на `ItemConfigurationVB`, а пространство имен по умолчанию — на `Company.ItemConfigurationVB`.  
  
    2.  Перейдите на вкладку **Ссылки**.  
  
         Обновите список импортированных пространств имен.  
  
         Удалите пространство имен Company.ItemConfiguration.  
  
         Добавьте пространство имен Company.ItemConfigurationVB.  
  
2.  Для [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]:  
  
    1.  Откройте свойства проекта и перейдите на вкладку **Приложение**.  
  
         Измените имя сборки на `ItemConfigurationCS`, а пространство имен по умолчанию — на `Company.ItemConfigurationCS`.  
  
    2.  Откройте класс ItemConfigurationPackage в редакторе кода.  
  
         Чтобы переименовать существующее пространство имен с помощью инструментов рефакторинга, щелкните имя существующего пространства имен `ItemConfiguration` правой кнопкой мыши, наведите указатель на пункт **Выполнить рефакторинг**, а затем выберите пункт **Переименовать**. Измените имя на `ItemConfigurationCS`.  
  
3.  Сохраните все изменения.  
  
#### Тестирование созданного кода  
  
1.  Скомпилируйте и запустите VSPackage в экспериментальном кусте Visual Studio.  
  
2.  В меню **Сервис** выберите пункт **Инициализировать конфигурацию элемента VB** или **Инициализировать конфигурацию элемента CS**.  
  
     При этом откроется окно сообщения с текстом, указывающим на то, что был вызван обработчик элемента меню пакета.  
  
3.  Закройте экспериментальную версию [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  
  
## Создание элементов управления панели элементов  
 В этом разделе вы создадите и зарегистрируете пользовательский элемент управления `Control1`, который объявляет связанный элемент **панели элементов** по умолчанию. Вы также создадите и зарегистрируете второй пользовательский элемент управления `Control2` и связанный настраиваемый элемент **панели элементов**`Control2_ToolboxItem`, производный от класса <xref:System.Drawing.Design.ToolboxItem>. Дополнительные сведения о создании элементов управления Windows Forms и классов <xref:System.Drawing.Design.ToolboxItem> см. в разделе [Создание элементов управления Windows Forms во время разработки](../Topic/Developing%20Windows%20Forms%20Controls%20at%20Design%20Time.md).  
  
#### Создание элементов панели элементов по умолчанию и настраиваемых элементов  
  
1.  Следуйте указаниям в [Пошаговое руководство: автозагрузка элементов на панели элементов](../Topic/Walkthrough:%20Autoloading%20Toolbox%20Items.md), чтобы создать элемент **панели элементов** по умолчанию и настраиваемый элемент **панели элементов**, как указано ниже.  
  
    1.  Выполните процедуру "Создание элемента управления **панели элементов**, который будет использоваться с объектом ToolboxItem по умолчанию". Обновите атрибут <xref:System.ComponentModel.DescriptionAttribute> так, чтобы он ссылался на этот проект.  
  
         В итоге код для класса `Control1` должен выглядеть следующим образом:  
  
         [!code-cs[DynamicToolboxMembers#01](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_1.cs)]
         [!code-vb[DynamicToolboxMembers#01](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_1.vb)]  
  
    2.  Выполните процедуру "Создание элемента управления **панели элементов** для использования настраиваемого класса, производного от ToolboxItem. Обновите атрибут <xref:System.ComponentModel.DescriptionAttribute> так, чтобы он ссылался на этот проект.  
  
         В итоге код для классов `Control2` и `Control2_ToolboxItem` должен выглядеть следующим образом:  
  
         [!code-vb[DynamicToolboxMembers#02](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_2.vb)]
         [!code-cs[DynamicToolboxMembers#02](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_2.cs)]  
  
2.  Сохраните файлы.  
  
## Внедрение растровых значков  
 Атрибут <xref:System.Drawing.ToolboxBitmapAttribute>, применяемый к каждому элементу управления, указывает значок, который следует связать с элементом управления. Создайте растровые изображения для обоих элементов управления и назовите их следующим образом:  
  
-   `Control1.bmp` для класса `Control1`.  
  
-   `Control2.bmp` для класса `Control2`.  
  
#### Внедрение растрового значка для элемента панели элементов  
  
1.  Добавьте в проект новое растровое изображение, выполнив указанные ниже действия.  
  
    1.  В **обозревателе решений** щелкните правой кнопкой мыши проект VSPackage, наведите указатель на пункт **Добавить**, а затем выберите пункт **Новый элемент**.  
  
    2.  В диалоговом окне **Добавление нового элемента** выберите пункт **Файл точечного рисунка** и введите имя растрового изображения.  
  
2.  С помощью редактора растровых изображений создайте значок 16x16, выполнив указанные ниже действия.  
  
    1.  В меню **Вид** выберите пункт **Окно свойств**.  
  
    2.  В окне **Свойства** установите для свойств **Высота** и **Ширина** значение 16.  
  
    3.  Создайте изображение значка с помощью редактора.  
  
3.  В **обозревателе решений** щелкните объект растрового изображения правой кнопкой мыши и выберите пункт **Свойства**.  
  
4.  Задайте для свойства **Действие при сборке** значение **Внедренный ресурс**.  
  
5.  Сохраните все открытые файлы.  
  
## Добавление поставщика динамической настройки панели элементов  
 В этом разделе вы создадите и зарегистрируете класс, реализующий интерфейс <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem>. Экземпляр этого класса создается и используется интегрированной средой разработки [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] для настройки элементов управления **панели элементов**.  
  
> [!NOTE]
>  Так как среда [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] создает экземпляр реализации <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem>, не реализуйте интерфейс <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem> для класса, реализующего <xref:Microsoft.VisualStudio.Shell.Package> для VSPackage.  
  
#### Создание и регистрация объекта конфигурации элементов управления панели элементов  
  
1.  В **обозревателе решений** добавьте класс в проект ItemConfiguration и назовите его `ToolboxConfig`.  
  
2.  Добавьте в файл приведенные ниже операторы пространств имен.  
  
     [!code-cs[DynamicToolboxMembers#03](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_3.cs)]
     [!code-vb[DynamicToolboxMembers#03](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_3.vb)]  
  
3.  Убедитесь в том, что класс `ToolboxConfig` является `public` и реализует интерфейс <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem>.  
  
4.  Примените <xref:System.Runtime.InteropServices.GuidAttribute> и <xref:Microsoft.VisualStudio.Shell.ProvideAssemblyFilterAttribute> к классу `ToolboxConfig``.`  
  
    -   Для [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] используйте имя сборки `"ItemConfigurationVB, Version=*, Culture=*, PublicKeyToken=*"`.  
  
    -   Для [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] используйте имя сборки `"ItemConfigurationCS, Version=*, Culture=*, PublicKeyToken=*"`.  
  
     Благодаря этому класс `ToolboxConfig` будет работать только с объектами <xref:System.Drawing.Design.ToolboxItem>, которые предоставлены сборкой, содержащей текущий пакет VSPackage.  
  
     [!code-cs[DynamicToolboxMembers#04](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_4.cs)]
     [!code-vb[DynamicToolboxMembers#04](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_4.vb)]  
  
     Идентификатор GUID можно создать, выбрав пункт **Создать GUID** в меню **Сервис**. Выберите **формат с квадратными скобками**, щелкните **Копировать** и вставьте идентификатор GUID в код. Измените ключевое слово `GUID` на `Guid`.  
  
5.  Реализуйте метод <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem.ConfigureToolboxItem%2A> интерфейса <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem> так, чтобы он применялся только к двум классам <xref:System.Drawing.Design.ToolboxItem>: `Control1` и `Control2`.  
  
     Реализация <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem.ConfigureToolboxItem%2A> применяет экземпляры <xref:System.ComponentModel.ToolboxItemFilterAttribute> к двум объектам <xref:System.Drawing.Design.ToolboxItem> указанным ниже образом.  
  
    -   Объект <xref:System.Drawing.Design.ToolboxItem>, реализованный с помощью класса `Control1`, доступен на **панели элементов** только тем разработчикам, которые работают с объектами <xref:System.Windows.Forms.UserControl>.  
  
    -   Объект <xref:System.Drawing.Design.ToolboxItem>, реализованный с помощью класса `Control2`, недоступен на **панели элементов** разработчикам, которые работают с объектами <xref:System.Windows.Forms.UserControl>.  
  
     [!code-cs[DynamicToolboxMembers#05](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_5.cs)]
     [!code-vb[DynamicToolboxMembers#05](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_5.vb)]  
  
## Изменение реализации VSPackage  
 Реализацию VSPackage по умолчанию, предоставляемую шаблоном пакета [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], необходимо изменить так, чтобы она выполняла следующие действия:  
  
-   регистрировалась как поставщик элементов **панели элементов**;  
  
-   регистрировала класс, обеспечивающий динамическую настройку элементов управления **панели элементов** для VSPackage;  
  
-   использовала <xref:System.Drawing.Design.ToolboxService> для загрузки всех объектов <xref:System.Drawing.Design.ToolboxItem>, предоставляемых сборкой VSPackage;  
  
-   обрабатывала события <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized> и <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded>.  
  
#### Изменение реализации пакета для поставщика элементов панели элементов в VSPackage  
  
1.  Откройте класс ItemConfigurationPackage в редакторе кода.  
  
2.  Измените объявление класса `ItemConfigurationPackage`, который является реализацией класса <xref:Microsoft.VisualStudio.Shell.Package> в решении.  
  
    1.  Добавьте в файл приведенные ниже операторы пространств имен.  
  
         [!code-vb[DynamicToolboxMembers#06](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_6.vb)]
         [!code-cs[DynamicToolboxMembers#06](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_6.cs)]  
  
    2.  Чтобы зарегистрировать VSPackage как поставщик элементов **панели элементов**, примените к пакету атрибут <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemsAttribute>. Чтобы зарегистрировать класс `ToolboxConfig` как поставщик динамической настройки элементов управления **панели элементов**, примените к пакету атрибут <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemConfigurationAttribute>.  
  
         [!code-vb[DynamicToolboxMembers#07](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_7.vb)]
         [!code-cs[DynamicToolboxMembers#07](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_7.cs)]  
  
        > [!NOTE]
        >  Единственным аргументом <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemsAttribute> является версия <xref:System.Drawing.Design.ToolboxItem>, предоставляемая пакетом VSPackage. Изменив это значение, можно обеспечить принудительную загрузку пакета VSPackage интегрированной средой разработки, даже если имеется ранее кэшированная версия <xref:System.Drawing.Design.ToolboxItem>.  
  
    3.  Создайте два новых поля `private` в классе `ItemConfiguration` следующим образом:  
  
         член <xref:System.Collections.ArrayList> с именем `ToolboxItemList` для хранения списка объектов <xref:System.Drawing.Design.ToolboxItem>, которыми управляет класс `ItemConfiguration`;  
  
         объект <xref:System.String> с именем `CategoryTab`, который содержит вкладку **панели элементов**, используемую для хранения объектов <xref:System.Drawing.Design.ToolboxItem>, которыми управляет класс `ItemConfiguration`.  
  
         [!code-vb[DynamicToolboxMembers#08](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_8.vb)]
         [!code-cs[DynamicToolboxMembers#08](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_8.cs)]  
  
     Результат этого изменения должен выглядеть примерно так:  
  
     [!code-vb[DynamicToolboxMembers#09](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_9.vb)]
     [!code-cs[DynamicToolboxMembers#09](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_9.cs)]  
  
3.  Определите метод `OnRefreshToolbox` для обработки событий <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized> и <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded>.  
  
     Метод `OnRefreshToolbox` использует список объектов <xref:System.Drawing.Design.ToolboxItem>, содержащихся в поле `ToolboxItemList`, и выполняет следующие действия:  
  
    -   удаляет все объекты <xref:System.Drawing.Design.ToolboxItem> со вкладки **панели элементов**, которая определена в поле `CategoryTab`;  
  
    -   добавляет на вкладку **панели элементов** новые экземпляры всех объектов <xref:System.Drawing.Design.ToolboxItem>, перечисленных в поле `ToolboxItemList`;  
  
    -   устанавливает вкладку **панели элементов** в качестве активной вкладки.  
  
     [!code-vb[DynamicToolboxMembers#10](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_10.vb)]
     [!code-cs[DynamicToolboxMembers#10](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_10.cs)]  
  
4.  Для [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] зарегистрируйте в конструкторе метод `OnRefreshToolbox` в качестве обработчика событий <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized> и <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded>.  
  
     [!code-cs[DynamicToolboxMembers#11](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_11.cs)]  
  
5.  Измените метод `Initialize` в `ItemConfigurationPackage` для заполнения поля `ToolboxItemList` путем вызова метода <xref:System.Drawing.Design.ToolboxService.GetToolboxItems%2A> класса <xref:System.Drawing.Design.ToolboxService?displayProperty=fullName>. Служба **панели элементов** получает все классы элементов **панели элементов**, определенные в выполняемой в данный момент сборке. Поле `ToolboxItemList` используется обработчиками событий **панели элементов** для загрузки элементов **панели элементов**.  
  
     Добавьте следующий код в конец метода `Initialize`.  
  
     [!code-vb[DynamicToolboxMembers#12](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_12.vb)]
     [!code-cs[DynamicToolboxMembers#12](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_12.cs)]  
  
    > [!NOTE]
    >  В качестве упражнения можно создать механизм для проверки версии VSPackage или элементов и выполнения обновления только в том случае, если версия VSPackage или <xref:System.Drawing.Design.ToolboxItem> изменилась.  
  
## Инициализация панели элементов  
  
#### Реализация команды для инициализации панели элементов  
  
-   В классе `ItemConfigurationPackage` измените метод `MenuItemCallBack`, который является обработчиком команды, связанной с элементом меню.  
  
     Замените существующую реализацию метода `MenuItemCallBack`, используя следующий код:  
  
     [!code-vb[DynamicToolboxMembers#13](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_13.vb)]
     [!code-cs[DynamicToolboxMembers#13](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_13.cs)]  
  
## Сборка и запуск решения  
 Вы можете испытать результат выполнения инструкций из этого пошагового руководства, используя экземпляр Visual Studio, выполняющийся в экспериментальном кусте.  
  
#### Испытание результата выполнения инструкций этого пошагового руководства  
  
1.  Откройте Visual Studio и в меню **Сборка** выберите пункт **Пересобрать решение**.  
  
2.  Нажмите клавишу F5, чтобы запустить второй экземпляр [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] в экспериментальном кусте реестра.  
  
     Дополнительные сведения об использовании экспериментального куста см. в разделе [Экспериментальный экземпляр](../extensibility/the-experimental-instance.md).  
  
3.  Откройте меню **Сервис**.  
  
     Команда **Инициализировать ItemConfiguration VB** или **Инициализировать ItemConfiguration CS** должна находиться в начале меню вместе со значком с цифрой 1.  
  
4.  Создайте новое приложение Windows Forms в [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] или [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].  
  
     Откроется конструктор на основе <xref:System.Windows.Forms.Form>.  
  
5.  Добавьте пользовательский элемент управления в проект.  
  
     Появится конструктор пользовательских элементов управления.  
  
6.  Закрепите **панель элементов** в открытом состоянии и переключитесь между двумя представлениями конструктора.  
  
     Обратите внимание: то, какой элемент **панели элементов** скрыт, а какой отображается, зависит от того, в каком конструкторе находится фокус.  
  
7.  Перетащите первый элемент **панели элементов** в пользовательский элемент управления, чтобы добавить в него экземпляр `Control1`.  
  
8.  Перетащите второй элемент **панели элементов** в форму, чтобы добавить в нее экземпляр `Control2`.  
  
9. Выполните сборку приложения Windows.  
  
     Пользовательский элемент управления для приложения теперь доступен на **панели элементов**.  
  
10. Добавьте в форму пользовательский элемент управления приложения, а затем повторно выполните сборку приложения и его запуск.  
  
     Когда приложение запустится, щелкните каждый элемент управления на форме, чтобы открыть соответствующее окно сообщения.  
  
## Анализ реализации  
 Так как параметр `assemblyFilter` имеется в конструкторе класса <xref:Microsoft.VisualStudio.Shell.ProvideAssemblyFilterAttribute>, метод <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem.ConfigureToolboxItem%2A> класса `ToolboxConfg` применяется только к объектам <xref:System.Drawing.Design.ToolboxItem> в сборке, созданной в этом пошаговом руководстве.  
  
 Поэтому при каждой активации категории **ItemConfiguration Walkthrough** на **панели элементов** вызывается метод <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem.ConfigureToolboxItem%2A> класса `ToolboxConfg`, и экземпляры <xref:System.ComponentModel.ToolboxItemFilterAttribute> применяются к объектам <xref:System.Drawing.Design.ToolboxItem>, реализованным с помощью `Control1` и `Control2`.  
  
## См. также  
 [Расширение панели элементов](../misc/extending-the-toolbox.md)   
 [Регистрация возможностей поддержки панели элементов](../misc/registering-toolbox-support-features.md)   
 [Разработка расширенных элементов управления панели элементов](/visual-cpp/misc/advanced-toolbox-control-development)   
 [Пошаговые руководства по панели элементов](../misc/toolbox-walkthroughs.md)