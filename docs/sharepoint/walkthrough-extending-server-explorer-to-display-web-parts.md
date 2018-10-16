---
title: 'Пошаговое руководство: Расширение обозревателя сервера для отображения веб-частей | Документация Майкрософт'
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
ms.openlocfilehash: 84060ed018059f4b067b4744465bf4116f72841b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "42634742"
---
# <a name="walkthrough-extend-server-explorer-to-display-web-parts"></a>Пошаговое руководство: Расширение обозревателя сервера для отображения веб-частей
  В Visual Studio, можно использовать **подключения SharePoint** узел **обозревателя серверов** для просмотра компонентов на сайтах SharePoint. Тем не менее **обозревателя серверов** не отображать некоторые компоненты по умолчанию. В этом пошаговом руководстве, вы расширите **обозревателя серверов** , чтобы он отображал галерею веб-частей на каждый из которых подключен сайта SharePoint.  
  
 В этом пошаговом руководстве описаны следующие задачи.  
  
-   Создание расширения Visual Studio, который расширяет **обозревателя серверов** одним из следующих способов:  
  
    -   Добавляет расширение **коллекции веб-частей** в узле каждого узла сайта SharePoint в **обозревателя серверов**. Этот новый узел содержит дочерние узлы, представляющие каждый веб-части в галерею веб-частей на сайте.  
  
    -   Расширение определяет новый тип узла, представляющий экземпляр веб-части. Этот новый тип узла является основой для дочерних узлов нового **коллекции веб-частей** узла. Новый тип узла для веб-часть отображает сведения в **свойства** окно веб-части, который он представляет. Тип узла также включает элемент пользовательского контекстного меню можно использовать в качестве отправной точки для выполнения других задач, связанных с веб-части.  
  
