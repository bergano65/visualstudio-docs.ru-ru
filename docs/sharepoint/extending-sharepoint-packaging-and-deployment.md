---
title: "Расширение SharePoint упаковки и развертывания | Документы Microsoft"
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
helpviewer_keywords: SharePoint development in Visual Studio, extending deployment
ms.assetid: 4789ebb2-12bc-42b9-9427-e63d77137765
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b88c89d9464b5ac9bc588c4364de97c1f4e281d9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="extending-sharepoint-packaging-and-deployment"></a>Расширение упаковки и развертывания проектов SharePoint
  Вы можете расширить процесс упаковки и развертывания для проектов SharePoint.
  
##  <a name="creating-deployment-steps"></a>Создание шагов развертывания  
 При развертывании проекта SharePoint [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] выполняет ряд шагов развертывания. Visual Studio включает встроенные шаги развертывания для многих задач, например для отзыва или добавления решений. Однако вы также можете создать собственные шаги развертывания.  
  
 Пошаговое руководство, руководство по созданию шага развертывания см. в разделе [Пошаговое руководство: Создание пользовательского шага развертывания для проектов SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
##  <a name="creating-deployment-configurations"></a>Создание конфигураций развертывания  
 Конфигурация развертывания представляет собой набор шагов развертывания, который выполняется для данного проекта, но может повлиять на все элементы проекта SharePoint. Каждая конфигурация развертывания содержит один набор шагов, который выполняется при развертывании проекта, и другой набор, который выполняется при отзыве проекта. [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)]включает две встроенные конфигурации развертывания, но можно также создать свои собственные. При создании конфигурации развертывания можно включить встроенные шаги развертывания, а также специально созданные шаги.  
  
 Пошаговое руководство по созданию конфигурации развертывания см. в разделе [Пошаговое руководство: Создание пользовательского шага развертывания для проектов SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
##  <a name="run-code-when-a-sharepoint-solution-is-deployed-or-retracted"></a>Выполнение кода во время развертывания или отзыва решения SharePoint  
 Для выполнения дополнительных задач при развертывании или отзыве решения SharePoint можно настроить обработку событий. Visual Studio создает события, которые можно обрабатывать, в следующих сценариях.  
  
-   До и после выполнения каждого шага развертывания для элемента проекта SharePoint. Дополнительные сведения см. в разделе [как: запуска кода при руководство](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md).  
  
-   До и после развертывания или отзыва проекта SharePoint. Дополнительные сведения см. в разделе [как: запуска кода при проекта SharePoint является развертывания или отзыва](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md).  
  
##  <a name="handling-deployment-conflicts"></a>Обработка конфликтов развертывания  
 Некоторые типы элементов проекта SharePoint, включая модули, веб-части, экземпляры списков и типы содержимого, предоставляют встроенную функцию разрешения конфликтов развертывания. При развертывании решения, содержащего один из таких элементов проекта, Visual Studio сначала проверяет, существует ли на сайте SharePoint файл с тем же именем, URL-адресом или идентификатором, что и файл в развертываемом элементе. В случае обнаружения конфликта Visual Studio может автоматически разрешить его или запросить у пользователя, следует ли Visual Studio разрешить конфликт или отменить развертывание. Дополнительные сведения см. в разделе [Устранение неполадок SharePoint упаковки и развертывания](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).  
  
 Эту возможность можно расширить, добавив собственный код, который проверяет наличие конфликтов развертывания и разрешает их. Дополнительные сведения см. в разделе [как: обработка конфликтов развертывания](../sharepoint/how-to-handle-deployment-conflicts.md).  
  
##  <a name="run-command-line-operations-before-or-after-a-project-is-deployed"></a>Выполнение операций командной строки до или после развертывания проекта  
 Чтобы выполнить операцию командной строки при развертывании решения SharePoint, можно задать свойства <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PreDeploymentCommand%2A> и <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PostDeploymentCommand%2A> объекта <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>. Visual Studio выполнит эти команды до и после развертывания проекта.  
  
 В некоторых случаях могут возникать конфликты развертывания. Существует несколько способов разрешения конфликтов. Дополнительные сведения см. в разделе [Устранение неполадок SharePoint упаковки и развертывания](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).  
  
##  <a name="customizing-validation-rules"></a>Настройка правил проверки  
 Перед развертыванием пакета решения (WSP-файла) можно создать настраиваемые правила проверки компонентов и пакетов для проверки допустимости компонента или пакета. Например, можно передать разработчикам сведения, предупреждения или ошибки, которые помогут им устранить проблемы проверки. Дополнительные сведения см. в разделе [как: Создание пользовательских компонентов и правила проверки пакетов для решений SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).  
  
## <a name="see-also"></a>См. также  
 [Как: выполнения кода при выполнении шагов развертывания](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)   
 [Пошаговое руководство: Создание пользовательского шага развертывания для проектов SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)   
 [Как: Создание пользовательской функции правил проверки и пакетов для решений SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)   
 [Расширение системы проектов SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  
