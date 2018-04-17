---
title: 'Пошаговое руководство: Расширение обозревателя серверов для отображения веб-частей | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint commands
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 34975f93b719c759707110907a3c19dabbd661c1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-extending-server-explorer-to-display-web-parts"></a>Пошаговое руководство. Расширение обозревателя сервера, чтобы в нем отображались веб-части
  В Visual Studio можно использовать **подключения SharePoint** узел **обозревателя серверов** просматривать компоненты на сайтах SharePoint. Тем не менее **обозревателя серверов** по умолчанию не отображаются некоторые компоненты. В этом пошаговом руководстве вы будете расширить **обозревателя серверов** подключить отображается коллекции веб-частей на сайте SharePoint.  
  
 В этом пошаговом руководстве описаны следующие задачи.  
  
-   Создание расширения Visual Studio, который расширяет **обозревателя серверов** одним из следующих способов:  
  
    -   Добавляет расширение **коллекции веб-частей** в узле каждого узла сайта SharePoint в **обозревателя серверов**. Этот новый узел содержит дочерние узлы, представляющие каждой веб-части в галерею веб-частей на сайте.  
  
    -   Расширение определяет новый тип узла, представляющий экземпляр веб-части. Этот новый тип узла является основой для дочерних узлов в новом **коллекции веб-частей** узла. Новый тип узла веб-части показывает информацию в **свойства** окна веб-части, который он представляет. Тип узла также включает пользовательский контекстного меню в элемент, можно использовать в качестве отправной точки для выполнения других задач, связанных с веб-части.  
  
