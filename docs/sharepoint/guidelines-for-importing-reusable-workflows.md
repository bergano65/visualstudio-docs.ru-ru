---
title: "Рекомендации по Импорт рабочих процессов с возможностью повторного использования | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- SharePoint development in Visual Studio, reusable workflows
- importing items [SharePoint development in Visual Studio]
- reusable workflows [SharePoint development in Visual Studio]
ms.assetid: 851043dd-ecbe-49ab-b5b7-5ea7b699df12
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 9f0ba8bdd5e599fadc98519d54a3015abf91f013
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="guidelines-for-importing-reusable-workflows"></a>Guidelines for Importing Reusable Workflows
  Для импорта рабочих процессов с возможностью повторного использования, созданных в SharePoint Designer, воспользуйтесь шаблоном "Импорт рабочего процесса SharePoint 2010 для повторного использования" в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Этот шаблон импортирует *декларативный* *рабочего процесса* ([!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]-только) и преобразует его в *рабочий процесс с кодом*, который является рабочий процесс, который можно расширить с помощью [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] или [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] кода. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][Пошаговое руководство: Импорт рабочего процесса SharePoint Designer для повторного использования в Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).  
  
 Однако шаблон "Импорт рабочего процесса SharePoint 2010 для повторного использования" может импортировать только решения фермы. Если требуется развернуть рабочий процесс как изолированное решение, воспользуйтесь шаблоном "Импорт пакета решения SharePoint 2010". Однако при этом невозможно преобразовать его в рабочий процесс с кодом и редактировать в этом качестве.  
  
## <a name="importing-reusable-workflows-by-using-the-import-reusable-workflow-template"></a>Импорт рабочих процессов для повторного использования с помощью шаблона рабочего процесса для повторного использования импорта  
 При таком импорте рабочего процесса вы можете выполнять или изменять решение аналогично любому другому решению [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 2010, но некоторые элементы придется исправить самостоятельно.  
  
### <a name="importing-task-forms"></a>Импорт форм задач  
 Шаблон проекта "Импорт рабочего процесса SharePoint 2010 для повторного использования" импортирует все формы запуска и формы связывания, но только одну форму задач, поскольку схема рабочего процесса с кодом разрешает наличие только одной формы задач. Все остальные формы задач из исходного решения рабочего процесса, помещаются в **Прочие импортированные файлы** папки в **обозревателе решений**.  
  
## <a name="importing-reusable-workflows-by-using-the-import-sharepoint-2010-solution-package-template"></a>Импорт рабочих процессов с возможностью повторного использования с помощью шаблона "Импорт пакета решения SharePoint 2010"  
 При таком импорте рабочих процессов с возможностью повторного использования с помощью шаблона "Импорт пакета решения SharePoint 2010" необходимо рассмотреть следующие проблемы.  
  
-   После импорта рабочий процесс, можно немедленно развернуть и запустите его в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , нажав клавишу F5. Тем не менее если вы вносит изменения в рабочий процесс в импортированных решений, может потребоваться вручную исправить элементов в проекте, прежде чем можно будет развернуть и запустить рабочий процесс.  
  
-   Поскольку является декларативным, к нему нельзя добавлять код. Для преобразования рабочего процесса в рабочий процесс с кодом, необходимо импортировать его в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] с помощью шаблона Импорт повторно используемого рабочего процесса SharePoint 2010.  
  
-   При редактировании файла конструктора (XOML-файл) рабочего процесса в режиме конструктора рекомендуется изменить его в представлении источника, так как в конструкторе рабочих процессов отображает ошибки, значение false.  
  
-   Отладка в рабочем процессе не работает с декларативным содержимым. Установить точки останова в [!INCLUDE[wfd2](../sharepoint/includes/wfd2-md.md)] , попадание не выполняется.  
  
## <a name="importing-globally-reusable-workflow-solutions"></a>Импорт решений глобального рабочего процесса  
 Глобальные рабочие процессы с возможностью повторного использования не могут быть импортированы с помощью шаблона "Импорт рабочего процесса SharePoint 2010 для повторного использования". Для импорта глобального рабочего процесса с возможностью повторного использования необходимо преобразовать его в неглобальный рабочий процесс с возможностью повторного использования или воспользоваться шаблоном "Импорт пакета решения SharePoint 2010".  
  
 Для преобразования рабочего процесса, необходимо сделать копию глобального рабочего процесса в SharePoint Designer (открыв контекстное меню для рабочего процесса и выбрав **сохранить копию**). Затем следует импортировать новый рабочий процесс с возможностью повторного использования с помощью шаблона "Импорт рабочего процесса SharePoint 2010 для повторного использования" в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 Для импорта глобального рабочего процесса с возможностью повторного использования в исходном виде следует использовать шаблон "Импорт пакета решения SharePoint 2010". При использовании этого метода рабочий процесс не преобразуется в рабочий процесс с кодом и остается декларативным рабочим процессом.  
  
## <a name="see-also"></a>См. также  
 [Импорт элементов из существующего сайта SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Пошаговое руководство. Импорт рабочего процесса с возможностью повторного использования из конструктора SharePoint в Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)  
  
  