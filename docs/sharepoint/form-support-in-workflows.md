---
title: Поддержка форм в рабочих процессах | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b064df6729b914af7758cde86b03b886fd0e5d26
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/28/2019
ms.locfileid: "72986266"
---
# <a name="form-support-in-workflows"></a>Поддержка форм в рабочих процессах
  В рабочем процессе можно использовать четыре типа форм: Ассоциация, Инициация, задача и изменение. Эти типы форм могут быть основаны на форме ASPX или InfoPath. Уровень поддержки, предоставляемый [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] для конкретной формы, зависит от нескольких факторов, которые описаны в следующих таблицах. Дополнительные сведения о типах форм рабочих процессов см. в разделе [Общие сведения о формах рабочих процессов](/previous-versions/office/developer/sharepoint-2010/ms457061(v=office.14)).

## <a name="xml-refactoring"></a>Рефакторинг XML
 При добавлении ассоциации ASPX или формы инициации в элемент проекта [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] рабочего процесса [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] автоматически выполняет XML-код в файле *Elements. XML* рабочего процесса, чтобы обеспечить синхронизацию атрибута, ссылающегося на форму связи или запуска. При обновлении имени формы или пути развертывания или при удалении формы. Однако при использовании других типов форм в рабочем процессе, таких как задача или форма изменения, файл *Elements. XML* не подвергается рефакторингу.

## <a name="form-support-in-new-visual-studio-workflows"></a>Поддержка форм в новых рабочих процессах Visual Studio
 В следующей таблице перечислены [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] поддержку различных типов форм в ASPX или формах InfoPath в рабочих процессах, создаваемых в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

|Тип формы|Рабочий процесс, созданный в Visual Studio с помощью формы ASPX|Рабочий процесс, созданный в Visual Studio с помощью формы InfoPath|
|---------------|---------------------------------------------------------|-----------------------------------------------------------------|
|Ассоциация|— Форму ассоциации ASPX можно добавить в рабочий процесс с помощью шаблона элемента **формы ассоциации рабочего процесса** .<br />— Файл *Elements. XML* рабочего процесса подвергается рефакторингу при добавлении, переименовании или удалении формы, а также при изменении пути развертывания.<br />Дополнительные сведения см. в разделе [Пошаговое руководство. Создание рабочего процесса с помощью форм связывания и инициации](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|— Шаблон формы ассоциации InfoPath отсутствует в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />— Интеграция между [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] и InfoPath Designer отсутствует.<br />— Файл *Elements. XML* рабочего процесса не подвергается рефакторингу.|
|Приглашения|— Форму инициации ASPX можно добавить в рабочий процесс с помощью шаблона элемента **формы запуска рабочего процесса** .<br />— Файл *Elements. XML* рабочего процесса подвергается рефакторингу при добавлении, переименовании или удалении формы, а также при изменении пути развертывания.<br />Дополнительные сведения см. в разделе [Пошаговое руководство. Создание рабочего процесса с помощью форм связывания и инициации](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|— Шаблон формы ассоциации InfoPath отсутствует в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />— Интеграция между [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] и InfoPath Designer отсутствует.<br />— Файл *Elements. XML* рабочего процесса не подвергается рефакторингу.|
|Задача|— Шаблон формы задачи ASPX недоступен в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Необходимо создать страницу приложения и добавить в нее код.<br />— Файл *Elements. XML* рабочего процесса не подвергается рефакторингу.<br />Дополнительные сведения см. в разделе [формы задач рабочего процесса (SharePoint Foundation)](/previous-versions/office/developer/sharepoint-2010/ms438856(v=office.14)) .|— Шаблон формы задачи InfoPath отсутствует в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />— Интеграция между [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] и InfoPath Designer отсутствует.<br />— Файл *Elements. XML* рабочего процесса не подвергается рефакторингу.|
|Изменение|— Шаблон формы изменений ASPX недоступен в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Чтобы добавить форму изменения, необходимо создать страницу приложения и добавить в нее код.<br />— Файл *Elements. XML* рабочего процесса не подвергается рефакторингу. Необходимо вручную изменить его, как нужно.<br />Дополнительные сведения см. в разделе [формы изменения рабочих процессов (SharePoint Foundation)](/previous-versions/office/developer/sharepoint-2010/ms480794(v=office.14)) .|— Шаблон формы модификаций InfoPath отсутствует в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />— Интеграция между [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] и InfoPath Designer отсутствует.<br />— Файл *Elements. XML* рабочего процесса не подвергается рефакторингу.|

## <a name="form-support-in-imported-sharepoint-reusable-workflows"></a>Поддержка форм в импортированных рабочих процессах с возможностью повторного использования SharePoint
 В следующей таблице перечислены [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] поддержки различных типов форм в ASPX или формах InfoPath в рабочих процессах с возможностью повторного использования в SharePoint, которые импортируются в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

|Тип формы|Рабочий процесс для повторного использования с формой ASPX, импортированной из SharePoint Designer|Рабочий процесс для повторного использования с формой InfoPath, импортированной из SharePoint Designer|
|---------------|-------------------------------------------------------------------------------| - |
|Ассоциация|— На форму указывает ссылка в файле рабочего процесса *Elements. XML* .<br />— Файл *Elements. XML* рабочего процесса подвергается рефакторингу при переименовании или удалении формы, а также при изменении пути развертывания.|— Форма импортируется, но не упоминается в *файле Elements. XML* рабочего процесса.<br />— Файл *Elements. XML* рабочего процесса не подвергается рефакторингу.|
|Приглашения|— На форму ссылается рабочий процесс из файла *Elements. XML* рабочего процесса.<br />— Файл *Elements. XML* рабочего процесса подвергается рефакторингу при переименовании или удалении формы, а также при изменении пути развертывания.|— Форма импортируется, но не упоминается в *файле Elements. XML* рабочего процесса.<br />— Файл *Elements. XML* рабочего процесса не подвергается рефакторингу. **Примечание.**  Для работы этого сценария необходимо добавить и изменить правила и свойства.|
|Задача|— На форму указывает ссылка в файле рабочего процесса *Elements. XML* .<br />— Файл *Elements. XML* рабочего процесса не подвергается рефакторингу.|— Форма импортируется, но не упоминается в *файле Elements. XML* рабочего процесса.<br />— Файл *Elements. XML* рабочего процесса не подвергается рефакторингу. **Примечание.**  Для работы этого сценария необходимо добавить и изменить правила и свойства.|
|Изменение|Неприменимо. Формы изменения ASPX не могут быть созданы в SharePoint Designer.|Неприменимо. Формы изменения InfoPath не могут быть созданы в SharePoint Designer, за исключением встроенного рабочего процесса SharePoint Server, который не включается в WSP-файл при экспорте рабочего процесса.|

## <a name="see-also"></a>См. также
- [Пошаговое руководство. Создание рабочего процесса с формами ассоциаций и инициации](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)
- [Создание решений для рабочих процессов SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)
- [Импорт элементов с существующего сайта SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
