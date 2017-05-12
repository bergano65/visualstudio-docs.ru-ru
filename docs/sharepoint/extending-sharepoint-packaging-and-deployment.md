---
title: "Extending SharePoint Packaging and Deployment"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint development in Visual Studio, extending deployment"
ms.assetid: 4789ebb2-12bc-42b9-9427-e63d77137765
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# Extending SharePoint Packaging and Deployment
  Вы можете расширить процесс упаковки и развертывания для проектов SharePoint.  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
##  <a name="creating_deployment_steps"></a> Создание шагов развертывания  
 При развертывании проекта SharePoint [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] выполняет ряд шагов развертывания.  Visual Studio включает встроенные шаги развертывания для многих задач, например для отзыва или добавления решений.  Однако вы также можете создать собственные шаги развертывания.  
  
 Пошаговое руководство по созданию шага развертывания см. в разделе [Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
##  <a name="creating_deployment_configurations"></a> Создание конфигураций развертывания  
 Конфигурация развертывания представляет собой набор шагов развертывания, который выполняется для данного проекта, но может повлиять на все элементы проекта SharePoint.  Каждая конфигурация развертывания содержит один набор шагов, который выполняется при развертывании проекта, и другой набор, который выполняется при отзыве проекта.  [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] включает две встроенные конфигурации развертывания, однако вы также можете создать свои собственные.  При создании конфигурации развертывания можно включить встроенные шаги развертывания, а также специально созданные шаги.  
  
 Пошаговое руководство по созданию конфигурации развертывания см. в разделе [Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
##  <a name="run_code_before_and_after_each_deployment_step"></a> Выполнение кода во время развертывания или отзыва решения SharePoint  
 Для выполнения дополнительных задач при развертывании или отзыве решения SharePoint можно настроить обработку событий.  Visual Studio создает события, которые можно обрабатывать, в следующих сценариях.  
  
-   До и после выполнения каждого шага развертывания для элемента проекта SharePoint.  Дополнительные сведения см. в разделе [How to: Run Code When Deployment Steps are Executed](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md).  
  
-   До и после развертывания или отзыва проекта SharePoint.  Дополнительные сведения см. в разделе [How to: Run Code When a SharePoint Project is Deployed or Retracted](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md).  
  
##  <a name="deployment_conflicts"></a> Обработка конфликтов развертывания  
 Некоторые типы элементов проекта SharePoint, включая модули, веб\-части, экземпляры списков и типы содержимого, предоставляют встроенную функцию разрешения конфликтов развертывания.  При развертывании решения, содержащего один из таких элементов проекта, Visual Studio сначала проверяет, существует ли на сайте SharePoint файл с тем же именем, URL\-адресом или идентификатором, что и файл в развертываемом элементе.  В случае обнаружения конфликта Visual Studio может автоматически разрешить его или запросить у пользователя, следует ли Visual Studio разрешить конфликт или отменить развертывание.  Дополнительные сведения см. в разделе [Устранение неполадок, связанных с упаковкой и развертыванием решений SharePoint](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).  
  
 Эту функцию можно расширить, добавив собственный код, который проверяет наличие конфликтов развертывания и разрешает их.  Дополнительные сведения см. в разделе [How to: Handle Deployment Conflicts](../sharepoint/how-to-handle-deployment-conflicts.md).  
  
##  <a name="run_command_line_operations_before_or_after_a_project_is_deployed"></a> Выполнение операций командной строки до или после развертывания проекта  
 Чтобы выполнить операцию командной строки при развертывании решения SharePoint, можно задать свойства <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PreDeploymentCommand%2A> и <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PostDeploymentCommand%2A> объекта <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>.  Visual Studio выполнит эти команды до и после развертывания проекта.  
  
 В некоторых случаях могут возникать конфликты развертывания.  Существует несколько способов разрешения конфликтов.  Дополнительные сведения см. в разделе [Устранение неполадок, связанных с упаковкой и развертыванием решений SharePoint](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).  
  
##  <a name="customizing_validation_rules"></a> Настройка правил проверки  
 Перед развертыванием пакета решения \(WSP\-файла\) можно создать настраиваемые правила проверки компонентов и пакетов для проверки допустимости компонента или пакета.  Например, можно передать разработчикам сведения, предупреждения или ошибки, которые помогут им устранить проблемы проверки.  Дополнительные сведения см. в разделе [How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).  
  
## См. также  
 [How to: Run Code When Deployment Steps are Executed](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)   
 [Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)   
 [How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)   
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  