-   Создание двух пользовательских команд SharePoint, который вызывает сборку расширения. Команды SharePoint, методы, которые могут быть вызваны сборок расширения для использования API-интерфейсы в серверной объектной модели SharePoint. В этом пошаговом руководстве создается команд, которые извлекают данные о веб-части из локального сайта SharePoint на компьютере разработчика. Дополнительные сведения см. в разделе [вызова объектной модели SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
-   Построение пакета расширения Visual Studio (VSIX) для развертывания расширения.  
  
-   Отладка и тестирование расширения.  
  
> [!NOTE]  
>  Альтернативную версию данного пошагового руководства, использующего объектную модель клиента для SharePoint вместо его серверную объектную модель, в разделе [Пошаговое руководство: вызов клиентской объектной модели SharePoint в расширении обозревателя серверов](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md).  
  
## <a name="prerequisites"></a>Предварительные требования  
 Необходимы следующие компоненты на компьютере разработчика для выполнения данного пошагового руководства.  
  
-   Поддерживаемые версии Windows, SharePoint и Visual Studio. Дополнительные сведения см. в разделе [требования к разработке решений SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio SDK. В этом пошаговом руководстве используется **проект VSIX** шаблона в пакете SDK для создания пакета VSIX для развертывания элемента проекта. Дополнительные сведения см. в разделе [расширение инструментов SharePoint в Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Изучением приведенных ниже концепций будет полезно, хотя и не требуется для выполнения данного пошагового руководства.  
  
-   Использование серверной объектной модели для SharePoint. Дополнительные сведения см. в разделе [с помощью объектной модели SharePoint Foundation серверные](http://go.microsoft.com/fwlink/?LinkId=177796).  
  
-   Веб-части в решениях SharePoint. Дополнительные сведения см. в разделе [Общие сведения о частях Web](http://go.microsoft.com/fwlink/?LinkId=177803).  
  
## <a name="creating-the-projects"></a>Создание проектов  
 Для выполнения данного пошагового руководства, необходимо создать три проекта:  
  
-   Чтобы создать пакет VSIX для развертывания расширения проекта VSIX.  
  
-   Проект библиотеки классов, которая реализует расширение. Этот проект должны предназначаться для платформы .NET Framework 4.5.  
  
-   Проект библиотеки классов, определяющий пользовательские команды SharePoint. Этот проект должен использовать.NET Framework 3.5.  
  
 Пошаговое руководство начинается с создания проектов.  
  
#### <a name="to-create-the-vsix-project"></a>Создание проекта VSIX  
  
1.  Запустите [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  В строке меню выберите **Файл**, **Создать**, **Проект**.  
  
3.  В **новый проект** диалогового окна разверните **Visual C#** или **Visual Basic** узлов и нажмите кнопку **расширяемости** узла.  
  
    > [!NOTE]  
    >  **Расширяемости** узел доступен, только если установлен пакет SDK для Visual Studio. Дополнительные сведения см. в разделе предварительных требований этого раздела.  
  
4.  В верхней части диалогового окна выберите **.NET Framework 4.5** в списке версий .NET Framework.  
  
5.  Выберите **проект VSIX** шаблона, имя проекта **WebPartNode**и нажмите кнопку **ОК** кнопки.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Добавляет **WebPartNode** проекта **обозревателе решений**.  
  
#### <a name="to-create-the-extension-project"></a>Создание проекта расширения  
  
1.  В **обозреватель решений**откройте контекстное меню узла решения, выберите **добавить**, а затем выберите **новый проект**.  
  
2.  В **новый проект** диалогового окна разверните **Visual C#** узел или **Visual Basic** узел, а затем нажмите **Windows** узла.  
  
3.  В верхней части диалогового окна выберите **.NET Framework 4.5** в списке версий .NET Framework.  
  
4.  В списке шаблонов проектов выберите **библиотеки классов**, присвойте проекту имя **WebPartNodeExtension**, а затем выберите **ОК** кнопки.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Добавляет **WebPartNodeExtension** в решение проект и открывает файл кода по умолчанию Class1.  
  
5.  Удалите файл Class1 код из проекта.  
  
#### <a name="to-create-the-sharepoint-commands-project"></a>Чтобы создать проект команды SharePoint  
  
1.  В **обозреватель решений**откройте контекстное меню узла решения, выберите **добавить**, а затем выберите **новый проект**.  
  
2.  В **новый проект** диалогового окна разверните **Visual C#** узел или **Visual Basic** узел и выберите **Windows** узла.  
  
3.  В верхней части диалогового окна выберите **.NET Framework 3.5** в списке версий .NET Framework.  
  
4.  
  
5.  В списке шаблонов проектов выберите **библиотеки классов**, присвойте проекту имя **WebPartCommands**, а затем выберите **ОК** кнопки.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Добавляет **WebPartCommands** в решение проект и открывает файл кода по умолчанию Class1.  
  
6.  Удалите файл Class1 код из проекта.  
  
## <a name="configuring-the-projects"></a>Настройка проектов  
 Перед написанием кода для создания расширения необходимо добавить файлы кода и ссылок на сборки и настроить параметры проекта.  
  
#### <a name="to-configure-the-webpartnodeextension-project"></a>Настройка проекта WebPartNodeExtension  
  
1.  Добавьте в проект WebPartNodeExtension, четырех файлов кода, которые имеют следующие имена:  
  
    -   SiteNodeExtension  
  
    -   WebPartNodeTypeProvider  
  
    -   WebPartNodeInfo  
  
    -   WebPartCommandIds  
  
2.  Откройте контекстное меню для **WebPartNodeExtension** проекта, а затем выберите **добавить ссылку**.  
  
3.  В **диспетчер ссылок - WebPartNodeExtension** диалогового окна выберите **Framework** вкладку, а затем установите флажок для каждого из следующих сборок:  
  
    -   System.ComponentModel.Composition  
  
    -   System.Windows.Forms.  
  
4.  Выберите **расширения** , установите флажок для сборки Microsoft.VisualStudio.SharePoint и нажмите кнопку **ОК** кнопки.  
  
5.  В **обозревателе решений**, откройте контекстное меню для **WebPartNodeExtension** узел проекта, а затем выберите **свойства**.  
  
     Открывается **Конструктор проектов**.  
  
6.  Перейдите на вкладку **Приложение**.  
  
7.  В **пространство имен по умолчанию** поле (C#) или **корневое пространство имен** поле ([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]), введите **ServerExplorer.SharePointConnections.WebPartNode**.  
  
#### <a name="to-configure-the-webpartcommands-project"></a>Чтобы настроить проект WebPartCommands  
  
1.  Добавьте в проект WebPartCommands, файл кода, который называется WebPartCommands.  
  
2.  В **обозревателе решений**, откройте контекстное меню для **WebPartCommands** узел проекта, выберите **добавить**, а затем выберите **существующий элемент**.  
  
3.  В **Добавление существующего элемента** диалоговое окно, перейдите в папку, содержащую файлы кода для проекта WebPartNodeExtension и выберите WebPartNodeInfo и WebPartCommandIds файлы кода.  
  
4.  Щелкните стрелку рядом с **добавить** , а затем кнопку **ссылку Добавить** в появившемся меню.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Добавляет файлы кода в проект WebPartCommands как ссылки. В результате файлы кода находятся в проекте WebPartNodeExtension, но код в файлы также компилируются в проекте WebPartCommands.  
  
5.  Откройте контекстное меню для **WebPartCommands** проект еще раз и кнопку **добавить ссылку**.  
  
6.  В **диспетчер ссылок - WebPartCommands** диалогового окна выберите **расширения** , установите флажок для каждого из следующих сборок и нажмите кнопку **ОК** кнопки:  
  
    -   Microsoft.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
7.  В **обозревателе решений**, откройте контекстное меню для **WebPartCommands** проекта еще раз, а затем выберите **свойства**.  
  
     Открывается **Конструктор проектов**.  
  
8.  Перейдите на вкладку **Приложение**.  
  
9. В **пространство имен по умолчанию** поле (C#) или **корневое пространство имен** поле ([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]), введите **ServerExplorer.SharePointConnections.WebPartNode**.  
  
## <a name="creating-icons-for-the-new-nodes"></a>Создание значков для новых узлов  
 Создайте два значка для **обозревателя серверов** расширение: значок для нового **коллекции веб-частей** узла и еще один значок для каждого дочернего узла веб-части, в разделе **коллекции веб-частей** узел. Далее в этом пошаговом руководстве будет написан код, связывающий эти значки с узлами.  
  
#### <a name="to-create-icons-for-the-nodes"></a>Создание значков для узлов  
  
1.  В **обозревателе решений**, откройте контекстное меню для **WebPartNodeExtension** проекта, а затем выберите **свойства**.  
  
2.  Открывается **Конструктор проектов**.  
  
3.  Выберите **ресурсов** , а затем выберите **этот проект не содержит файл ресурсов по умолчанию. Щелкните здесь, чтобы создать его** ссылку.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Создает файл ресурсов и открывает его в конструкторе.  
  
4.  В верхней части конструктора, щелкните стрелку рядом с **добавить ресурс** меню команды, а затем выберите **добавить новый значок** в появившемся меню.  
  
5.  В **добавить новый ресурс** диалоговом имя нового значка **WebPartsNode**и нажмите кнопку **добавить** кнопки.  
  
     Значок «Создать» открывается в **редактора изображений**.  
  
6.  Измените версию 16 x 16 значка, чтобы он имеет вид, который вы легко узнаете.  
  
7.  Откройте контекстное меню для значка версии 32 x 32, а затем выберите **удалить тип изображения**.  
  
8.  Повторите шаги с 5 по 8, чтобы добавить второй значок в ресурсы проекта и назовите этот значок **веб-части**.  
  
9. В **обозревателе решений**в разделе **ресурсов** папку для **WebPartNodeExtension** проекта, откройте контекстное меню для **WebPartsNode.ico**.  
  
10. В **свойства** окно, щелкните стрелку рядом с **действие при построении**и нажмите кнопку **внедренный ресурс** в появившемся меню.  
  
11. Повторите последние два шага для **значка WebPart.ico**.  
  
## <a name="adding-the-web-part-gallery-node-to-server-explorer"></a>Добавление узла коллекции веб-частей в обозреватель серверов  
 Создайте класс, который добавляет новый **коллекции веб-частей** узла к каждому узлу с сайта SharePoint. Для добавления нового узла класс реализует <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> интерфейса. Реализуйте этот интерфейс, каждый раз, когда требуется расширить поведение существующий узел в **обозревателя серверов**, таких как добавление дочернего узла на узел.  
  
#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>Добавление узла коллекции веб-частей в обозреватель серверов  
  
1.  В проекте WebPartNodeExtension откройте файл кода SiteNodeExtension и вставьте в него следующий код.  
  
    > [!NOTE]  
    >  Добавьте следующий код, проект будет содержать ошибки компиляции, но они будут исчезнуть при добавлении кода в последующих шагах.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/sitenodeextension.vb#1)]  
  
## <a name="defining-a-node-type-that-represents-a-web-part"></a>Определение типа узла, представляющий веб-части  
 Создайте класс, который определяет новый тип узла, представляющий веб-часть. Visual Studio использует этот новый тип узла для отображения дочерних узлов в **коллекции веб-частей** узла. Каждый дочерний узел представляет одну веб-часть на сайте SharePoint.  
  
 Для определения нового типа узлов, этот класс реализует <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> интерфейса. Реализуйте этот интерфейс, каждый раз, когда требуется определить новый тип узла в **обозревателя серверов**.  
  
#### <a name="to-define-the-web-part-node-type"></a>Чтобы определить тип узла веб-части  
  
1.  В проекте WebPartNodeExtension откройте файл кода WebPartNodeTypeProvder и вставьте в него следующий код.  
  
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb#2)]
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodetypeprovider.cs#2)]  
  
## <a name="defining-the-web-part-data-class"></a>Определение класса данных части Web  
 Определите класс, содержащий данные об одной веб-части на сайте SharePoint. Далее в этом пошаговом руководстве вы создадите настраиваемую команду SharePoint, который получает данные о каждой веб-части на узле, а затем назначает данные экземпляры этого класса.  
  
#### <a name="to-define-the-web-part-data-class"></a>Определение класса данных веб-части  
  
1.  В проекте WebPartNodeExtension откройте файл кода WebPartNodeInfo и вставьте в него следующий код.  
  
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodeinfo.vb#3)]
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodeinfo.cs#3)]  
  
## <a name="defining-the-ids-for-the-sharepoint-command"></a>Определение идентификаторов для команды SharePoint  
 Определите несколько строк, которые определяют пользовательские команды SharePoint. Эти команды будут реализованы далее в этом пошаговом руководстве.  
  
#### <a name="to-define-the-command-ids"></a>Для определения идентификаторов команд  
  
1.  В проекте WebPartNodeExtension откройте файл кода WebPartCommandIds и вставьте в него следующий код.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartcommandids.cs#4)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartcommandids.vb#4)]  
  
## <a name="creating-the-custom-sharepoint-commands"></a>Создание команд пользовательские SharePoint  
 Создание пользовательских команд, которые вызывают серверную объектную модель для SharePoint, чтобы получить данные о веб-частей на сайте SharePoint. Каждая команда является метод, имеющий <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> применяемый к нему.  
  
#### <a name="to-define-the-sharepoint-commands"></a>Для определения команды SharePoint  
  
1.  В проекте WebPartCommands откройте файл кода WebPartCommands и вставьте в него следующий код.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../sharepoint/codesnippet/CSharp/WebPartNode/WebPartCommands/WebPartCommands.cs#6)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartcommands/webpartcommands.vb#6)]  
  
## <a name="checkpoint"></a>Контрольная точка  
 На этом этапе в пошаговом руководстве, весь код **коллекции веб-частей** узла и команд SharePoint теперь находятся в проекты. Постройте решение, чтобы убедиться в том, что оба проекта компилируется без ошибок.  
  
#### <a name="to-build-the-solution"></a>Построение решения  
  
1.  В строке меню последовательно выберите **Сборка**и **Собрать решение**.  
  
    > [!WARNING]  
    >  На этом этапе проекта WebPartNode могут иметь ошибка сборки, так как значение не указано в файле манифеста VSIX для автора. Эта ошибка исчезнет при добавлении значения в последующих шагах.  
  
## <a name="creating-a-vsix-package-to-deploy-the-extension"></a>Создание пакета VSIX для развертывания расширения  
 Для развертывания расширения, используйте проект VSIX в решении для создания пакета VSIX. Во-первых настройте пакет VSIX, изменив файл source.extension.vsixmanifest в проекте VSIX. Затем создайте пакет VSIX с построением решения.  
  
#### <a name="to-configure-the-vsix-package"></a>Настройка пакета VSIX  
  
1.  В **обозревателе решений**, в узле проекта WebPartNode откройте **source.extension.vsixmanifest** файл в редакторе манифестов.  
  
     Файл source.extension.vsixmanifest является основой для файл extension.vsixmanifest, требующий все пакеты VSIX. Дополнительные сведения об этом файле см. в разделе [ссылки 1.0 схемы расширения VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  В **название продукта** введите **узел коллекции веб-частей для обозревателя серверов**.  
  
3.  В **автор** введите **Contoso**.  
  
4.  В **описание** введите **добавляет пользовательский узел коллекции веб-частей узла подключений SharePoint в обозревателе сервера. Это расширение использует настраиваемую команду SharePoint для вызова объектной модели сервера.**  
  
5.  Выберите **активы** вкладка редактора и выберите **New** кнопки.  
  
     **Добавить новый актив** откроется диалоговое окно.  
  
6.  В **тип** выберите **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Это значение соответствует `MefComponent` элемент в файл extension.vsixmanifest. Этот элемент задает имя сборки расширения в пакете VSIX. Дополнительные сведения см. в разделе [MEFComponent элемент (Схема VSX)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
7.  В **источника** выберите **проект в текущем решении**.  
  
8.  В **проекта** выберите **WebPartNodeExtension** и выберите **ОК** кнопки.  
  
9. В редакторе манифеста выберите **New** еще раз.  
  
     **Добавить новый актив** откроется диалоговое окно.  
  
10. В **тип** введите **SharePoint.Commands.v4**.  
  
    > [!NOTE]  
    >  Этот элемент задает пользовательский модуль, который требуется включить в расширение Visual Studio. Дополнительные сведения см. в разделе [активов элемент (Схема VSX)](http://msdn.microsoft.com/en-us/9fcfc098-edc7-484b-9d4c-acd17829d737).  
  
11. В **источника** выберите **проект в текущем решении** элемента списка.  
  
12. В **проекта** выберите **WebPartCommands**, а затем выберите **ОК** кнопки.  
  
13. В строке меню выберите **построения**, **построить решение**, а затем убедитесь, что решение компилируется без ошибок.  
  
14. Убедитесь, что в выходную папку построения для проекта WebPartNode теперь содержит файл WebPartNode.vsix.  
  
     По умолчанию является выходной папке сборки... папку \bin\debug в папке, содержащей файл проекта.  
  
## <a name="testing-the-extension"></a>Тестирование расширения  
 Теперь вы готовы для тестирования нового **коллекции веб-частей** узел в **обозревателя серверов**. Начните отладку расширения в экспериментальном экземпляре Visual Studio. Затем с помощью нового **веб-части** узел в экспериментальном экземпляре [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
#### <a name="to-start-debugging-the-extension"></a>Чтобы начать отладку расширения  
  
1.  Перезапустите [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] с учетными данными администратора и откройте решение WebPartNode.  
  
2.  В проекте WebPartNodeExtension, откройте файл кода SiteNodeExtension и затем добавьте точку останова в первой строке кода в `NodeChildrenRequested` и `CreateWebPartNodes` методы.  
  
3.  Нажмите клавишу F5, чтобы начать отладку.  
  
     Visual Studio устанавливает расширение для %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web расширение узла коллекции частей для Explorer\1.0 сервера и запуске экспериментального экземпляра Visual Studio. В этом экземпляре Visual Studio будет тестировать элемент проекта.  
  
#### <a name="to-test-the-extension"></a>Чтобы проверить расширение  
  
1.  В экспериментальном экземпляре [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], в строке меню выберите **представление**, **обозревателя серверов**.  
  
2.  Выполните следующие действия, если сайт SharePoint, который будет использоваться для тестирования не отображается в списке **подключения SharePoint** узел в **обозревателя серверов**:  
  
    1.  В **обозревателя серверов**, откройте контекстное меню для **подключения SharePoint**, а затем выберите **добавить подключение**.  
  
    2.  В **Добавление подключения SharePoint** диалоговом окне введите URL-адрес сайта SharePoint, к которому требуется подключиться, а затем выберите **ОК** кнопки.  
  
         Чтобы указать сайт SharePoint на компьютере разработчика, введите **http://localhost**.  
  
3.  Разверните узел подключения (в котором отображается URL-адрес вашего сайта) и разверните дочерний узел сайта (например, **узла группы**).  
  
4.  Убедитесь, что код в другом экземпляре [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] останавливается в точке останова, заданной ранее в `NodeChildrenRequested` метода, а затем нажмите F5, чтобы продолжить отладку проекта.  
  
5.  В экспериментальном экземпляре Visual Studio, убедитесь, что новый узел с именем **коллекции веб-частей** появится в узле сайта верхнего уровня, а затем разверните **коллекции веб-частей** узла.  
  
6.  Убедитесь, что код в другом экземпляре Visual Studio прервано на точке останова, заданной ранее в `CreateWebPartNodes` метода, а затем нажмите клавишу F5, чтобы продолжить отладку проекта.  
  
7.  В экспериментальном экземпляре Visual Studio, убедитесь, что все веб-части на подключенном сайте отображаются под **коллекции веб-частей** узел в **обозревателя серверов**.  
  
8.  В **обозревателя серверов**, откройте контекстное меню для одного из веб-части и выберите **свойства**.  
  
9. В экземпляре [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] выполняется отладка, убедитесь, что отображаются сведения о веб-часть в **свойства** окна.  
  
## <a name="uninstalling-the-extension-from-visual-studio"></a>При удалении расширения из Visual Studio  
 После завершения тестирования расширения, удалите расширение из Visual Studio.  
  
#### <a name="to-uninstall-the-extension"></a>Удаление расширения  
  
1.  В экспериментальном экземпляре [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], в строке меню выберите **средства**, **расширения и обновления**.  
  
     Появится диалоговое окно **Расширения и обновления**.  
  
2.  В списке расширений выберите **расширение узла коллекции веб-частей для обозревателя серверов**и нажмите кнопку **удаления** кнопки.  
  
3.  В появившемся диалоговом окне, выберите **Да** кнопку, чтобы убедиться, что вы хотите удалить расширение, а затем выберите **Перезагрузить сейчас** кнопку, чтобы завершить удаление.  
  
4.  Закройте оба экземпляра Visual Studio (экспериментальный экземпляр и экземпляр Visual Studio, в котором открыт решение WebPartNode).  
  
## <a name="see-also"></a>См. также  
 [Расширение узла подключений SharePoint в обозревателе серверов](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Пошаговое руководство: Вызов клиентской объектной модели SharePoint в расширении обозревателя серверов](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)   
 [Редактор изображений для значков](/cpp/windows/image-editor-for-icons)   
 [Создание значка или другого изображения &#40;редактор изображений для значков&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)  
  
  