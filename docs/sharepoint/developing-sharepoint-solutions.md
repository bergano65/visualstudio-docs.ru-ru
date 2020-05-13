---
title: Разработка решений SharePoint | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.ProjectProperties
- VS.SharePointTools.Project.ProjectItemProperties
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, overview
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d7670f05fbeced78a0c77a8ffc053cf6b607708f
ms.sourcegitcommit: da5ebc29544fdbdf625ab4922c9777faf2bcae4a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/29/2020
ms.locfileid: "82586895"
---
# <a name="develop-sharepoint-solutions"></a>Разработка решений SharePoint
  В [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] имеется несколько шаблонов типов проектов SharePoint для создания сайтов SharePoint и элементов сайтов. Список доступных типов проектов см. в разделе [шаблоны проектов и элементов проектов SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md). Далее следует описание элементов и свойств проекта SharePoint.

 Сведения о SharePoint 2013 и надстройках SharePoint см. в разделах [SharePoint 2013](https://www.microsoft.com/microsoft-365/previous-versions/microsoft-sharepoint-2013) и [Сборка надстроек SharePoint](/sharepoint/dev/sp-add-ins/sharepoint-add-ins).

## <a name="elements-of-a-sharepoint-project"></a>Элементы проекта SharePoint
 Узлы в проекте SharePoint называются *элементами SharePoint*. Элементы SharePoint также могут содержать один или несколько вложенных файлов, называемых *файлами элементов SharePoint*, например файлы конфигурации [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] , формы ASPX и другие.

 Вместо создания проекта с помощью шаблона с уже имеющимися файлами элементов проекта можно воспользоваться шаблоном **Пустой проект** , чтобы создать новый проект SharePoint и затем добавить элементы проекта вручную. Проекты SharePoint могут также дополнительно содержать один или несколько файлов функций (для активации в SharePoint) и файл пакета для распространения проекта.

### <a name="special-nodes"></a>Специальные узлы
 Каждый проект SharePoint содержит два узла, которые нельзя переименовывать, удалять, вырезать, копировать и перетаскивать из проекта. Это узлы:

- Компоненты
- Пакет

  Оба эти узла всегда присутствуют в проекте SharePoint, даже если никакие другие компоненты и пакеты не определены в проекте.

#### <a name="features-node"></a>Узел "компоненты"
 Узел **Функции** содержит одну или несколько функций проекта SharePoint. Функция — это контейнер расширений для SharePoint. После развертывания функции на сервере SharePoint она может быть включена в список определений сайтов или активирована индивидуально администраторами SharePoint на сайтах SharePoint. Дополнительные сведения см. в разделе [Работа с компонентами](/previous-versions/office/developer/sharepoint-2010/ms460318(v=office.14)).

 При добавлении элемента, например типа содержимого или экземпляра списка, в проект SharePoint он добавляется в функцию в узле **Функции** . Область элемента определяет, куда добавляется элемент: в новую или существующую функцию. Если область нового элемента совпадает с областью существующей функции, он добавляется в эту функцию. В противном случае элемент добавляется в новую функцию.

 Чтобы добавить функцию вручную, выберите команду **Добавить функцию** из контекстного меню узла функции. Вы можете просмотреть или изменить содержимое функции с помощью конструктора функций. Дополнительные сведения см. [в разделе руководство. Настройка компонента SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md).

 Когда функция добавляется в проект SharePoint, она появляется в **обозревателе решений** в виде узла с заданным по умолчанию именем Feature*x*.feature, где *x* — уникальный номер. После развертывания функции на сервере SharePoint администратор SharePoint может активировать ее, тем самым сделав ее доступной для пользователей сайта SharePoint.

#### <a name="package-node"></a>Узел пакета
 Узел **Пакет** содержит один файл, который реализует механизм распространения проекта SharePoint. Этот файл, называемый *пакетом решения*, имеет значение. На основе CAB-файла с. Расширение WSP. Пакет решения является файлом развертывания и повторного использования, который содержит набор функций, определений сайтов и сборок, применимых к сайтам SharePoint, которые можно включать и отключать индивидуально. Узел **Пакет** также всегда содержит файл с именем Package.wspdef — файл определения [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] для пакета. После развертывания пакета на сервере, где выполняется SharePoint, администратор SharePoint может установить его и активировать его функции.

 Содержимое пакета можно просмотреть или изменить в конструкторе пакетов, дважды щелкнув узел пакета или открыв его контекстное меню и выбрав **Открыть**. Дополнительные сведения см. в разделе [Создание пакетов решений SharePoint](../sharepoint/creating-sharepoint-solution-packages.md).

## <a name="sharepoint-project-and-project-item-properties"></a>Свойства проекта и элемента проекта SharePoint
 Свойства проектов SharePoint, так же как и свойства других проектов [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , отображаются в окне «Свойства» и на странице свойств. Отображаемые свойства зависят от того, какой узел выбран.

 При выборе проекта SharePoint, элемента проекта или узла файла элемента проекта в **обозревателе решений**в окне «Свойства» или на странице свойств отображаются следующие свойства:

### <a name="project-properties"></a>Свойства проекта

|Имя свойства|Описание|
|-------------------|-----------------|
|Активная конфигурация развертывания|Указывает ряд шагов, выполненных в процессе развертывания. Дополнительные сведения см. [в разделе инструкции. изменение конфигурации развертывания SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).|
|Место развертывания сборки|Определяет, где находятся *сборки приложения SharePoint* . Допустимое расположение сборок: либо *GlobalAssemblyCache* (по умолчанию), либо *WebApplication*.<br /><br /> Если свойству *Sandboxed Solution* присвоено значение **true**, это свойство отключается.|
|Автоматически отозвать после отладки|Указывает, должно ли развернутое решение автоматически отзываться из SharePoint после выполнения приложения в режиме отладки в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Если параметр выбран, решение отзывается, когда интегрированная среда разработки возвращается в режим конструктора после отладки. Если параметр не выбран, решение не отзывается. Дополнительные сведения см. в разделе [Отзыв решения](/previous-versions/office/developer/sharepoint-2010/aa543958(v=office.14)).|
|Изменить конфигурации|Задает конфигурацию развертывания для проекта. Дополнительные сведения см. [в разделе как изменить конфигурацию развертывания SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) и [развернуть, опубликовать и обновить пакеты решений SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).|
|Включить отладку Silverlight (вместо отладки скриптов)|Если выбран этот параметр, к процессу отладки присоединяется отладчик Silverlight. Если параметр не выбран, к процессу отладки присоединяется отладчик скриптов. Дополнительные сведения см. в разделе [Общие сведения об отладке Silverlight](/previous-versions/windows/).|
|Включить сборку в пакет|Указывает, должна ли сборка проекта включаться в пакет во время построения.|
|Строка команды после развертывания|Задает команды, выполняемые после развертывания решения SharePoint. Эта строка поддерживает любые пакетные команды, а также разрешение переменных MSBuild. Для получения дополнительной информации см. [How to: Set SharePoint Deployment Commands](../sharepoint/how-to-set-sharepoint-deployment-commands.md).|
|Строка команды до развертывания|Задает команды, выполняемые до развертывания решения SharePoint. Эта строка поддерживает любые пакетные команды, а также разрешение переменных MSBuild. Для получения дополнительной информации см. [How to: Set SharePoint Deployment Commands](../sharepoint/how-to-set-sharepoint-deployment-commands.md).|
|Файл проекта|Имя файла, содержащего сведения о сборке и конфигурации, а также другую информацию о проекте.|
|Папка проекта|Расположение файла проекта в системе. (только для чтения).|
|Sandboxed Solution|Указывает, должен ли проект развертываться как *изолированное решение*, называемое также *пользовательским решением*. Изолированные решения не всегда являются доверенными. Значение **true** означает, что проект развертывается как изолированное решение, значение **false** означает, что проект развертывается как решение фермы. Дополнительные сведения см. в разделах [Sandboxed Solution Considerations](../sharepoint/sandboxed-solution-considerations.md) и [Differences Between Sandboxed and Farm Solutions](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).|
|URL-адрес сайта|Указывает [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] конечного сайта для этого проекта.|
|Автозапускаемый элемент|Указывает первый элемент в проекте, который должен быть запущен.|

 При выборе файла элемента SharePoint (например, рабочего процесса или функции в узле «Функции») в окне «Свойства» отображаются следующие свойства:

### <a name="project-item-properties"></a>Свойства элемента проекта

|Имя свойства|Описание|
|-------------------|-----------------|
|Устранение конфликта развертывания|Указывает действие к исполнению при развертывании элемента проекта, свойства которого идентичны свойствам элемента, уже существующего на сервере. Для получения дополнительной информации см. [Troubleshooting SharePoint Packaging and Deployment](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).|
|Свойства функций|Задает набор значений (сохраняемых в виде пар «ключ — значение»), который включается в состав функции при ее развертывании в SharePoint. После развертывания функции значения свойств можно использовать в коде. Дополнительные сведения см. в разделе [Providing Packaging and Deployment Information in Project Items](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|
|Приемник компонента|Предоставляет код, который выполняется при возникновении определенных событий для элемента проекта, содержащего функцию. Дополнительные сведения см. в разделе [Providing Packaging and Deployment Information in Project Items](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|
|Имя папки|Имя папки элемента проекта SharePoint.|
|Выходные ссылки проекта|Задает зависимость, например сборку, которую должен запустить элемент проекта. Дополнительные сведения см. в разделе [Providing Packaging and Deployment Information in Project Items](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|
|Записи безопасных элементов управления|Задает элементы управления, к которым можно безопасно открыть доступ для редактирования пользователям, не являющимся доверенными. Дополнительные сведения см. в разделе [Providing Packaging and Deployment Information in Project Items](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|

### <a name="project-item-file-properties"></a>Свойства файла элемента проекта

|Имя свойства|Описание|
|-------------------|-----------------|
|Действие построения|Определяет, как файл связан с процессами сборки и развертывания. Дополнительные сведения см. в разделе [Свойства файлов](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\)).|
|Копировать в выходной каталог|Указывает, будет ли файл (файлы) исходного кода скопирован в выходной каталог. Может иметь одно из следующих значений:<br /><br /> -   *Не копировать*<br />-   *Всегда копировать*<br />-   *Копировать, если новее*<br /><br /> Дополнительные сведения см. в разделе [Свойства файлов](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\)).|
|Пользовательский инструмент|Задает имя инструмента, если таковой имеется, преобразующего файл во время разработки и помещающего результат преобразования в другой файл. Например, файл набора данных (.[!INCLUDE[TLA2#tla_xsd](../sharepoint/includes/tla2sharptla-xsd-md.md)]) имеет пользовательский инструмент по умолчанию. Дополнительные сведения см. в разделе [Свойства файлов](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\)).|
|Пространство имен пользовательского инструмента|Пространство имен, в которое копируются выходные данные пользовательского инструмента. Дополнительные сведения см. в разделе [Свойства файлов](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\)).|
|Расположение развертывания|Полный путь к файлу на сервере SharePoint. Этот путь состоит из корневого каталога развертывания и вложенных свойств пути развертывания.|
|Путь развертывания|Относительный путь к файлу на сервере SharePoint, например Workflow1\\. Полный путь к файлу создается путем объединения значения *Deployment Path* со значением *Deployment Root* до конца.<br /><br /> Выбор значения *RootFile* для свойства *тип развертывания* приводит к изменению свойства *Root для развертывания* на \<SharePointRoot>\\, что приводит к полному пути \<SharePointRoot> \Workflow1.\\ Дополнительные сведения см. в разделе [Упаковка и развертывание решений SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md).|
|Deployment Root|Строка. Корневая папка, в которой файл развертывается на сервере SharePoint. Например, \<SharePointRoot> \TEMPLATE\FEATURES\\\<FeatureName>\\.<br /><br /> Значение свойства *Deployment Root* определяется параметром *Deployment Type* .|
|Тип развертывания|Тип развертывания файла, определяющий его значение *Deployment Root* . Может иметь одно из следующих значений:<br /><br /> Развертывание: * \<нет значения>*<br /><br /> ElementManifest: * \<SharePointRoot> \TEMPLATE\FEATURES\\\<FeatureName>*\\<br /><br /> ElementFile: * \<SharePointRoot> \TEMPLATE\FEATURES\\\<FeatureName>\\*<br /><br /> TemplateFile: * \<SharePointRoot> \TEMPLATE\\*<br /><br /> RootFile: * \<SharePointRoot>\\*<br /><br /> Глобалресаурце: * \<SharePointRoot> \ресаурцес\\*<br /><br /> ClassResource: * \<классресаурцепас>\\*<br /><br /> Для получения дополнительной информации см. <xref:Microsoft.VisualStudio.SharePoint.DeploymentType>.|
|Имя файла|Имя файла или папки для файла элемента.|
|Полный путь|Расположение файла для элемента. (только для чтения).|

## <a name="related-topics"></a>См. также

|Заголовок|Описание|
|-----------|-----------------|
|[Шаблоны проектов и элементов проектов SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md)|Описание шаблонов проектов и элементов проектов SharePoint, доступных в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].|
|[Практическое руководство. Добавление элементов в проект SharePoint](../sharepoint/how-to-add-items-to-a-sharepoint-project.md)|Описание процедуры добавления новых или существующих элементов в проект SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .|
|[Пошаговое руководство. Создание столбца сайта, типа содержимого и списка для SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)|Описание по шагам процедуры создания настраиваемого поля, типа содержимого, определения списка и экземпляра списка.|
|[Как создать приемник событий](../sharepoint/how-to-create-an-event-receiver.md)|Описывает добавление приемника событий для проекта, созданного в [разделе Пошаговое руководство: Создание столбца сайта, типа содержимого и списка для SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).|
|[Создание решений для рабочих процессов SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)|Описание процедуры создания проектов рабочих процессов, включающее формы сопоставления и формы запуска рабочих процессов.|
|[Создание страниц для SharePoint](../sharepoint/creating-pages-for-sharepoint.md)|Описание процедуры создания страниц, например страниц приложений, страниц сайтов, эталонных страниц и макетов страниц для SharePoint.|
|[Создание веб-частей для SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)|Описание процедуры добавления элементов управления, позволяющих пользователям напрямую изменять содержимое, внешний вид и поведение страниц сайта SharePoint с помощью браузера.|
|[Создание многократно используемых элементов управления для веб-частей или страниц приложений](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|Описание процедуры создания пользовательских элементов управления, которые можно размещать на страницах приложений и в веб-частях, используемых в SharePoint.|
|[Интеграция бизнес-данных в SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)|Описание процедуры интеграции данных, полученных из веб-служб и серверных приложений, в приложения SharePoint.|
|[Создание определений сайтов для SharePoint](../sharepoint/creating-site-definitions-for-sharepoint.md)|Описание процедуры создания определений сайтов — шаблонов, которые используются для создания сайтов SharePoint.|
|[Импорт элементов из существующего сайта SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)|Описание процедуры импорта элементов, например типов содержимого и модулей, из существующего сайта SharePoint в проект SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .|
|[Использование модулей для включения файлов в решение](../sharepoint/using-modules-to-include-files-in-the-solution.md)|Описание способа использования модулей для развертывания файлов из проекта [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] на сайт SharePoint.|
|[Просмотр подключений SharePoint с помощью обозреватель сервера](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)|Описание способа просмотра локальных сайтов SharePoint с помощью обозревателя серверов.|
|[Предоставление сведений об упаковке и развертывании в элементах проекта](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)|Описание способа использования свойств элементов проекта для предоставления сведений об упаковке и развертывании для проектов, например записей безопасных элементов управления, выходных ссылок проекта и свойств функций.|
|[Как добавлять и удалять сопоставленные папки](../sharepoint/how-to-add-and-remove-mapped-folders.md)|Описание процедуры добавления в проект сопоставленных папок для более удобного доступа к ресурсам SharePoint.|
|[Рекомендации по изолированным решениям](../sharepoint/sandboxed-solution-considerations.md)|Описание проблем, связанных с изолированными решениями.|
|[Безопасность решений SharePoint](../sharepoint/security-for-sharepoint-solutions.md)|Рассмотрение вопросов безопасности при разработке решений SharePoint в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].|
|[Диалоговое окно выбора URL-адреса &#40;разработки SharePoint в Visual Studio&#41;](../sharepoint/url-picker-dialog-box-sharepoint-development-in-visual-studio.md)|Описание диалогового окна, которое можно использовать для добавления ссылок в виде путей к ресурсам в проекте или на локальном сервере SharePoint.|

## <a name="see-also"></a>См. также раздел
- [Приступая к работе &#40;разработке решений SharePoint в Visual Studio&#41;](../sharepoint/getting-started-sharepoint-development-in-visual-studio.md)
- [Просмотр подключений SharePoint с помощью обозреватель сервера](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
- [Сборка и отладка решений SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Упаковка и развертывание решений SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
