---
title: Форма поддержки в рабочих процессах | Документы Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7214a472eff3b9181362932828f3ffee2f4fbe48
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767401"
---
# <a name="form-support-in-workflows"></a>Поддержка форм в рабочих процессах
  В рабочих процессах можно использовать четыре типа форм: ассоциации, инициации, задач и изменения. Данные типы форм могут основываться на форме ASPX или формы InfoPath. Уровень поддержки, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] предоставляет для определенной форме, зависит от нескольких факторов, которые описаны в следующих таблицах. Дополнительные сведения о типах форм рабочего процесса см. в разделе [Общие сведения о формах рабочего процесса](http://go.microsoft.com/fwlink/?LinkId=185228) на сайте MSDN.  
  
## <a name="xml-refactoring"></a>Рефакторинг XML
 При добавлении форму ассоциации или запуска ASPX для [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] элемент проекта рабочего процесса, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] автоматически выполняет рефакторинг XML в файле Elements.xml рабочего процесса для сохранения атрибута, который ссылается на форму ассоциации или запуска синхронизации Каждый раз, когда обновляется путь имя или развертывания формы или удалении формы. Однако при использовании других типов форм в рабочем процессе, такие как форма задач или изменений не Рефакторинг файла Elements.xml.  
  
## <a name="form-support-in-new-visual-studio-workflows"></a>Поддержка форм в новых рабочих процессов Visual Studio
 В следующей таблице перечислены [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] поддержка различных типов форм ASPX или InfoPath форм в рабочие процессы, созданные в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
|Тип формы|Рабочий процесс, созданный в Visual Studio с форму ASPX|Рабочий процесс, созданный в Visual Studio с помощью формы InfoPath|  
|---------------|---------------------------------------------------------|-----------------------------------------------------------------|  
|Ассоциация|-Форму ассоциации ASPX можно добавить в рабочий процесс с помощью **форма сопоставления рабочего процесса** шаблона элемента.<br />— Рефакторинг в файл Elements.xml рабочего процесса происходит при добавлении, переименован или удален формы или при изменении пути развертывания.<br />— Дополнительные сведения см. в разделе [Пошаговое руководство: Создание рабочего процесса с формами связывания и запуска](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|-Отсутствует шаблон формы ассоциации InfoPath в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-Не существует интеграции между [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] и конструктор InfoPath.<br />-Не Рефакторинг файла Elements.xml рабочего процесса.|  
|Запуск|-Форму запуска ASPX можно добавить в рабочий процесс с помощью **форма запуска рабочего процесса** шаблона элемента.<br />— Рефакторинг в файл Elements.xml рабочего процесса происходит при добавлении, переименован или удален формы или при изменении пути развертывания.<br />— Дополнительные сведения см. в разделе [Пошаговое руководство: Создание рабочего процесса с формами связывания и запуска](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|-Отсутствует шаблон формы ассоциации InfoPath в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-Не существует интеграции между [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] и конструктор InfoPath.<br />-Не Рефакторинг файла Elements.xml рабочего процесса.|  
|Задача|-Отсутствует шаблон формы задач ASPX доступна в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Необходимо создать страницу приложения и добавьте в код.<br />-Не Рефакторинг файла Elements.xml рабочего процесса.<br />— Дополнительные сведения см. в разделе [формы задач рабочего процесса (SharePoint Foundation)](http://go.microsoft.com/fwlink/?LinkId=187674)|-Отсутствует шаблон формы InfoPath задачи в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-Не существует интеграции между [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] и конструктор InfoPath.<br />-Не Рефакторинг файла Elements.xml рабочего процесса.|  
|Изменение|-Отсутствует шаблон формы изменений ASPX доступна в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Чтобы добавить форму изменений, необходимо создать страницу приложения и добавьте в код.<br />-Не Рефакторинг файла Elements.xml рабочего процесса. Необходимо вручную изменить его соответствующим образом.<br />— Дополнительные сведения см. в разделе [формы изменения рабочего процесса (SharePoint Foundation)](http://go.microsoft.com/fwlink/?LinkId=187675)|-Отсутствует шаблон формы InfoPath изменения в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-Не существует интеграции между [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] и конструктор InfoPath.<br />-Не Рефакторинг файла Elements.xml рабочего процесса.|  
  
## <a name="form-support-in-imported-sharepoint-reusable-workflows"></a>Поддержка форм в импортированных рабочих процессов SharePoint для повторного использования
 В следующей таблице перечислены [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] поддержка различных типов форм формы ASPX или InfoPath в многократно используемых рабочих процессов SharePoint, которые импортируются в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
|Тип формы|Повторно используемый рабочий процесс, который был импортирован из SharePoint Designer форму ASPX|Повторно используемый рабочий процесс, который был импортирован из SharePoint Designer формы InfoPath|  
|---------------|-------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|  
|Ассоциация|-Форма указывается в файле Elements.xml рабочего процесса.<br />-Рефакторинг файле Elements.xml рабочего процесса происходит, когда форма переименован или удален, или при изменении пути развертывания.|-Форме импортированы, но нет ссылок в файл Elements.xml рабочего процесса.<br />-Не Рефакторинг файла Elements.xml рабочего процесса.|  
|Запуск|-Форма указывается рабочим процессом в файле Elements.xml рабочего процесса.<br />-Рефакторинг файле Elements.xml рабочего процесса происходит, когда форма переименован или удален, или при изменении пути развертывания.|-Форме импортированы, но нет ссылок в файл Elements.xml рабочего процесса.<br />-Не Рефакторинг файла Elements.xml рабочего процесса. **Примечание:** правила и свойства должны добавляться и изменен в этом сценарии для работы.|  
|Задача|-Форма указывается в файле Elements.xml рабочего процесса.<br />-Не Рефакторинг файла Elements.xml рабочего процесса.|-Форме импортированы, но нет ссылок в файл Elements.xml рабочего процесса.<br />-Не Рефакторинг файла Elements.xml рабочего процесса. **Примечание:** правила и свойства должны добавляться и изменен в этом сценарии для работы.|  
|Изменение|Неприменимо. Изменение формы ASPX невозможно создать в SharePoint Designer.|Неприменимо. Изменение формы InfoPath невозможно создать в SharePoint Designer, за исключением встроенных рабочего процесса SharePoint Server, который не входит в WSP-файл при экспорте рабочего процесса.|  
  
## <a name="see-also"></a>См. также
 [Пошаговое руководство: Создание рабочего процесса с формами связывания и запуска](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)   
 [Создание решений рабочих процессов SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [Импорт элементов из существующего сайта SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)  
  
  
