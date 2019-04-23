---
title: Импорт элементов из существующего сайта SharePoint | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.WSPImport.SelectionDependency
- VS.SharepointTools.WSPImport.SpecifyProjectSource
- VS.SharePointTools.WSPImport.SelectionItemsToImport
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- SharePoint development in Visual Studio, importing .wsp files
- importing items [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 206cd77ae3c648add62b17c86a4966e6174c345c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60082585"
---
# <a name="import-items-from-an-existing-sharepoint-site"></a>Импорт элементов из существующего сайта SharePoint
  Шаблон проекта "Импорт пакета решения SharePoint" позволяет многократно использовать элементы, такие как типы контента и поля, из существующих сайтов SharePoint в новом решении SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Хотя большинство импортированных решений можно запускать без изменений, существуют некоторые ограничения и вопросы, которые необходимо учитывать, особенно если вы изменяете какие-либо элементы после их импорта.

> [!NOTE]
>  Для импорта многократно используемых рабочих процессов используйте шаблон проекта "Импорт рабочего процесса с возможностью повторного использования". [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Руководства по импорту многократно используемых рабочих процессов](../sharepoint/guidelines-for-importing-reusable-workflows.md).

## <a name="supported-sharepoint-solutions"></a>Поддерживаемые решения SharePoint
 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] полностью поддерживает импорт решений, созданных в [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] и [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)].

 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] не поддерживает импорт решений, созданных в следующих приложениях.

- [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)]

- [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)]

- [!INCLUDE[vs_orcas_long](../sharepoint/includes/vs-orcas-long-md.md)]

- Microsoft SharePoint Designer 2007

- [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)]

  Несмотря на то что зачастую удается успешно импортировать решения, созданные в этих приложениях, эта функциональность не протестирована и не поддерживается.

## <a name="item-import-restrictions"></a>Ограничения на импорт элементов
 Несмотря на то, что большинство элементов SharePoint можно импортировать из существующего *.wsp* файла, следующие элементы не поддерживаются и могут потребовать внесения изменений для правильной работы:

- сущности модели подключения к бизнес-данным;

- элементы сопоставления рабочего процесса кода;

- рабочие процессы кода;

- визуальные веб-части (ASCX-файлы);

- Веб-служб (*.asmx*)

- привязки типов контента;

- приемники событий;

- определения списков (шаблоны);

- определения сайтов.

  При экспорте решения из [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] или [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)], эти элементы автоматически исключаются из *.wsp* файл. Тем не менее другие *.wsp* файлы, созданные неподдерживаемыми инструментами, могут содержать эти элементы. (См. раздел "Поддерживаемые решения SharePoint" выше в этой статье.)

## <a name="what-happens-when-you-import-a-solution"></a>Что происходит при импорте решения
 При импорте решения с помощью шаблона "Импорт пакета решения SharePoint", [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] копирует все содержимое *.wsp* импорта файла и пытается согласовать и сохранить все ассоциации и ссылки между элементы и их файлов.

 Все импортированные элементы копируются в соответствующие папки в **обозревателе решений**. Например, типы контента отображаются в папке **Типы контента** , а экземпляры списков отображаются в папке **Экземпляры списка**. Файлы, связанные с импортированным элементом, также копируются в папку этого элемента. Например, импортированный экземпляр списка включает его модули, формы и страницы ASPX.

### <a name="dependent-items"></a>Зависимые элементы
 Если вы выбираете в мастере импорта пакета решения SharePoint элемент, но не его зависимые элементы, то выводится сообщение о том, что перед импортом необходимо также выбрать и зависимые элементы.

