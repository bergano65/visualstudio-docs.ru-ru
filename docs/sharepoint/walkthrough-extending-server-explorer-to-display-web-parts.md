---
title: "Walkthrough: Extending Server Explorer to Display Web Parts | Microsoft Docs"
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
  - "SharePoint Connections [SharePoint development in Visual Studio], extending a node"
  - "SharePoint commands"
  - "SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer"
  - "SharePoint Connections [SharePoint development in Visual Studio], creating a new node type"
ms.assetid: 5b1f104a-0eaf-4929-9f1f-d7afcfc8b707
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# Walkthrough: Extending Server Explorer to Display Web Parts
  В Visual Studio можно использовать узел **Подключения SharePointОбозреватель серверов** чтобы просмотреть компоненты на сайтах SharePoint.  Однако **Обозреватель серверов** не отображается по умолчанию нескольких компонентов.  В этом пошаговом руководстве, можно расширить функциональные **Обозреватель серверов** таким образом, чтобы он отображает коллекцию веб\-части для каждого подключенном сайте SharePoint.  
  
 В этом пошаговом руководстве показано выполнение следующих задач.  
  
-   Создание расширения Visual Studio, которое следующим образом расширяет **Обозреватель серверов**:  
  
    -   Расширение добавляет узел **Коллекция веб\-части** под каждым узлом сайта SharePoint в **Обозреватель серверов**.  Этот новый узел содержит дочерние узлы, представляющие каждую из веб\-частей в коллекции веб\-частей на сайте;  
  
    -   Расширение определяет новый тип узла, который представляет экземпляр веб\-части.  Этот новый узел является базовым для дочерних узлов нового узла **Коллекция веб\-частей**.  Новый тип узла веб\-части в окне **Свойства** отображает сведения о веб\-части, которую он представляет.  Тип узла также включает пользовательский элемент контекстного меню, который можно использовать в качестве отправной точки для выполнения других задач, относящихся к веб\-части.  
  
