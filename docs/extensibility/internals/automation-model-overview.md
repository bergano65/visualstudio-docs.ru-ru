---
title: "Общие сведения о модели автоматизации | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6d4fda81b18824560276c1398583b2674bf200ab
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="automation-model-overview"></a>Общие сведения о модели автоматизации
Модель автоматизации состоит из набора объектов, для которых можно написать надстройки Visual Studio или расширение. Надстройка — это приложение, можно управлять средой Visual Studio и автоматизации типичных задач. Расширение Visual Studio можно создавать пользовательские компоненты Visual Studio или добавить функциональные возможности стандартных компонентов, таких как текстовый редактор.  
  
## <a name="objects-in-the-automation-model"></a>Объекты в модели автоматизации  
 Модель автоматизации состоит из связанные группы объектов, которые управляют важнейшими областями среде. Ниже приведен диаграмма, показывающая широкий набор объектов, которые составляют модель автоматизации.  
  
 ![Диаграмма объектов автоматизации Visual Studio](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")  
Объекты автоматизации Visual Studio  
  
 Дополнительные сведения см. в разделе [расширение среды Visual Studio](http://msdn.microsoft.com/Library/4173a963-7ac7-4966-9bb7-e28a9d9f6792).  
  
 Среде предоставляет модель для разных функциональных областях. Например отсутствует модели кода для различных элементов, которые могут оказаться в коде. Имеется модель документа для различных элементов документа. Особый интерес для поставщиков VSPackage — одну область, область проекта. Скорее всего, вы будете вашей новых типов проектов принять участие в модели автоматизации, так же, как [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] и [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] участие в модели автоматизации. Появлялся процесс [предоставление автоматизации для пакетов VSPackage](../../extensibility/internals/providing-automation-for-vspackages.md).  
  
 Места, где можно рассмотреть расширение модели автоматизации среды:  
  
-   Проект  
  
-   Document  
  
-   Код  
  
-   Построить  
  
 Дополнительные сведения об автоматизации см. в разделе [автоматизации и расширению среды для Visual Studio](http://msdn.microsoft.com/Library/f71a2253-3e68-4e5e-9a18-edbba816caf6). В этом документе, а также в документах также предоставляет ссылки на, помогут принять решение в отношении как должна предоставлять автоматизации для VSPackage.  
  
## <a name="see-also"></a>См. также  
 [Как: создание надстройки](http://msdn.microsoft.com/Library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)