-   Создайте две настраиваемые команды SharePoint, которые вызывает сборку расширения. Команды SharePoint представляют собой методы, которые могут быть вызваны для сборки расширений для использования API в серверную объектную модель для SharePoint. В этом пошаговом руководстве создание команд, получить сведения о веб-части из локального сайта SharePoint на компьютере разработчика. Дополнительные сведения см. в разделе [вызова объектной модели SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
-   Построение пакета Visual Studio Extension (VSIX) для развертывания расширения.  
  
-   Отладка и тестирование расширения.  
  
> [!NOTE]  
>  Альтернативная версия данного пошагового руководства, использующего клиентскую объектную модель для SharePoint вместо его серверную объектную модель, см. в разделе [Пошаговое руководство: вызов клиентской объектной модели SharePoint в расширении обозревателя серверов](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md).  
  
## <a name="prerequisites"></a>Предварительные требования  
 Необходимы следующие компоненты на компьютере разработчика для выполнения этого пошагового руководства.  
  
-   Поддерживаемые версии Windows, SharePoint и Visual Studio.  
  
-   Visual Studio SDK. В этом пошаговом руководстве использует **проект VSIX** шаблона в пакете SDK для создания пакета VSIX для развертывания элемента проекта. Дополнительные сведения см. в разделе [расширения инструментов SharePoint в Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Знание следующие основные понятия будут полезны, но не требуется для выполнения данного пошагового руководства:  
  
-   Для SharePoint с помощью объектной модели сервера. Дополнительные сведения см. в разделе [использование объектной модели SharePoint Foundation на сервере](http://go.microsoft.com/fwlink/?LinkId=177796).  
  
-   Веб-частей в решениях SharePoint. Дополнительные сведения см. в разделе [Общие сведения о частях Web](http://go.microsoft.com/fwlink/?LinkId=177803).  
  
## <a name="create-the-projects"></a>Создание проектов
 Для выполнения этого пошагового руководства, необходимо создать три проекта:  
  
-   Проект VSIX, чтобы создать пакет VSIX для развертывания расширения.  
  
-   Проект библиотеки классов, реализующий расширение. Этот проект должен быть предназначен для .NET Framework 4.5.  
  
-   Проект библиотеки классов, который определяет настраиваемые команды SharePoint. Этот проект должен использовать.NET Framework 3.5.  
  
 Начало выполнения пошагового руководства по созданию проектов.  
  
#### <a name="to-create-the-vsix-project"></a>Создание проекта VSIX  
  
1.  Запустите [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  В строке меню выберите **Файл** > **Создать** > **Проект**.  
  
3.  В **новый проект** диалогового окна разверните узел **Visual C#** или **Visual Basic** узлов и нажмите кнопку **расширяемости** узла.  
  
    > [!NOTE]  
    >  **Расширяемости** узел доступен только в том случае, если установить пакет SDK для Visual Studio. Дополнительные сведения см. в разделе "Предварительные требования" ранее в этом разделе.  
  
4.  В верхней части диалоговое окно, выберите **.NET Framework 4.5** в списке версий .NET Framework.  
  
5.  Выберите **проект VSIX** шаблон, имя проекта **WebPartNode**, а затем выберите **ОК** кнопки.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Добавляет **WebPartNode** проект **обозревателе решений**.  
  
#### <a name="to-create-the-extension-project"></a>Создание проекта расширения  
  
1.  В **обозревателе решений**, откройте контекстное меню узла решения, выберите **добавить**, а затем выберите **новый проект**.  
  
2.  В **новый проект** диалогового окна разверните узел **Visual C#** узел или **Visual Basic** узел, а затем выберите **Windows** узла.  
  
3.  В верхней части диалоговое окно, выберите **.NET Framework 4.5** в списке версий .NET Framework.  
  
4.  В списке шаблонов проектов выберите **библиотеки классов**, назовите проект **WebPartNodeExtension**, а затем выберите **ОК** кнопки.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Добавляет **WebPartNodeExtension** проекта в решение и открывает файл кода по умолчанию Class1.  
  
5.  Удалите файл Class1 код из проекта.  
  
#### <a name="to-create-the-sharepoint-commands-project"></a>Чтобы создать проект команды SharePoint  
  
1.  В **обозревателе решений**, откройте контекстное меню узла решения, выберите **добавить**, а затем выберите **новый проект**.  
  
2.  В **новый проект** диалогового окна разверните узел **Visual C#** узел или **Visual Basic** узел и нажмите кнопку **Windows** узла.  
  
3.  В верхней части диалоговое окно, выберите **.NET Framework 3.5** в списке версий .NET Framework.  
  
4.  В списке шаблонов проектов выберите **библиотеки классов**, назовите проект **WebPartCommands**, а затем выберите **ОК** кнопки.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Добавляет **WebPartCommands** проекта в решение и открывает файл кода по умолчанию Class1.  
  
5.  Удалите файл Class1 код из проекта.  
  
## <a name="configure-the-projects"></a>Настройка проектов
 Перед написанием кода для создания расширения, необходимо добавить файлы кода и ссылки на сборки и настроить параметры проекта.  
  
#### <a name="to-configure-the-webpartnodeextension-project"></a>Чтобы настроить проект WebPartNodeExtension
  
1.  Добавьте в проект WebPartNodeExtension, четырех файлов кода, которые имеют следующие имена:  
  
    -   SiteNodeExtension  
  
    -   WebPartNodeTypeProvider  
  
    -   WebPartNodeInfo  
  
    -   WebPartCommandIds  
  
2.  Откройте контекстное меню для **WebPartNodeExtension** проекта, а затем выберите **добавить ссылку**.  
  
3.  В **диспетчер ссылок - WebPartNodeExtension** диалоговое окно, выберите **Framework** вкладку, а затем установите флажок для каждого из следующих сборок:  
  
    -   System.ComponentModel.Composition  
  
    -   System.Windows.Forms.  
  
4.  Выберите **расширения** вкладке, установите флажок для сборки Microsoft.VisualStudio.SharePoint и затем выберите **ОК** кнопки.  
  
5.  В **обозревателе решений**, откройте контекстное меню для **WebPartNodeExtension** узел проекта, а затем выберите **свойства**.  
  
     Открывается **Конструктор проектов**.  
  
6.  Перейдите на вкладку **Приложение**.  
  
7.  В **пространство имен по умолчанию** поле (C#) или **корневое пространство имен** поле ([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]), введите **ServerExplorer.SharePointConnections.WebPartNode**.  
  
#### <a name="to-configure-the-webpartcommands-project"></a>Чтобы настроить проект webpartcommands
  
1.  В проекте WebPartCommands добавьте файл кода, который называется WebPartCommands.  
  
2.  В **обозревателе решений**, откройте контекстное меню для **WebPartCommands** узел проекта, выберите **добавить**, а затем выберите **существующий элемент**.  
  
3.  В **добавить существующий элемент** диалоговом окне перейдите к папке, содержащей файлы кода для проекта WebPartNodeExtension и выберите WebPartNodeInfo и WebPartCommandIds файлы кода.  
  
4.  Выберите стрелку рядом с пунктом **добавить** кнопку, а затем выберите **добавить как ссылку** в появившемся меню.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Добавляет файлы кода в проект WebPartCommands как ссылки. Таким образом файлы кода, находятся в проекте WebPartNodeExtension, но код в файлы также компилируются в проекте WebPartCommands.  
  
5.  Откройте контекстное меню для **WebPartCommands** проекта еще раз и выберите **добавить ссылку**.  
  
6.  В **диспетчер ссылок - WebPartCommands** диалоговое окно, выберите **расширения** вкладке, установите флажок для каждого из следующих сборок и затем выберите **ОК** кнопка:  
  
    -   Microsoft.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
7.  В **обозревателе решений**, откройте контекстное меню для **WebPartCommands** проект еще раз, а затем выберите **свойства**.  
  
     Открывается **Конструктор проектов**.  
  
8.  Перейдите на вкладку **Приложение**.  
  
9. В **пространство имен по умолчанию** поле (C#) или **корневое пространство имен** поле ([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]), введите **ServerExplorer.SharePointConnections.WebPartNode**.  
  
## <a name="create-icons-for-the-new-nodes"></a>Создание значков для новых узлов
 Создайте два значка для **обозревателя серверов** расширения: значок для нового **коллекции веб-частей** узел и еще один значок для каждого дочернего узла веб-часть, в разделе **коллекции веб-частей** узел. Далее в этом пошаговом руководстве вы напишете код, который связывает эти значки с узлами.  
  
#### <a name="to-create-icons-for-the-nodes"></a>Создание значков для узлов  
  
1.  В **обозревателе решений**, откройте контекстное меню для **WebPartNodeExtension** проекта, а затем выберите **свойства**.  
  
2.  Открывается **Конструктор проектов**.  
  
3.  Выберите **ресурсы** вкладке, а затем выберите **этот проект содержит файл ресурсов по умолчанию. Щелкните здесь, чтобы создать ее** ссылку.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Создает файл ресурсов и открывает его в конструкторе.  
  
4.  В верхней части конструктора, щелкните стрелку рядом с полем **добавить ресурс** меню команды, а затем выберите **добавить новый значок** в появившемся меню.  
  
5.  В **добавления нового ресурса** диалоговом окне имя значок "Создать" **WebPartsNode**, а затем выберите **добавить** кнопки.  
  
     Значок "Создать" откроется в **редактор изображений**.  
  
6.  Измените версию значок 16 x 16, таким образом, чтобы он имеет вид, который можно легко распознать.  
  
7.  Откройте контекстное меню для значка версии 32 x 32, а затем выберите **удалить тип изображения**.  
  
8.  Повторите шаги с 5 по 8, чтобы добавить второй значок ресурсы проекта и назовите этот значок **WebPart**.  
  
9. В **обозревателе решений**в разделе **ресурсы** папку для **WebPartNodeExtension** проекта, откройте контекстное меню для **WebPartsNode.ico**.  
  
10. В **свойства** окно, выберите стрелку рядом с пунктом **действие при построении**и нажмите кнопку **внедренный ресурс** в появившемся меню.  
  
11. Повторите последние два шага для **значка WebPart.ico**.  
  
## <a name="add-the-web-part-gallery-node-to-server-explorer"></a>Добавить узел коллекции веб-частей в обозревателе серверов
 Создайте класс, который добавляет новый **коллекции веб-частей** узел на каждый узел сайта SharePoint. Чтобы добавить новый узел, этот класс реализует <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> интерфейс. Реализуйте этот интерфейс, каждый раз, когда вы хотите расширить поведение существующего узла в **обозревателя серверов**, таких как добавление дочернего узла на узел.  
  
#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>Чтобы добавить узел коллекции веб-частей в обозревателе серверов
  
1.  В проекте WebPartNodeExtension откройте файл кода SiteNodeExtension и вставьте в него следующий код.  
  
    > [!NOTE]  
    >  После добавьте следующий код, проект будет содержать некоторые ошибки компиляции, но они будут исчезнуть при добавлении кода в последующих шагах.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/sitenodeextension.vb#1)]  
  
## <a name="define-a-node-type-that-represents-a-web-part"></a>Определение типа узла, который представляет веб-части
 Создайте класс, определяющий новый тип узла, представляющий веб-часть. Visual Studio использует этот новый тип узла для отображения дочерних узлов в **коллекции веб-частей** узла. Каждый дочерний узел представляет один веб-часть на сайте SharePoint.  
  
 Чтобы определить новый тип узла, этот класс реализует <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> интерфейс. Реализуйте этот интерфейс, каждый раз, когда требуется определить новый тип узла в **обозревателя серверов**.  
  
#### <a name="to-define-the-web-part-node-type"></a>Чтобы определить тип узла часть web
  
1.  В проекте WebPartNodeExtension откройте файл кода WebPartNodeTypeProvder и вставьте в него следующий код.  
  
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb#2)]
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodetypeprovider.cs#2)]  
  
## <a name="define-the-web-part-data-class"></a>Определение класса web part данных
 Определите класс, содержащий данные об одном веб-часть на сайте SharePoint. Далее в этом пошаговом руководстве вы создадите настраиваемую команду SharePoint, который извлекает данные о каждой веб-части на узле, а затем назначает данные экземпляры этого класса.  
  
#### <a name="to-define-the-web-part-data-class"></a>Для определения класса web part данных
  
1.  В проекте WebPartNodeExtension откройте файл кода WebPartNodeInfo и вставьте в него следующий код.  
  
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodeinfo.vb#3)]
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodeinfo.cs#3)]  
  
## <a name="define-the-ids-for-the-sharepoint-commands"></a>Определение идентификаторов для команды SharePoint
 Определите несколько строк, идентифицирующих настраиваемые команды SharePoint. Эти команды будут реализованы позже в этом пошаговом руководстве.  
  
#### <a name="to-define-the-command-ids"></a>Чтобы определить идентификаторы команд
  
1.  В проекте WebPartNodeExtension откройте файл кода WebPartCommandIds и вставьте в него следующий код.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartcommandids.cs#4)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartcommandids.vb#4)]  
  
## <a name="create-the-custom-sharepoint-commands"></a>Создавать настраиваемые команды SharePoint
 Создание пользовательских команд, которые вызывают серверную объектную модель для SharePoint для получения данных о веб-частей на сайте SharePoint. Каждая команда представляет метод, имеющий <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> примененных к нему.  
  
#### <a name="to-define-the-sharepoint-commands"></a>Для определения команды SharePoint  
  
1.  В проекте WebPartCommands откройте файл кода WebPartCommands и вставьте в него следующий код.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../sharepoint/codesnippet/CSharp/WebPartNode/WebPartCommands/WebPartCommands.cs#6)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartcommands/webpartcommands.vb#6)]  
  
## <a name="checkpoint"></a>Контрольная точка  
 На этом этапе в этом пошаговом руководстве, весь код для **коллекции веб-частей** узел и команды SharePoint, теперь в проектах. Постройте решение, чтобы убедиться, что оба проекта компилируется без ошибок.  
  
#### <a name="to-build-the-solution"></a>Построение решения  
  
1.  В строке меню последовательно выберите **Сборка**  >  **Собрать решение**.  
  
    > [!WARNING]  
    >  На этом этапе проекта WebPartNode могут иметь ошибка сборки, так как файл манифеста VSIX не имеет значения для автора. Эта ошибка исчезнет при добавлении значения в последующих шагах.  
  
## <a name="create-a-vsix-package-to-deploy-the-extension"></a>Создание пакета VSIX для развертывания расширения
 Чтобы развернуть расширение, используйте проекта VSIX в решении для создания пакета VSIX. Во-первых настройте пакет VSIX, изменив файл source.extension.vsixmanifest проекта VSIX. Затем создайте пакет VSIX, построения решения.  
  
#### <a name="to-configure-the-vsix-package"></a>Чтобы настроить пакет VSIX  
  
1.  В **обозревателе решений**, разверните проект WebPartNode, откройте **source.extension.vsixmanifest** файл в редакторе манифестов.  
  
     Файл source.extension.vsixmanifest является основой для файл extension.vsixmanifest, требующий всех пакетов VSIX. Дополнительные сведения об этом файле см. в разделе [Справочник по схеме 1.0 VSIX расширения](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  В **название продукта** введите **узел коллекции веб-частей для обозревателя серверов**.  
  
3.  В **автор** введите **Contoso**.  
  
4.  В **описание** введите **добавляет пользовательский узел коллекции веб-частей узла подключений SharePoint в обозревателе серверов. Это расширение использует настраиваемую команду SharePoint для вызова серверной объектной модели.**  
  
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
    >  Этот элемент задает пользовательское расширение, которое вы хотите включить в расширение Visual Studio. Дополнительные сведения см. в разделе [активов элемент (Схема VSX)](http://msdn.microsoft.com/en-us/9fcfc098-edc7-484b-9d4c-acd17829d737).  
  
11. В **источника** выберите **проект в текущем решении** элемента списка.  
  
12. В **проекта** выберите **WebPartCommands**, а затем выберите **ОК** кнопки.  
  
13. В строке меню выберите **построения** > **построить решение**и убедитесь, что решение компилируется без ошибок.  
  
14. Убедитесь, что в выходную папку построения для проекта WebPartNode теперь содержит файл WebPartNode.vsix.  
  
     По умолчанию является выходной папке сборки... папку \bin\debug в папке, содержащей файл проекта.  
  
## <a name="test-the-extension"></a>Тестирование расширения
 Теперь вы готовы к тестированию новый **коллекции веб-частей** узел в **обозревателя серверов**. Начните отладку расширения в экспериментальном экземпляре Visual Studio. Затем с помощью нового **веб-частей** узел в экспериментальном экземпляре [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
#### <a name="to-start-debugging-the-extension"></a>Чтобы начать отладку расширения  
  
1.  Перезапустите [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] с учетными данными администратора, а затем откройте решение WebPartNode.  
  
2.  В проекте WebPartNodeExtension, откройте файл кода SiteNodeExtension и затем добавьте точку останова в первой строке кода в `NodeChildrenRequested` и `CreateWebPartNodes` методы.  
  
3.  Выберите **F5** клавишу, чтобы начать отладку.  
  
     Visual Studio устанавливает расширение для %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web расширение узла коллекции частей для сервера Explorer\1.0 и запускает экспериментальный экземпляр Visual Studio. Элемент проекта будут тестироваться в этот экземпляр Visual Studio.  
  
#### <a name="to-test-the-extension"></a>Чтобы проверить расширение  
  
1.  В экспериментальном экземпляре [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], в строке меню выберите **представление** > **обозревателя серверов**.  
  
2.  Выполните следующие действия, если сайт SharePoint, который вы хотите использовать для тестирования не отображается в разделе **подключения SharePoint** узел в **обозревателя серверов**:  
  
    1.  В **обозревателя серверов**, откройте контекстное меню для **подключения SharePoint**, а затем выберите **добавить подключение**.  
  
    2.  В **Добавление подключения SharePoint** диалоговом окне введите URL-адрес для сайта SharePoint, к которому вы хотите подключиться, а затем выберите **ОК** кнопки.  
  
         Чтобы указать сайт SharePoint на компьютере разработчика, введите **http://localhost**.  
  
3.  Разверните узел подключения (в котором отображаются URL-адрес сайта), а затем разверните дочерний узел узла (например, **сайт группы**).  
  
4.  Убедитесь, что код в другом экземпляре [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] останавливается на точке останова, заданной ранее в `NodeChildrenRequested` метод, а затем выберите **F5** продолжить отладку проекта.  
  
5.  В экспериментальном экземпляре Visual Studio, убедитесь, что новый узел с именем **коллекции веб-частей** появится в узле сайта верхнего уровня, а затем разверните **коллекции веб-частей** узла.  
  
6.  Убедитесь, что выполнение кода в другом экземпляре Visual Studio будет приостановлено в точке останова, заданной ранее в `CreateWebPartNodes` метод, а затем выберите **F5** клавишу, чтобы продолжить отладку проекта.  
  
7.  В экспериментальном экземпляре Visual Studio, убедитесь, что все веб-части на подключенном сайте отображаются в разделе **коллекции веб-частей** узел в **обозревателя серверов**.  
  
8.  В **обозревателя серверов**, откройте контекстное меню для одного из веб-частей и затем выберите **свойства**.  
  
9. В экземпляре [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] отлаживаемое, убедитесь, что сведения о веб-части отображаются в **свойства** окна.  
  
## <a name="uninstall-the-extension-from-visual-studio"></a>Удалите расширение из Visual Studio
 После завершения тестирования расширения, удалите расширение из Visual Studio.  
  
#### <a name="to-uninstall-the-extension"></a>Удаление расширения  
  
1.  В экспериментальном экземпляре [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], в строке меню выберите **средства** > **расширения и обновления**.  
  
     Появится диалоговое окно **Расширения и обновления**.  
  
2.  В список расширений, выберите **расширение узла коллекции веб-частей для обозревателя серверов**, а затем выберите **удаления** кнопки.  
  
3.  В появившемся диалоговом окне, выберите **Да** кнопку, чтобы убедиться, что вы хотите удалить расширение, а затем выберите **Перезагрузить сейчас** кнопку, чтобы завершить удаление.  
  
4.  Закройте оба экземпляра Visual Studio (экспериментальный экземпляр и экземпляр Visual Studio, в котором открыто решение WebPartNode).  
  
## <a name="see-also"></a>См. также
 [Расширение узла подключений SharePoint в обозревателе серверов](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Пошаговое руководство: Вызов клиентской объектной модели SharePoint в расширении обозревателя серверов](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)   
 [Редактор изображений для значков](/cpp/windows/image-editor-for-icons)   
 [Создание значка или другого изображения &#40;редактор изображений для значков&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)  
  