-   Создание настраиваемых команд SharePoint 2, которая вызывает сборку модуля.  Команды SharePoint методы, которые могут быть Вызываются сборок модуля для использования API объектной модели сервера для SharePoint.  В этом пошаговом руководстве описывается создание команд, извлекающих сведения о веб\-части из локального сайта SharePoint на компьютере разработчика.  Дополнительные сведения см. в разделе [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
-   Построение пакета расширения Visual Studio \(VSIX\) для расширения.  
  
-   Отладка и тестирование расширения.  
  
> [!NOTE]  
>  Для другой версии данного пошагового руководства, использующего объектную модель " клиент " для SharePoint вместо его объектной модели сервера см. в разделе [Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md).  
  
## Обязательные компоненты  
 Для выполнения данного пошагового руководства на компьютере разработчика должны быть установлены следующие компоненты:  
  
-   Поддерживаемые выпуски Windows, SharePoint и Visual Studio.  Дополнительные сведения см. в разделе [Требования по разработке решений SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Пакет SDK для Visual Studio.  В этом пошаговом руководстве шаблон **Проект VSIX** из пакета SDK используется для создания пакета VSIX, который служит для развертывания элемента проекта.  Дополнительные сведения см. в разделе [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Знание следующих подходов может оказаться полезным, но не требуется для выполнения пошагового руководства.  
  
-   Использование объектной модели сервера для SharePoint.  Дополнительные сведения см. в разделе [Using the SharePoint Foundation Server\-Side Object Model](http://go.microsoft.com/fwlink/?LinkId=177796).  
  
-   веб\-части в решениях SharePoint.  Дополнительные сведения см. в разделе [Web Parts Overview](http://go.microsoft.com/fwlink/?LinkId=177803).  
  
## Создание проектов  
 Чтобы выполнить это пошаговое руководство, необходимо создать project 3:  
  
-   проект VSIX, который позволит создать пакет VSIX для развертывания расширения;  
  
-   проект библиотеки классов, реализующий расширение  Этот проект должен ПУСТО платформы .NET Framework 4,5.  
  
-   проект библиотеки классов, определяющий пользовательские команды SharePoint  \(в этом проекте необходимо использовать .NET Framework 3.5\).  
  
 Начните выполнение пошагового руководства с создания проектов.  
  
#### Создание проекта VSIX  
  
1.  Запустите [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  В строке меню выберите **Файл**, **Создать**, **Проект**.  
  
3.  В диалоговом окне  **Создать проект** разверните узлы **Visual C\#** или **Visual Basic**, а затем выберите узел **Расширение среды**.  
  
    > [!NOTE]  
    >  Узел **Расширение среды** доступен, только если установить пакет SDK для Visual Studio.  Дополнительные сведения см. в параграфе предварительных требований ранее в этом разделе.  
  
4.  В верхней части диалогового окна, выберите **платформа .NET Framework 4,5** в списке версий платформы .NET Framework.  
  
5.  Выберите шаблон **Проект VSIX**, назовите проект **WebPartNode**, а затем нажмите кнопку **ОК**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] добавит в **Обозреватель решений** проект **WebPartNode**.  
  
#### Создание проекта расширения  
  
1.  В **Обозреватель решений** открыть контекстное меню для узла решения выберите **Добавить**, а затем выберите **Создать проект**.  
  
    > [!NOTE]  
    >  В проектах Visual Basic узел решения отображается в **обозревателе решений**, только если в диалоговом окне ["Общие", страница "Проекты и решения", диалоговое окно "Параметры"](http://msdn.microsoft.com/ru-ru/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca) установлен флажок **Всегда показывать решение**.  
  
2.  В диалоговом окне **Создать проект** разверните узел **Visual C\#** или узел **Visual Basic**, а затем выбрать узел **Окна**.  
  
3.  В верхней части диалогового окна, выберите **платформа .NET Framework 4,5** в списке версий платформы .NET Framework.  
  
4.  В списке шаблонов проектов выберите **Библиотека классов**, назовите проект **WebPartNodeExtension**, а затем нажмите кнопку **ОК**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] добавит проект **WebPartNodeExtension** в решение и откроет заданный по умолчанию файл с кодом Class1.  
  
5.  Удалите из проекта файл c кодом Class1.  
  
#### Создание проекта команд SharePoint  
  
1.  В **Обозреватель решений** открыть контекстное меню для узла решения выберите **Добавить**, а затем выберите **Создать проект**.  
  
    > [!NOTE]  
    >  В проектах Visual Basic узел решения отображается в **обозревателе решений**, только если в диалоговом окне ["Общие", страница "Проекты и решения", диалоговое окно "Параметры"](http://msdn.microsoft.com/ru-ru/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca) установлен флажок **Всегда показывать решение**.  
  
2.  В диалоговом окне  **Создать проект** разверните узел **Visual C\#** или узел **Visual Basic**, а затем выберите узел **Окна**.  
  
3.  В верхней части диалогового окна, выберите **.NET Framework 3.5** в списке версий платформы .NET Framework.  
  
4.  В списке шаблонов проектов выберите **Библиотека классов**, назовите проект **WebPartCommands**, а затем нажмите кнопку **ОК**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] добавит проект **WebPartCommands** в решение и откроет файл с кодом по умолчанию Class1.  
  
5.  Удалите из проекта файл c кодом Class1.  
  
## Настройка проектов  
 Перед разработкой кода для создания расширения, необходимо добавить ссылки на файлы с кодом и на сборки, а также настроить параметры проекта.  
  
#### Настройка проекта WebPartNodeExtension  
  
1.  В проекте WebPartNodeExtension добавьте 4 файла с кодом, имеющие следующие имена:  
  
    -   SiteNodeExtension  
  
    -   WebPartNodeTypeProvider  
  
    -   WebPartNodeInfo  
  
    -   WebPartCommandIds  
  
2.  Открыть контекстное меню для проекта **WebPartNodeExtension**, а затем выберите **Добавить ссылку**.  
  
3.  В диалоговом окне **Диспетчер ссылок – WebPartNodeExtension** выберите вкладку **Платформа**, а затем установите флажок для каждой из следующих сборок:  
  
    -   System.ComponentModel.Composition  
  
    -   System.Windows.Forms  
  
4.  Выберите вкладку **Расширения** установите флажок для сборки Microsoft.VisualStudio.SharePoint, а затем нажмите кнопку **ОК**.  
  
5.  В **Обозреватель решений** открыть контекстное меню для узла проекта **WebPartNodeExtension**, а затем выберите **Свойства**.  
  
     Откроется **Конструктор проектов**.  
  
6.  Выберите вкладку **Приложение**.  
  
7.  В окне **Пространство имен по умолчанию** \(C\#\) или в окне **Корневое пространство имен** \([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]\) введите **ServerExplorer.SharePointConnections.WebPartNode**.  
  
#### Настройка проекта WebPartCommands  
  
1.  В проекте WebPartCommands добавьте файл кода с именем WebPartCommands.  
  
2.  В **Обозреватель решений** открыть контекстное меню для узла проекта **WebPartCommands** выберите **Добавить**, а затем выберите **Существующий элемент**.  
  
3.  В диалоговом окне **Добавление существующего элемента** перейдите к папке, содержащей файлы с кодом проекта WebPartNodeExtension, а затем выберите файлы с кодом WebPartNodeInfo и WebPartCommandIds.  
  
4.  Нажмите стрелку рядом с кнопкой **Добавить**, а затем выберите **Добавить как связь** в появившемся меню.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] добавит файлы с кодом в проект WebPartCommands в виде ссылок.  В результате файлы кода найдены в проекте WebPartNodeExtension, но код в файлах также компилироваться в проекте WebPartCommands.  
  
5.  Раскрывайте контекстное меню для проекта **WebPartCommands** еще раз и выберите **Добавить ссылку**.  
  
6.  В диалоговом окне **Диспетчер ссылок – WebPartCommands** выберите вкладку **Расширения** установите флажок для каждой из следующих сборок, а затем нажмите кнопку **ОК**:  
  
    -   Microsoft.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
7.  В **Обозреватель решений**, раскрывайте контекстное меню для проекта **WebPartCommands**, а затем выберите **Свойства**.  
  
     Откроется **Конструктор проектов**.  
  
8.  Выберите вкладку  **Приложение**.  
  
9. В окне **Пространство имен по умолчанию** \(C\#\) или в окне **Корневое пространство имен** \([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]\) введите **ServerExplorer.SharePointConnections.WebPartNode**.  
  
## Создание значков для новых узлов  
 Создайте два значка для расширений **обозревателя серверов**: значок для нового узла **Коллекция веб\-частей** и еще один значок для каждого дочернего узла веб\-части внутри узла **Коллекция веб\-частей**.  Далее в этом пошаговом руководстве будет показано, как написать код, связывающий эти значки с узлами.  
  
#### Создание значков для узлов  
  
1.  В **Обозреватель решений** открыть контекстное меню для проекта **WebPartNodeExtension**, а затем выберите **Свойства**.  
  
2.  Откроется **Конструктор проектов**.  
  
3.  Выберите  **вкладку ресурсов**, а затем выберите  **этот проект не содержит файла ресурсов по умолчанию. Щелкните здесь, чтобы создать одну** связь.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] создает файл ресурсов и открытые в конструкторе.  
  
4.  В верхней части конструктора выберите стрелку рядом с командой меню **Добавить ресурс**, а затем выберите **Добавить новый значок** в появившемся меню.  
  
5.  В диалоговом окне **Добавление нового ресурса**, назовите новый значок **WebPartsNode**, а затем нажмите кнопку **Добавить**.  
  
     Новый значок будет отрыт в **Редакторе изображений**.  
  
6.  Правка версия значок 16x16, чтобы он будет содержать конструкцию, которую можно легко распознать.  
  
7.  Открыть контекстное меню для версии значка размером 32x32, а затем выберите **Удалить тип изображений**.  
  
8.  Повторяющиеся секции 5 до 8, чтобы добавить второй значок к ресурсам проект и назовите этот значок **WebPart**.  
  
9. В **Обозреватель решений** в папке **Ресурсы** для проекта **WebPartNodeExtension** открыть контекстное меню для **WebPartsNode.ico**.  
  
10. В окне **Свойства** нажмите стрелку рядом с **Действие при построении**, а затем выберите **Внедренный ресурс** в появившемся меню.  
  
11. Повторите последние два шага для значка **WebPart.ico**.  
  
## Добавление узла коллекции веб\-частей в обозреватель серверов  
 Создайте класс, который добавляет новый узел **Коллекция веб\-частей** в узел каждого из сайтов SharePoint.  Для добавления нового узла класс реализует интерфейс <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>.  Этот интерфейс следует реализовывать всякий раз, когда требуется расширить поведение существующего узла в **Обозреватель серверов**, как добавить дочерний узел к узлу.  
  
#### Добавление узла коллекции веб\-частей в обозреватель серверов  
  
1.  В проекте WebPartNodeExtension, откройте файл с кодом SiteNodeExtension, а затем вставьте в нее следующий код.  
  
    > [!NOTE]  
    >  После добавления этого кода, проект будет иметь некоторые компилировать ошибок, но они пойдут прочь при добавлении кода в последующих шагах.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/CS/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/vb/webpartnodeextension/sitenodeextension.vb#1)]  
  
## Определение типа узла, представляющего веб\-часть  
 Создайте класс, который определяет новый тип узла, представляющий веб\-часть.  Visual Studio использует этот новый тип узла, чтобы отобразить дочерние узлы под узлом **Коллекция веб\-части**.  Каждый дочерний узел представляет отдельный " веб\-часть " на сайте SharePoint.  
  
 Для определения нового типа узла класс реализует интерфейс <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>.  Этот интерфейс следует реализовывать всякий раз, когда требуется определить новый тип узла в **обозревателе серверов**.  
  
#### Определение типа узла веб\-части  
  
1.  В проекте WebPartNodeExtension, откройте файл кода WebPartNodeTypeProvder, а затем вставьте в нее следующий код.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/CS/webpartnodeextension/webpartnodetypeprovider.cs#2)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/vb/webpartnodeextension/webpartnodetypeprovider.vb#2)]  
  
## Определение класса данных веб\-части  
 Определите класс, содержащий сведения об отдельной веб\-части сайта SharePoint.  Далее в этом пошаговом руководстве показано создание пользовательской команды SharePoint, которая получает данные о каждом веб\-части на сайте, а затем присвоить данные в экземпляры этого класса.  
  
#### Определение класса данных веб\-части  
  
1.  В проекте WebPartNodeExtension, откройте файл с кодом WebPartNodeInfo и вставьте в нее следующий код.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/CS/webpartnodeextension/webpartnodeinfo.cs#3)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/vb/webpartnodeextension/webpartnodeinfo.vb#3)]  
  
## Определение идентификаторов для команды SharePoint  
 Определите несколько строк, идентифицирующих настраиваемые команды SharePoint.  Эти команды будут реализованы далее в данном пошаговом руководстве.  
  
#### Определение идентификаторов команд  
  
1.  В проекте WebPartNodeExtension, откройте файл с кодом WebPartCommandIds, а затем вставьте в нее следующий код.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/CS/webpartnodeextension/webpartcommandids.cs#4)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/vb/webpartnodeextension/webpartcommandids.vb#4)]  
  
## Создание настраиваемых команд SharePoint  
 Создание пользовательских команд, осуществляющих вызовы в объектную модель сервера SharePoint для получения данных о веб\-части на сайте SharePoint.  Каждая из команд представляет собой метод, к которому применяется атрибут <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute>.  
  
#### Определение команд SharePoint  
  
1.  В проекте WebPartCommands откройте файл с кодом WebPartCommands, а затем вставьте в нее следующий код.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/CS/WebPartCommands/WebPartCommands.cs#6)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/vb/webpartcommands/webpartcommands.vb#6)]  
  
## Контрольная точка  
 На данный момент проекты содержат весь код узла **Коллекция веб\-частей** и команд SharePoint.  Выполните построение решения, чтобы убедиться, что компиляция обоих проектов выполняется без ошибок.  
  
#### Построение решения  
  
1.  В строке меню выберите **Построение**, **Построить решение**.  
  
    > [!WARNING]  
    >  На этом этапе проекта WebPartNode может иметь ошибку построения, поскольку файл манифеста VSIX не имеет значения для автора.  Эта ошибка будет направлена прочь при добавлении значение в последующих шагах.  
  
## Создание пакета VSIX для развертывания расширения  
 Для развертывания расширения воспользуйтесь проектом VSIX в своем решении для создания пакета VSIX.  Сначала настроить пакет VSIX, изменив файл source.extension.vsixmanifest в проекте VSIX.  Затем создайте пакет VSIX, выполнив построение решения.  
  
#### Настройка пакета VSIX  
  
1.  В **Обозреватель решений** под проектом WebPartNode, откройте файл **source.extension.vsixmanifest** в редакторе манифестов.  
  
     Файл source.extension.vsixmanifest качестве основы для файла extension.vsixmanifest которого все пакеты VSIX.  Дополнительные сведения об этом файле см. в разделе [Справочник по схеме расширения VSIX](http://msdn.microsoft.com/ru-ru/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  В окне **Название продукта** введите **Узел коллекции веб\-части для обозревателя серверов**.  
  
3.  В окне **Автор** введите **Contoso**.  
  
4.  В  **поле описание** введите добавить  **пользовательский узел коллекции веб\-части в узле подключения SharePoint в обозревателе сервера. Для вызова серверной объектной модели расширение использует настраиваемую команду SharePoint.**  
  
5.  Выберите вкладку **Активы** редактор, а затем нажмите кнопку **Создать**.  
  
     Диалоговое окно **Добавить новый актив**.  
  
6.  В списке **Тип** выберите **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Это значение соответствует элементу `MefComponent`, описанному в файле extension.vsixmanifest.  Этот элемент задает имя сборки расширения в пакете VSIX.  Дополнительные сведения см. в разделе [NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/ru-ru/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
7.  В списке **Источник** выберите **Проект в текущем решении**.  
  
8.  В списке **Проект** выберите **WebPartNodeExtension**, а затем нажмите кнопку **ОК**.  
  
9. В редакторе манифестов, нажмите кнопку **Создать** попытку.  
  
     Диалоговое окно **Добавить новый актив**.  
  
10. В окне **Тип** введите **SharePoint.Commands.v4**.  
  
    > [!NOTE]  
    >  Этот элемент задает настраиваемое расширение, которое требуется включить в расширение Visual Studio.  Дополнительные сведения см. в разделе [элемент актива \(схема VSX\)](http://msdn.microsoft.com/ru-ru/9fcfc098-edc7-484b-9d4c-acd17829d737).  
  
11. В списке **Источник** выберите элемент списка **Проект в текущем решении**.  
  
12. В списке **Проект** выберите **WebPartCommands**, а затем нажмите кнопку **ОК**.  
  
13. В строке меню выберите **Построение**, **Построить решение** и убедитесь, что решение будет компилироваться без ошибок.  
  
14. Убедитесь, что в выходную папку построения для проекта WebPartNode теперь содержит файл WebPartNode.vsix.  
  
     По умолчанию выходной папкой построения является папка ..  \\bin\\Debug, расположенная в папке, содержащей файл проекта.  
  
## Тестирование расширения  
 Теперь можно проверить новый узел **Коллекция веб\-части** в **Обозреватель серверов**.  Начните отладку расширения в экспериментальном экземпляре Visual Studio.  Затем перейдите к новому зулу **Веб\-части** в экспериментальном экземпляре [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
#### Запуск отладки расширения  
  
1.  Перезапустите [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] с учетными данными администратора, а затем откройте решение WebPartNode.  
  
2.  В проекте WebPartNodeExtension, откройте файл с кодом SiteNodeExtension, а затем добавьте точку останова на первой строке кода в методах `NodeChildrenRequested` и `CreateWebPartNodes`.  
  
3.  Выберите ключ F5, чтобы начать отладку.  
  
     Visual Studio устанавливает расширения до %UserProfile% \\ AppData \\ local \\ Microsoft \\ VisualStudio \\ 11.0Exp \\ extensions \\ Contoso \\ расширение узла коллекции веб\-части для обозревателя серверов \\ 1.0 и запускает экспериментальном экземпляре Visual Studio.  После этого можно тестировать элемент проекта в открытом экземпляре Visual Studio.  
  
#### Тестирование расширения  
  
1.  В экспериментальном экземпляре [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] в строке меню выберите **Вид**, **Обозреватель серверов**.  
  
2.  Выполните следующие действия, если сайт SharePoint, который необходимо использовать для тестирования не отображается в узле **Подключения SharePoint** в **Обозреватель серверов**:  
  
    1.  В **Обозреватель серверов** открыть контекстное меню для **Подключения SharePoint**, а затем выберите **Добавить подключение**.  
  
    2.  В диалоговом окне **Добавление подключения к SharePoint** введите URL\-адрес сайта SharePoint, к которому нужно подключиться, а затем нажмите кнопку **ОК**.  
  
         Чтобы указать сайт SharePoint на компьютере разработчика, введите **http:\/\/localhost**.  
  
3.  Разверните узел подключения сайта \(который указывает URL\-адрес вашего сайта\), а затем разверните узел подчиненного сайта \(например, **сайт группы**\).  
  
4.  Убедитесь, что выполнение кода в другом экземпляре [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] останавливается в точке останова установлено ранее в методе `NodeChildrenRequested`, а затем выбрать F5, чтобы продолжить отладку проекта.  
  
5.  В экспериментальном экземпляре Visual Studio, убедитесь, что новый узел с именем **Коллекция веб\-части** отображается в узле сайта верхнего уровня, а затем разверните узел **Коллекция веб\-части**.  
  
6.  Убедитесь, что выполнение кода в другом экземпляре Visual Studio прерывается на точке останова, которая имеет ранее в методе `CreateWebPartNodes`, а затем выбрать ключ F5, чтобы продолжить отладку проекта.  
  
7.  В экспериментальном экземпляре Visual Studio, убедитесь в том, что все веб\-части на подключенном сайте отображаются в узле **Коллекция веб\-части** в **Обозреватель серверов**.  
  
8.  В **Обозреватель серверов** открыть контекстное меню для одного из веб\-частей и выберите **Свойства**.  
  
9. В экземпляре [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], отладке, убедитесь, что сведения о веб\-части отображаются в окне **Свойства**.  
  
## Удаление расширения из Visual Studio  
 После тестирования расширения удалите его из Visual Studio.  
  
#### Удаление расширения  
  
1.  В экспериментальном экземпляре [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] в строке меню выберите **Сервис**, **Расширения и обновления**.  
  
     Будет открыто диалоговое окно **Расширения и обновления**.  
  
2.  В списке расширений выберите **Расширение узла коллекции веб\-части для обозревателя серверов**, а затем нажмите кнопку **Удалить**.  
  
3.  В появившемся диалоговом окне нажмите кнопку **Да**, чтобы подтвердить удаление расширения, а затем нажмите кнопку **Перезагрузить сейчас** для завершения удаления.  
  
4.  Закройте оба экземпляра Visual Studio \(экспериментальном экземпляра и экземпляр Visual Studio, в котором открыто решение WebPartNode\).  
  
## См. также  
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)   
 [Image Editor for Icons](/visual-cpp/windows/image-editor-for-icons)   
 [Creating an Icon or Other Image &#40;Image Editor for Icons&#41;](/visual-cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)  
  
  