### <a name="what-are-features"></a>Что такое компоненты
 Пользователи SharePoint Designer могут увидеть неожиданные файлы, называемые *компонентами*, которые отображаются в импортированных решениях в **обозревателе решений** . Хотя компоненты существовали в решении SharePoint Designer, они были скрыты. Теперь компоненты отображаются в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

 Компоненты представляют собой контейнеры для элементов SharePoint. Каждый компонент хранит ссылки на все элементы, такие как типы контента и определения списков, которые он содержит. При импорте решения [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] устанавливает компоненты для всех импортированных элементов и старается поддерживать для файлов отношения "компонент-элемент". Все файлы, ссылки для которых не удалось разрешить, помещаются в папку **Прочие импортированные файлы** .

 Дополнительные сведения о функциях см. в разделе [решения разработки SharePoint](../sharepoint/developing-sharepoint-solutions.md) и [работа с компонентами](http://go.microsoft.com/fwlink/?LinkID=147704).

### <a name="handle-special-cases"></a>Обработка особых случаев
 В некоторых случаях Visual Studio не может согласовать элемент с его зависимыми файлами. Все файлы, которые [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] не удалось разрешить, отображаются в папке **Прочие импортированные файлы**. Кроме того, для их свойства **DeploymentType** устанавливается значение **NoDeployment** , чтобы они не были развернуты вместе с решением.

 Например, при импорте определения списка ExpenseForms определение списка с таким именем отобразится в разделе **список определений** папку в **обозревателе решений** вместе с его  *Elements.XML* и *Schema.xml* файлов. Однако его связанные формы ASPX и HTML могут быть помещены в папку с именем **ExpenseForms** в папке **Прочие импортированные файлы** . Чтобы завершить импорт, переместите эти файлы в определение списка ExpenseForms в **обозревателе решений** и измените значение свойства **DeploymentType** каждого файла с **NoDeployment** на **ElementFile**.

 При импорте приемников событий, *Elements.xml* файл копируется в правильное расположение, но необходимо вручную включить сборку в пакет решения, таким образом, чтобы она развертывалась с решением. [!INCLUDE[crabout](../sharepoint/includes/crabout-md.md)] как это сделать, см. в разделе [как: Добавление и удаление дополнительных сборок](../sharepoint/how-to-add-and-remove-additional-assemblies.md).

 При импорте рабочих процессов формы InfoPath копируются в папку **Прочие импортированные файлы** . Если *.wsp* файл содержит веб-шаблон, он устанавливается в качестве стартовой страницы в **обозревателе решений**.

## <a name="import-fields-and-property-bags"></a>Импорт полей и контейнеров свойств
 При импорте решения с несколькими полями все отдельные определения полей объединяются в единое *Elements.xml* файла в узле **обозревателе решений** вызывается **поля** . Аналогично, все записи контейнеров свойств объединяются в *Elements.xml* файла в узле с именем **PropertyBags**.

 Поля в SharePoint — это столбцы с указанным типом данных, таким как text, Boolean или lookup. Дополнительные сведения см. в разделе [стандартный блок: Столбцы и типы полей](http://go.microsoft.com/fwlink/?LinkId=182304). Контейнеры свойств позволяют добавлять свойства ко всем объектам в SharePoint, от фермы до списка, на сайте SharePoint. Контейнеры свойств реализованы в виде хэш-таблицы имен и значений свойств. Дополнительные сведения см. в разделе [Управление конфигурацией SharePoint](http://go.microsoft.com/fwlink/?LinkId=182296) или [Параметры свойств контейнера SharePoint](http://go.microsoft.com/fwlink/?LinkId=182297).

## <a name="delete-items-in-the-project"></a>Удаление элементов проекта
 Большинство элементов решений SharePoint имеет хотя бы один зависимый элемент. Например, экземпляры списка зависят от типов контента, а типы контента зависят от полей. После импорта решения SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] не уведомляет вас о каких-либо проблемах со ссылками, если вы удаляете из решения элемент без его зависимых элементов, пока вы не попытаетесь развернуть решение. Например, если импортированное решение содержит экземпляр списка, который зависит от типа контента, и вы удалите этот тип контента, то при развертывании может возникнуть ошибка. Эта ошибка возникает, если зависимый элемент отсутствует на сервере SharePoint. Аналогично, если удаленный элемент также содержит контейнер связанного свойства, удалите эти записи свойств контейнера из **PropertyBags** *Elements.xml* файл. Поэтому, если при удалении каких-либо элементов из импортированного решения и появляются ошибки развертывания, необходимо узнать, есть ли какие-либо зависимые элементы, которые также должны быть удалены.

## <a name="restore-missing-feature-attributes"></a>Восстановление отсутствующих атрибутов компонента
 При импорте решения некоторые необязательные атрибуты компонента не включаются в манифест импортированного компонента. Если вы хотите восстановить эти атрибуты в новом файле компонента, найдите отсутствующие атрибуты, сравнив исходный файл компонента с новым манифестом компонента и следуйте инструкциям в разделе [как: Настройка компонента SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md).

## <a name="deployment-conflict-detection-is-not-performed-on-built-in-list-instances"></a>Обнаружение конфликтов развертывания во встроенных экземплярах списка не выполняется
 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] не выполняет обнаружение конфликтов развертывания во встроенных экземплярах списка (т. е. в экземплярах списка по умолчанию, поставляемых с SharePoint). Обнаружение конфликтов не выполняется для того, чтобы избежать перезаписи встроенных экземпляров списка в SharePoint. Встроенные экземпляры списка развертываются и обновляются, но никогда не удаляются и не перезаписываются. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Устранение неполадок развертывания и упаковки SharePoint](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).

