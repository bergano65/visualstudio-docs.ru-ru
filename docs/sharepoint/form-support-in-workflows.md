---
title: Поддержка форм в рабочих процессах | Документация Майкрософт
description: 'Ознакомьтесь со сведениями о поддержке форм в рабочих процессах SharePoint. В рабочем процессе можно использовать четыре типа форм: Ассоциация, Инициация, задача и изменение.'
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 52939fe00dcbca1cfd633c81d4b0a00ea6b517b9
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915509"
---
# <a name="form-support-in-workflows"></a>Поддержка форм в рабочих процессах
  В рабочем процессе можно использовать четыре типа форм: Ассоциация, Инициация, задача и изменение. Эти типы форм могут быть основаны на форме ASPX или InfoPath. Уровень поддержки, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] предоставляемой для конкретной формы, зависит от нескольких факторов, которые описаны в следующих таблицах. Дополнительные сведения о типах форм рабочих процессов см. в разделе [Общие сведения о формах рабочих процессов](/previous-versions/office/developer/sharepoint-2010/ms457061(v=office.14)).

## <a name="xml-refactoring"></a>Рефакторинг XML
 При добавлении ассоциации ASPX или формы инициации в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] элемент проекта рабочего процесса автоматически перемещает [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] XML в файл *Elements.xml* рабочего процесса, чтобы обеспечить синхронизацию атрибута, ссылающегося на форму связи или запуска, при обновлении имени формы или пути развертывания или при удалении формы. Однако при использовании других типов форм в рабочем процессе, таких как задача или форма изменения, файл *Elements.xml* не подвергается оптимизации.

## <a name="form-support-in-new-visual-studio-workflows"></a>Поддержка форм в новых рабочих процессах Visual Studio
 В следующей таблице приводится [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Поддержка различных типов форм в ASPX или формах InfoPath в рабочих процессах, созданных в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

|Тип формы|Рабочий процесс, созданный в Visual Studio с помощью формы ASPX|Рабочий процесс, созданный в Visual Studio с помощью формы InfoPath|
|---------------|---------------------------------------------------------|-----------------------------------------------------------------|
|Взаимосвязь|— Форму ассоциации ASPX можно добавить в рабочий процесс с помощью шаблона элемента **формы ассоциации рабочего процесса** .<br />— Файл *Elements.xml* рабочего процесса подвергается рефакторингу при добавлении, переименовании или удалении формы, а также при изменении пути развертывания.<br />Дополнительные сведения см. в разделе [Пошаговое руководство. Создание рабочего процесса с помощью форм связывания и инициации](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|— Шаблон формы взаимосвязей InfoPath отсутствует в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .<br />— Интеграция между [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] и InfoPath Designer отсутствует.<br />— Файл *Elements.xml* рабочего процесса не подвергается рефакторингу.|
|Запуск|— Форму инициации ASPX можно добавить в рабочий процесс с помощью шаблона элемента **формы запуска рабочего процесса** .<br />— Файл *Elements.xml* рабочего процесса подвергается рефакторингу при добавлении, переименовании или удалении формы, а также при изменении пути развертывания.<br />Дополнительные сведения см. в разделе [Пошаговое руководство. Создание рабочего процесса с помощью форм связывания и инициации](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|— Шаблон формы взаимосвязей InfoPath отсутствует в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .<br />— Интеграция между [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] и InfoPath Designer отсутствует.<br />— Файл *Elements.xml* рабочего процесса не подвергается рефакторингу.|
|Задача|— Шаблон формы задачи ASPX недоступен в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Необходимо создать страницу приложения и добавить в нее код.<br />— Файл *Elements.xml* рабочего процесса не подвергается рефакторингу.<br />Дополнительные сведения см. в разделе [формы задач рабочего процесса (SharePoint Foundation)](/previous-versions/office/developer/sharepoint-2010/ms438856(v=office.14)) .|— Шаблон формы задачи InfoPath отсутствует в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .<br />— Интеграция между [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] и InfoPath Designer отсутствует.<br />— Файл *Elements.xml* рабочего процесса не подвергается рефакторингу.|
|Изменение|— Шаблон формы изменений ASPX не доступен в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Чтобы добавить форму изменения, необходимо создать страницу приложения и добавить в нее код.<br />— Файл *Elements.xml* рабочего процесса не подвергается рефакторингу. Необходимо вручную изменить его, как нужно.<br />Дополнительные сведения см. в разделе [формы изменения рабочих процессов (SharePoint Foundation)](/previous-versions/office/developer/sharepoint-2010/ms480794(v=office.14)) .|— Шаблон формы изменения InfoPath отсутствует в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .<br />— Интеграция между [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] и InfoPath Designer отсутствует.<br />— Файл *Elements.xml* рабочего процесса не подвергается рефакторингу.|

## <a name="form-support-in-imported-sharepoint-reusable-workflows"></a>Поддержка форм в импортированных рабочих процессах с возможностью повторного использования SharePoint
 В следующей таблице перечислены [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] различные типы форм для форм ASPX или InfoPath в рабочих процессах с возможностью повторного использования в SharePoint, которые импортируются в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

|Тип формы|Рабочий процесс для повторного использования с формой ASPX, импортированной из SharePoint Designer|Рабочий процесс для повторного использования с формой InfoPath, импортированной из SharePoint Designer|
|---------------|-------------------------------------------------------------------------------| - |
|Взаимосвязь|— Ссылка на форму содержится в файле *Elements.xml* рабочего процесса.<br />— Файл *Elements.xml* рабочего процесса подвергается рефакторингу при переименовании или удалении формы, а также при изменении пути развертывания.|— Форма импортируется, но не упоминается в *Elements.xml* рабочего процесса.<br />— Файл *Elements.xml* рабочего процесса не подвергается рефакторингу.|
|Запуск|— На форму ссылается рабочий процесс в файле *Elements.xml* рабочего процесса.<br />— Файл *Elements.xml* рабочего процесса подвергается рефакторингу при переименовании или удалении формы, а также при изменении пути развертывания.|— Форма импортируется, но не упоминается в *Elements.xml* рабочего процесса.<br />— Файл *Elements.xml* рабочего процесса не подвергается рефакторингу. **Примечание.**  Для работы этого сценария необходимо добавить и изменить правила и свойства.|
|Задача|— Ссылка на форму содержится в файле *Elements.xml* рабочего процесса.<br />— Файл *Elements.xml* рабочего процесса не подвергается рефакторингу.|— Форма импортируется, но не упоминается в *Elements.xml* рабочего процесса.<br />— Файл *Elements.xml* рабочего процесса не подвергается рефакторингу. **Примечание.**  Для работы этого сценария необходимо добавить и изменить правила и свойства.|
|Изменение|Неприменимо. Формы изменения ASPX не могут быть созданы в SharePoint Designer.|Неприменимо. Формы изменения InfoPath не могут быть созданы в SharePoint Designer, за исключением встроенного рабочего процесса SharePoint Server, который не включается в WSP-файл при экспорте рабочего процесса.|

## <a name="see-also"></a>См. также раздел
- [Пошаговое руководство: Создание рабочего процесса с формами связывания и запуска](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)
- [Создание решений рабочих процессов SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)
- [Импорт элементов с существующего сайта SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
