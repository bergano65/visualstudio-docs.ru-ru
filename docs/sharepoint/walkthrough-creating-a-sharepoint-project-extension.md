---
title: 'Пошаговое руководство: Создание расширения проекта SharePoint | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 17722233c5215858dce59a0d85a05f668de85446
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-a-sharepoint-project-extension"></a>Пошаговое руководство. Создание расширения проекта SharePoint
  В этом пошаговом руководстве показано, как создавать расширения для проектов SharePoint. Можно использовать расширение проекта реагировать на события на уровне проекта, например, когда проект добавлена, удалена или переименована. Также можно добавлять пользовательские свойства или реагировать на них при изменении значения свойства. В отличие от расширений элемента проекта расширения проекта нельзя связать с определенным типом проекта SharePoint. При создании расширения проекта это расширение загружается при открытии любого проекта SharePoint в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 В этом пошаговом руководстве вы создадите пользовательский логическое свойство, которое добавляется в любой проект SharePoint, созданных в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Если задано значение **True**, добавляет новое свойство или сопоставляет с ним папку ресурсов изображений в проект. Если задано значение **False**, папка "изображения" удаляется, если он существует. Дополнительные сведения см. в разделе [как: Добавление и удаление папок Mapped](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
 В этом пошаговом руководстве описаны следующие задачи.  
  
-   Создание [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] расширения для проектов SharePoint, выполняющий следующие:  
  
    -   Добавляет настраиваемое свойство проекта в окне «Свойства». Свойство применяется к любому проекту SharePoint.  
  
    -   Использует объектную модель проекта SharePoint, Добавление сопоставленной папки в проект.  
  
    -   Использует [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] объектная модель автоматизации (DTE), чтобы удалить сопоставленную папку из проекта.  
  
-   Построение [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] пакета Extension (VSIX) для развертывания сборки расширения свойств проекта.  
  
-   Отладка и тестирование свойства проекта.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Необходимы следующие компоненты на компьютере разработчика для выполнения данного пошагового руководства.  
  
-   Поддерживаемые выпуски [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)], SharePoint и [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Дополнительные сведения см. в разделе [требования к разработке решений SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. В этом пошаговом руководстве используется **проект VSIX** шаблона в [!INCLUDE[TLA2#tla_sdk](../sharepoint/includes/tla2sharptla-sdk-md.md)] Создание пакета VSIX для развертывания расширения свойства проекта. Дополнительные сведения см. в разделе [расширение инструментов SharePoint в Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="creating-the-projects"></a>Создание проектов  
 Для выполнения данного пошагового руководства, необходимо создать два проекта:  
  
-   Проект VSIX для создания пакета VSIX для развертывания расширения проекта.  
  
-   Проект библиотеки классов, реализующей расширение проекта.  
  
 Пошаговое руководство начинается с создания проектов.  
  
#### <a name="to-create-the-vsix-project"></a>Создание проекта VSIX  
  
1.  Запустите [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  В строке меню выберите **Файл**, **Создать**, **Проект**.  
  
3.  В **новый проект** диалогового окна разверните **Visual C#** или **Visual Basic** узлов и нажмите кнопку **расширяемости** узла.  
  
    > [!NOTE]  
    >  Этот узел доступен, только если установлен пакет SDK для Visual Studio. Дополнительные сведения см. в разделе предварительных требований этого раздела.  
  
4.  В верхней части диалогового окна выберите **.NET Framework 4.5** в список версий .NET Framework и выберите **проект VSIX** шаблона.  
  
5.  В **имя** введите **Пакет_расширений_проекта**, а затем выберите **ОК** кнопки.  
  
     **Пакет_расширений_проекта** проект отображается в **обозревателе решений**.  
  
#### <a name="to-create-the-extension-project"></a>Создание проекта расширения  
  
1.  В **обозреватель решений**откройте контекстное меню узла решения, выберите **добавить**, а затем выберите **новый проект**.  
  
2.  В **новый проект** диалогового окна разверните **Visual C#** или **Visual Basic** узлов, а затем выберите **Windows**.  
  
3.  В верхней части диалогового окна выберите **.NET Framework 4.5** в список версий .NET Framework и выберите **библиотеки классов** шаблона проекта.  
  
4.  В **имя** введите **Расширение_проекта**, а затем выберите **ОК** кнопки.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Добавляет **Расширение_проекта** в решение проект и открывает файл кода по умолчанию Class1.  
  
5.  Удалите файл Class1 код из проекта.  
  
## <a name="configuring-the-project"></a>Настройка проекта  
 Перед написанием кода для создания расширения проекта добавьте файлы кода и ссылок на сборки в проект расширения.  
  
#### <a name="to-configure-the-project"></a>Настройка проекта  
  
1.  Добавьте файл кода, который называется **CustomProperty** Расширение_проекта проект.  
  
2.  Откройте контекстное меню для **Расширение_проекта** проекта, а затем выберите **добавить ссылку**.  
  
3.  В **диспетчер ссылок - CustomProperty** диалогового окна выберите **Framework** узел, а затем установите флажок рядом со сборками System.ComponentModel.Composition и System.Windows.Forms.  
  
4.  Выберите **расширения** , установите флажок рядом со сборками Microsoft.VisualStudio.SharePoint и EnvDTE и нажмите кнопку **ОК** кнопки.  
  
5.  В **обозревателе решений**в разделе **ссылки** папку для **Расширение_проекта** проекта, выбор **EnvDTE**.  
  
6.  В **свойства** измените **внедрить типы взаимодействия** свойства **False**.  
  
## <a name="defining-the-new-sharepoint-project-property"></a>Определение нового свойства проекта SharePoint  
 Создайте класс, определяющий расширение проекта и поведение нового свойства проекта. Чтобы определить новое расширение проекта класс реализует <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> интерфейса. Реализуйте этот интерфейс, когда нужно определять расширения для проекта SharePoint. Кроме того, добавьте <xref:System.ComponentModel.Composition.ExportAttribute> в класс. Этот атрибут позволяет [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] обнаружить и загрузить вашей <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> реализации. Передайте <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> тип в конструктор атрибута.  
  
#### <a name="to-define-the-new-sharepoint-project-property"></a>Для определения нового свойства проекта SharePoint  
  
1.  Вставьте следующий код в файл кода CustomProperty.  
  
     [!code-vb[SPExt_ProjectExtension#1](../sharepoint/codesnippet/VisualBasic/projectextension/customproperty.vb#1)]
     [!code-csharp[SPExt_ProjectExtension#1](../sharepoint/codesnippet/CSharp/projectextension/customproperty.cs#1)]  
  
## <a name="building-the-solution"></a>Построение решения  
 Затем выполнить сборку решения, чтобы убедиться в том, что оно компилируется без ошибок.  
  
#### <a name="to-build-the-solution"></a>Построение решения  
  
1.  В строке меню последовательно выберите **Сборка**и **Собрать решение**.  
  
## <a name="creating-a-vsix-package-to-deploy-the-project-property-extension"></a>Создание пакета VSIX для развертывания расширения свойства проекта  
 Для развертывания проекта расширения, используйте проект VSIX в решении для создания пакета VSIX. Во-первых настройте пакет VSIX, изменив файл source.extension.vsixmanifest, включенный в проект VSIX. Затем создайте пакет VSIX с построением решения.  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>Для настройки и создания пакета VSIX  
  
1.  В **обозревателе решений**, откройте контекстное меню Файл source.extension.vsixmanifest и выберите **откройте** кнопки.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Открывает файл в конструкторе манифеста. Сведения, отображаемые в **метаданные** также отображается вкладка **расширения и обновления**. Все пакеты VSIX требуется файл extension.vsixmanifest. Дополнительные сведения об этом файле см. в разделе [ссылки 1.0 схемы расширения VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  В **название продукта** введите **настраиваемое свойство проекта**.  
  
3.  В **автор** введите **Contoso**.  
  
4.  В **описание** введите **настраиваемое свойство проекта SharePoint, с помощью которого сопоставление папки ресурсов изображений в проект**.  
  
5.  Выберите **активы** , а затем выберите **New** кнопки.  
  
     **Добавить новый актив** откроется диалоговое окно.  
  
6.  В **тип** выберите **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Это значение соответствует `MEFComponent` элемент в файл extension.vsixmanifest. Этот элемент задает имя сборки расширения в пакете VSIX. Дополнительные сведения см. в разделе [MEFComponent элемент (Схема VSX)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
7.  В **источника** выберите **проект в текущем решении** переключатель.  
  
8.  В **проекта** выберите **Расширение_проекта**.  
  
     Это значение определяет имя сборки, для которого выполняется сборка проекта.  
  
9. Выберите **ОК** закрыть **добавить новый актив** диалоговое окно.  
  
10. В строке меню выберите **файл**, **сохранить все** при завершении, а затем закройте конструктор манифестов.  
  
11. В строке меню выберите **построения**, **построить решение**, а затем убедитесь, что проект компилируется без ошибок.  
  
12. В **обозревателе решений**, откройте контекстное меню для **Пакет_расширений_проекта** проекта, а затем выберите **открыть папку в проводнике** кнопки.  
  
13. В **проводнике**, откройте выходную папку построения для проекта "Пакет_расширений_проекта" и убедитесь, что папка содержит файл с именем Пакет_расширений_проекта.VSIX.  
  
     По умолчанию является выходной папке сборки... папку \bin\debug в папке, содержащей файл проекта.  
  
## <a name="testing-the-project-property"></a>Проверка свойства проекта  
 Теперь вы готовы для тестирования настраиваемое свойство проекта. Можно легко отладить и проверить новое расширение свойства проекта в экспериментальном экземпляре [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Этот экземпляр [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] создается при запуске VSIX или другого проекта расширения. После отладки проекта можно установить расширение в системе и затем продолжить отладку и тестирование в обычном экземпляре [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
#### <a name="to-debug-and-test-the-extension-in-an-experimental-instance-of-visual-studio"></a>Отладка и тестирование расширения в экспериментальном экземпляре Visual Studio  
  
1.  Перезапустите [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] с учетными данными администратора и откройте решение "Пакет_расширений_проекта".  
  
2.  Запустите отладочную сборку проекта, выбрав **F5** ключа или выберите в строке меню, выберите **отладки**, **начать отладку**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Устанавливает расширение для %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom Property\1.0 проекта и запускает экспериментальный экземпляр [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
3.  В экспериментальном экземпляре [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], создайте проект для решения фермы SharePoint и использовать значения по умолчанию для других значений в мастере.  
  
    1.  В строке меню выберите **Файл**, **Создать**, **Проект**.  
  
    2.  В верхней части **новый проект** диалогового окна выберите **.NET Framework 3.5** в списке версий .NET Framework.  
  
         Расширения инструментов SharePoint требуются функции в этой версии [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)].  
  
    3.  В разделе **шаблоны** узел, разверните **Visual C#** или **Visual Basic** узел, выберите **SharePoint** узел и нажмите кнопку **2010** узла.  
  
    4.  Выберите **проект SharePoint 2010** шаблона, а затем введите **ModuleTest** как имя проекта.  
  
4.  В **обозревателе решений**, выберите **ModuleTest** узел проекта.  
  
     Новое пользовательское свойство **сопоставить папку изображений** отображается в **свойства** окна со значением по умолчанию **False**.  
  
5.  Измените значение этого свойства **True**.  
  
     Папка ресурса изображения добавляется в проект SharePoint.  
  
6.  Изменить значение этого свойства обратно **False**.  
  
     При выборе **Да** кнопку в **удалить папку Images?** диалоговое окно, изображения, папка ресурс будет удален из проекта SharePoint.  
  
7.  Закройте экспериментальный образец [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Расширение проектов SharePoint](../sharepoint/extending-sharepoint-projects.md)   
 [Как: Добавление свойства в проекты SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Преобразование между типами системы проектов SharePoint и другими типами проектов Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [Сохранение данных в расширениях системы проектов SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [Связь пользовательских данных с расширениями средств SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
  