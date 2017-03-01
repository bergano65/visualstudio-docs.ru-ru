---
title: "Общие сведения о модели автоматизации | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: ce59c002accd55b9179cacc60cf944ff72138c7e
ms.lasthandoff: 02/22/2017

---
# <a name="automation-model-overview"></a>Общие сведения о модели автоматизации
Модель автоматизации состоит из набора объектов, для которых можно написать надстройки Visual Studio или расширение. Надстройка — это приложение, можно управлять средой Visual Studio и автоматизировать часто выполняемые задачи. Расширения Visual Studio можно создавать пользовательские компоненты Visual Studio или расширить функциональные возможности стандартных компонентов, таких как текстовый редактор.  
  
## <a name="objects-in-the-automation-model"></a>Объекты в модели автоматизации  
 Модель автоматизации состоит из связанных групп объектов, контролирующих главные аспекты среде. Вот диаграмма, отображающая обширный набор объектов, которые составляют модель автоматизации.  
  
 ![Диаграмма объектов автоматизации Visual Studio](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")  
Объекты автоматизации Visual Studio  
  
 Дополнительные сведения см. в разделе [расширение среды Visual Studio](http://msdn.microsoft.com/Library/4173a963-7ac7-4966-9bb7-e28a9d9f6792).  
  
 Среда предоставляет модель для различных функциональных областей. Например существует модель кода для различных элементов, которые могут оказаться в коде. Существует модель документов для различных элементов документа. Одна область, область проекта, представляет Особенный интерес к поставщикам VSPackage. Вероятно, стоит новых типов проекта включаются в модель автоматизации так же, как [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] и [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] включаются в модель автоматизации. Что процесс описан в [предоставляет сведения об автоматизации VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md).  
  
 Места, где можно рассматривать расширение модели автоматизации среды:  
  
-   Проект  
  
-   Document  
  
-   Код  
  
-   Построить  
  
 Дополнительные сведения об автоматизации см. в разделе [Автоматизация и расширение среды для Visual Studio](http://msdn.microsoft.com/Library/f71a2253-3e68-4e5e-9a18-edbba816caf6). В этом документе и документы также предоставляет ссылки на, помогут принять решение в отношении как следует предоставить автоматизацию VSPackage.  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство: создание надстройки](http://msdn.microsoft.com/Library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)
