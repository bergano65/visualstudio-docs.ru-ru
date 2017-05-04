---
title: "Walkthrough: Creating a SharePoint Project Extension | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "projects [SharePoint development in Visual Studio], extending"
  - "SharePoint development in Visual Studio, extending projects"
  - "SharePoint projects, extending"
ms.assetid: 5547e2ed-47a3-48f1-9619-42149c03df76
caps.latest.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 25
---
# Walkthrough: Creating a SharePoint Project Extension
  В этом пошаговом руководстве иллюстрируется создание расширения для проектов SharePoint.  Расширение проекта можно использовать для реагирования на события проект\- уровня например, если добавление, удаление и переименование проекта.  Кроме того, при изменении значения свойства можно добавить настраиваемые свойства или выполнить определенные действия.  В отличие от расширений элемента проекта, расширения проекта нельзя связать с определенный типом проекта SharePoint.  При создании расширения проекта это расширение загружается при открытии любого проекта SharePoint в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 В этом пошаговом руководстве будет создано настраиваемое свойство логического типа, добавляемое ко всем проектам SharePoint, создаваемым в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Если для него задано значение **True**, новое свойство добавляет в проект или сопоставляет с ним папку ресурсов "Изображения".  Если для него задано значение **False**, папка "Изображения" удаляется, если она существует.  Дополнительные сведения см. в разделе [Практическое руководство. Добавление и удаление сопоставленных папок](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
 В этом пошаговом руководстве показано выполнение следующих задач.  
  
-   Создание расширения [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] для проектов SharePoint, которое выполняет следующие действия.  
  
    -   Добавляет настраиваемое свойство проекта в окно "Свойства".  Это свойство применяется к любым проектам SharePoint.  
  
    -   Использует объектную модель проекта SharePoint для добавления в проект сопоставленной папки.  
  
    -   Использует объектную модель автоматизации [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(DTE\) для удаления сопоставленной папки из проекта.  
  
-   Построение пакета расширения [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(VSIX\) для развертывания сборки расширения свойств проекта.  
  
-   Отладка и тестирование свойства проекта.  
  
## Обязательные компоненты  
 Для выполнения данного пошагового руководства на компьютере разработчика должны быть установлены следующие компоненты:  
  
-   Поддерживаемые выпуски [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)], SharePoint и [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Дополнительные сведения см. в разделе [Требования по разработке решений SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)].  В этом пошаговом руководстве шаблон **Проект VSIX** \([!INCLUDE[TLA2#tla_sdk](../sharepoint/includes/tla2sharptla-sdk-md.md)]\) используется для создания пакета VSIX, который служит для развертывания расширения свойства проекта.  Дополнительные сведения см. в разделе [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
## Создание проектов  
 Чтобы выполнить это пошаговое руководство, необходимо создать два проекта:  
  
-   проект VSIX для создания пакета VSIX с целью развертывания расширения проекта;  
  
-   проект библиотеки классов, реализующей расширение проекта.  
  
 Начните выполнение пошагового руководства с создания проектов.  
  
#### Создание проекта VSIX  
  
1.  Запустите [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  В строке меню выберите **Файл**, **Создать**, **Проект**.  
  
3.  В диалоговом окне **Создать проект** разверните узлы **Visual C\#** или **Visual Basic**, а затем выберите узел **Расширение среды**.  
  
    > [!NOTE]  
    >  Этот узел доступен, только если установить пакет SDK для Visual Studio.  Дополнительные сведения см. в параграфе предварительных требований ранее в этом разделе.  
  
4.  В верхней части диалогового окна, выберите **платформа .NET Framework 4,5** в списке версий платформы .NET Framework, а затем выберите шаблон **Проект VSIX**.  
  
5.  В окне **Имя**, вставки **ProjectExtensionPackage**, а затем кнопку **ОК**.  
  
     Проект **ProjectExtensionPackage** отображается в **Обозреватель решений**.  
  
#### Создание проекта расширения  
  
1.  В **Обозреватель решений** открыть контекстное меню для узла решения выберите **Добавить**, а затем выберите **Создать проект**.  
  
    > [!NOTE]  
    >  В проектах [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] узел решения отображается в **Обозреватель решений**, только если флажок **Всегда показывать решение** выбрать в ["Общие", страница "Проекты и решения", диалоговое окно "Параметры"](http://msdn.microsoft.com/ru-ru/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).  
  
2.  В диалоговом окне **Создать проект** разверните узлы **Visual C\#** или **Visual Basic**, а затем выберите **Окна**.  
  
3.  В верхней части диалогового окна, выберите **платформа .NET Framework 4,5** в списке версий платформы .NET Framework, а затем выберите шаблон проекта **Библиотека классов**.  
  
4.  В окне **Имя**, вставки **ProjectExtension**, а затем кнопку **ОК**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] добавит проект **Расширение\_проекта** в решение и откроет заданный по умолчанию файл с кодом Class1.  
  
5.  Удалите из проекта файл c кодом Class1.  
  
## Настройка проекта  
 Перед разработкой кода для создания расширения проекта добавьте в проект расширения ссылки на файлы с кодом и ссылки на сборки.  
  
#### Настройка проекта  
  
1.  Добавьте файл кода с именем **CustomProperty** в проект ProjectExtension.  
  
2.  Открыть контекстное меню для проекта **ProjectExtension**, а затем выберите **Добавить ссылку**.  
  
3.  В диалоговом окне **Диспетчер ссылок – CustomProperty** выберите узел **Платформа**, а затем установите флажок рядом с сборками и System.Windows.Forms System.ComponentModel.Composition.  
  
4.  Выберите узел **Расширения** установите флажок рядом с сборками Microsoft.VisualStudio.SharePoint и EnvDTE, а затем нажмите кнопку **ОК**.  
  
5.  В **Обозреватель решений** в папке **Ссылки** для проекта **ProjectExtension** выберите **EnvDTE**.  
  
6.  В окне **Свойства** измените значение свойства **Внедрить типы взаимодействия** на **False**.  
  
## Определение нового свойства проекта SharePoint  
 Создайте класс, определяющий расширение проекта и поведение нового свойства проекта.  Для определения нового расширения проекта класс реализует интерфейс <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>.  Этот интерфейс следует реализовывать при каждом определении расширения для проекта SharePoint.  Кроме того, следует добавить к классу атрибут <xref:System.ComponentModel.Composition.ExportAttribute>.  Данный атрибут позволяет приложению [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] находить и загружать пользовательскую реализацию <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>.  Передайте конструктору этого атрибута тип <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>.  
  
#### Определение нового свойства проекта SharePoint  
  
1.  Вставьте следующий код в файл кода CustomProperty.  
  
     [!code-csharp[SPExt_ProjectExtension#1](../snippets/csharp/VS_Snippets_OfficeSP/spext_projectextension/cs/projectextension/customproperty.cs#1)]
     [!code-vb[SPExt_ProjectExtension#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spext_projectextension/vb/projectextension/customproperty.vb#1)]  
  
## Построение решения  
 Далее нужно построить решение, чтобы убедиться в отсутствии ошибок при его компиляции.  
  
#### Построение решения  
  
1.  В строке меню выберите **Построение**, **Построить решение**.  
  
## Создание пакета VSIX для развертывания расширения свойства проекта  
 Для развертывания расширения проекта воспользуйтесь проектом VSIX в своем решении для создания пакета VSIX.  Сначала настройте пакет VSIX, изменив содержимое файла source.extension.vsixmanifest, входящего в состав проекта VSIX.  Затем создайте пакет VSIX, выполнив построение решения.  
  
#### Настройка и создание пакета VSIX  
  
1.  В **Обозреватель решений** открыть контекстное меню для файла source.extension.vsixmanifest, а затем нажмите кнопку **Открыть**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] открывает файл в конструкторе манифестов.  Сведения, которые отображаются на вкладке **Метаданные** также отображается в **Расширения и обновления**. Все пакеты VSIX, необходим файл extension.vsixmanifest.  Дополнительные сведения об этом файле см. в разделе [Справочник по схеме расширения VSIX](http://msdn.microsoft.com/ru-ru/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  В окне **Название продукта** введите **Пользовательское свойство проекта**.  
  
3.  В окне **Автор** введите **Contoso**.  
  
4.  В окне **Описание** введите **Пользовательское свойство проекта SharePoint, которое переключает сопоставление папки ресурсов изображений в проект**.  
  
5.  Выберите вкладку **Активы**, а затем нажмите кнопку **Создать**.  
  
     Диалоговое окно **Добавить новый актив**.  
  
6.  В списке **Тип** выберите **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Это значение соответствует элементу `MEFComponent`, описанному в файле extension.vsixmanifest.  Этот элемент задает имя сборки расширения в пакете VSIX.  Дополнительные сведения см. в разделе [NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/ru-ru/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
7.  В списке **Источник** выберите переключатель **Проект в текущем решении**.  
  
8.  В списке **Проект** выберите **ProjectExtension**.  
  
     Это значение указывает имя сборки, что построении проекта.  
  
9. Выберите **ОК**, чтобы закрыть диалоговое окно **Добавить новый актив**.  
  
10. В строке меню выберите **Файл**, **Сохранить все** завершив, а затем закройте конструктор манифеста.  
  
11. В строке меню выберите **Построение**, **Построить решение** и убедитесь, что проект будет компилироваться без ошибок.  
  
12. В **Обозреватель решений** открыть контекстное меню для проекта **ProjectExtensionPackage** и нажмите кнопку **Открыть папку в проводнике**.  
  
13. В **Проводник**, откройте выходную папку построения для проекта ProjectExtensionPackage, а затем проверьте, что папка содержит файл с именем ProjectExtensionPackage.vsix.  
  
     По умолчанию выходной папкой построения является папка ..  \\bin\\Debug, расположенная в папке, содержащей файл проекта.  
  
## Проверка свойства проекта  
 Теперь можно проверить пользовательское свойство проекта.  Проще всего отладка и тестирование нового расширения свойства проекта в экспериментальном экземпляре [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Этот экземпляр [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] созданы при запуске VSIX или другого проекта расширяемости.  После отладки проекта можно задать расширения в системе, а затем продолжить отладку и протестировать его в обычном экземпляре [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
#### Отладка и тестирование расширения в экспериментальном экземпляре Visual Studio  
  
1.  Перезапустите [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] с учетными данными администратора, а затем откройте решение ProjectExtensionPackage.  
  
2.  Начните построение отладки проекта, то путем выбора ключа **F5** либо в строке меню, при выборе **Отладка**, **Начать отладку**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] установит расширения до %UserProfile% \\ AppData \\ local \\ Microsoft \\ VisualStudio \\ 11.0Exp \\ extensions \\ Contoso \\ пользовательское свойство проекта \\ 1.0 и запускает экспериментальном экземпляре [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
3.  В экспериментальном экземпляре [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] создайте проект SharePoint для решения фермы и используйте значения по умолчанию для остальных значений в мастере.  
  
    1.  В строке меню выберите **Файл**, **Создать**, **Проект**.  
  
    2.  В верхней части диалогового окна **Создать проект** выберите **.NET Framework 3.5** в списке версий платформы .NET Framework.  
  
         Расширения средств SharePoint требуют функций в этой версии [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)].  
  
    3.  В узле **Шаблоны** разверните узел **Visual C\#** или **Visual Basic** выберите узел **SharePoint**, а затем выберите узел **2010**.  
  
    4.  Выберите шаблон **Проект SharePoint 2010**, а затем введите в качестве имени проекта **ModuleTest**.  
  
4.  В **Обозреватель решений** выберите узел проекта **ModuleTest**.  
  
     В окне **Свойства** отобразится новое настраиваемое свойство **Сопоставить папку изображений** со значением по умолчанию **False**.  
  
5.  Измените значение свойства в **True**.  
  
     В проект SharePoint будет добавлена папка ресурсов "Изображения".  
  
6.  Измените значение свойства обратно в **False**.  
  
     Если выбрана кнопка **Да** в диалоговом окне **Удалите папку образов?**, то в папке ресурсов изображений удаляется из проекта SharePoint.  
  
7.  Закройте экспериментальный экземпляр [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
## См. также  
 [Extending SharePoint Projects](../sharepoint/extending-sharepoint-projects.md)   
 [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
  