## <a name="import-sharepoint-server-2010-workflows"></a>Импорт рабочих процессов SharePoint Server 2010
 Если вы импортируете рабочий процесс, созданный в [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)], после его развертывания он будет работать неправильно. Рабочий процесс работает неправильно потому, что некоторые сборки отсутствуют, и рабочие процессы  [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] содержат формы InfoPath, которые в настоящее время не поддерживаются в решениях рабочих процессов [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Однако импортированные рабочие процессы [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] могут начать правильно работать после исправления некоторых моментов, например после добавления ссылок на сборки [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] повторного подключения форм InfoPath. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Импорт рабочих процессов SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkId=182226).

## <a name="item-name-character-limit"></a>Количество знаков в имени элемента
 В[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] существует ограничение в 260 символов для имен проекта и элементов проекта, включая путь. Если при импорте решения имя элемента превышает это ограничение, возникает ошибка:

 **Указанный путь и имя файла имеют слишком большую длину. Полное имя файла должно содержать меньше 260 символов, а имя каталога — меньше 248 символов**

 При возникновении этой ошибки элемент не создается. Наиболее часто эта проблема возникает с импортированными модулями. Чтобы избежать этой проблемы, выполните следующие действия.

- Используйте короткое имя проекта при вводе его в диалоговом окне **добавления нового проекта** .

- Создавайте проект в месте как можно ближе к корневой папке, чтобы сократить путь.

## <a name="the-sharepointproductversion-attribute"></a>Атрибут SharePointProductVersion
 При импорте решения, созданного в более ранней версии SharePoint, такой как [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] или [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)], измените значение атрибута SharePointProductVersion в манифесте пакета на 12.0 или вставьте элемент управления диспетчера скриптов во все импортированные веб-страницы и оставьте для SharePointProductVersion значение 14.0. В противном случае импортированные веб-формы не будут отображаться в SharePoint.

### <a name="background"></a>Фон
 Решения в [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] и [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] включают атрибут с именем SharePointProductVersion. SharePoint использует этот атрибут в манифестах пакетов для определения версии SharePoint, для которой предназначено решение. Допустимые значения — 12.0 и 14.0. Значение 12.0 указывает, что элемент разработан для [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] или [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)]; значение 14.0 указывает, что элемент разработан для [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] или [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)].

 Для обеспечения дополнительной защиты при отрисовке страниц ASPX [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] и [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] все страницы ASPX или главные страницы должны содержать элемент управления диспетчера скриптов. Дополнительные сведения о диспетчере скриптов см. в разделе [Обзор элемента управления ScriptManager](http://go.microsoft.com/fwlink/?LinkID=169399). Поскольку элемент управления диспетчера скриптов был недоступен в [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] и [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)], его необходимо добавлять к любой странице [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] или [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] , которая обновляется до [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] или [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]. В страницы ASPX, использующие стандартную эталонную страницу, добавлять диспетчер скриптов не требуется, поскольку он уже добавлен в стандартную эталонную страницу. Однако в страницы ASPX, не использующие эталонную страницу или использующие пользовательскую эталонную страницу, необходимо добавить элемент управления диспетчера скриптов, чтобы они могли работать в [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] или [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)].

 Отсутствие элемента управления диспетчера скриптов может вызвать проблемы при импорте проекта [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] или [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] в [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)], поскольку атрибуту SharePointProductVersion всех новых проектов присваивается значение 14.0. При развертывании обновленного проекта с веб-формой без диспетчера скриптов эта форма не будет отображаться в SharePoint.

## <a name="see-also"></a>См. также
- [Пошаговое руководство: Импорт элементов из существующего сайта SharePoint](../sharepoint/walkthrough-import-items-from-an-existing-sharepoint-site.md)
- [Руководства по импорту многократно используемых рабочих процессов](../sharepoint/guidelines-for-importing-reusable-workflows.md)
- [Пошаговое руководство: Импорт рабочего процесса для повторного использования SharePoint Designer в Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)
- [Практическое руководство. Добавление существующего файла модели BDC в проект SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
