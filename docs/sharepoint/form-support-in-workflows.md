---
title: Форма поддержки в рабочие процессы | Документация Майкрософт
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
ms.openlocfilehash: 704e08524bb9aaf014dbd29e7df7361a7e1bbefe
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56604136"
---
# <a name="form-support-in-workflows"></a>Поддержка форм в рабочих процессах
  Четыре типа форм можно использовать в рабочем процессе: ассоциации, инициации, задач и изменения. Эти типы форм могут основываться на форме ASPX или форму InfoPath. Уровень поддержки, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] предоставляет для определенной форме, зависит от нескольких факторов, которые описаны в следующих таблицах. Дополнительные сведения о типах форм рабочего процесса, см. в разделе [Workflow Forms Overview](http://go.microsoft.com/fwlink/?LinkId=185228).

## <a name="xml-refactoring"></a>Рефакторинг XML
 При добавлении форму ассоциации или запуска ASPX для [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] элемент проекта рабочего процесса, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] автоматически выполняет рефакторинг XML в рабочем процессе *Elements.xml* файла для сохранения атрибута, который ссылается на связь или при удалении форму инициации синхронизации при каждом обновлении путь имя или развертывания формы или формы. Тем не менее, при использовании других типов форм в рабочем процессе, например форму задач или изменений, *Elements.xml* не Рефакторинг файла.

## <a name="form-support-in-new-visual-studio-workflows"></a>Поддержка форм в новых рабочих процессов Visual Studio
 В следующей таблице перечислены [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] поддержка различных типов форм ASPX или InfoPath forms в рабочих процессах, созданных в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

|Тип формы|Рабочий процесс, созданный в Visual Studio с форму ASPX|Рабочий процесс, созданный в Visual Studio с помощью формы InfoPath|
|---------------|---------------------------------------------------------|-----------------------------------------------------------------|
|Ассоциация|-Форму ASPX сопоставления можно добавить в рабочий процесс с помощью **форма сопоставления рабочего процесса** шаблона элемента.<br />- *Elements.xml* рефакторинг файл рабочего процесса происходит при добавлении, переименован или удален формы или при изменении пути развертывания.<br />— Дополнительные сведения см. в разделе [Пошаговое руководство: Создание рабочего процесса с формами связывания и запуска](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|-Отсутствует шаблон формы InfoPath ассоциации в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-Не существует интеграции между [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] и конструктора InfoPath.<br />- *Elements.xml* не Рефакторинг файла рабочего процесса.|
|Запуска|-Форму запуска ASPX можно добавить в рабочий процесс с помощью **форма запуска рабочего процесса** шаблона элемента.<br />- *Elements.xml* рефакторинг файл рабочего процесса происходит при добавлении, переименован или удален формы или при изменении пути развертывания.<br />— Дополнительные сведения см. в разделе [Пошаговое руководство: Создание рабочего процесса с формами связывания и запуска](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|-Отсутствует шаблон формы InfoPath ассоциации в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-Не существует интеграции между [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] и конструктора InfoPath.<br />- *Elements.xml* не Рефакторинг файла рабочего процесса.|
|Задача|-Отсутствует шаблон формы ASPX задач доступна в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Необходимо создать страницу приложения и добавьте в него код.<br />- *Elements.xml* не Рефакторинг файла рабочего процесса.<br />— Дополнительные сведения см. в разделе [Workflow Task Forms (SharePoint Foundation)](http://go.microsoft.com/fwlink/?LinkId=187674)|-Отсутствует шаблон формы InfoPath задачи в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-Не существует интеграции между [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] и конструктора InfoPath.<br />- *Elements.xml* не Рефакторинг файла рабочего процесса.|
|Изменение|-Отсутствует шаблон формы ASPX изменений доступен в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Чтобы добавить форму изменений, необходимо создать страницу приложения и добавьте в него код.<br />- *Elements.xml* не Рефакторинг файла рабочего процесса. Необходимо вручную изменить соответствующим образом.<br />— Дополнительные сведения см. в разделе [Workflow Modification Forms (SharePoint Foundation)](http://go.microsoft.com/fwlink/?LinkId=187675)|-Отсутствует шаблон формы InfoPath изменения в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-Не существует интеграции между [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] и конструктора InfoPath.<br />- *Elements.xml* не Рефакторинг файла рабочего процесса.|

## <a name="form-support-in-imported-sharepoint-reusable-workflows"></a>Поддержка форм в импортированных рабочих процессах SharePoint для повторного использования
 В следующей таблице перечислены [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] поддержка различных типов форм ASPX или InfoPath forms в рабочих процессах SharePoint для повторного использования, которые импортируются в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

|Тип формы|Повторно используемый рабочий процесс, имеющий форму ASPX, импортированных из SharePoint Designer|Повторно используемый рабочий процесс, имеющий форму InfoPath, импортированных из SharePoint Designer|
|---------------|-------------------------------------------------------------------------------| - |
|Ассоциация|-Форма указывается в *Elements.xml* файл рабочего процесса.<br />- *Elements.xml* рефакторинг файл рабочего процесса происходит при виде переименован или удален, или при изменении пути развертывания.|-Импортируется форме, но нет ссылок в *Elements.xml* рабочего процесса.<br />- *Elements.xml* не Рефакторинг файла рабочего процесса.|
|Запуска|-Форме ссылается рабочий процесс в *Elements.xml* файл рабочего процесса.<br />- *Elements.xml* рефакторинг файл рабочего процесса происходит при виде переименован или удален, или при изменении пути развертывания.|-Импортируется форме, но нет ссылок в *Elements.xml* рабочего процесса.<br />- *Elements.xml* не Рефакторинг файла рабочего процесса. **Примечание.**  Правила и свойства необходимо добавить и изменить для работы данного сценария.|
|Задача|-Форма указывается в *Elements.xml* файл рабочего процесса.<br />- *Elements.xml* не Рефакторинг файла рабочего процесса.|-Импортируется форме, но нет ссылок в *Elements.xml* рабочего процесса.<br />- *Elements.xml* не Рефакторинг файла рабочего процесса. **Примечание.**  Правила и свойства необходимо добавить и изменить для работы данного сценария.|
|Изменение|Неприменимо. Формы изменения ASPX в SharePoint Designer, невозможно.|Неприменимо. Формы InfoPath изменений не может создаваться в SharePoint Designer, за исключением встроенных рабочий процесс SharePoint Server, который не включается в WSP-файла при экспорте рабочего процесса.|

## <a name="see-also"></a>См. также
- [Пошаговое руководство: Создание рабочего процесса с формами связывания и запуска](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)
- [Создание решений рабочих процессов SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)
- [Импорт элементов из существующего сайта SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
