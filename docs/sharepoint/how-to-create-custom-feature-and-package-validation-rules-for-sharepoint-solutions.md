---
title: "How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions | Microsoft Docs"
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
  - "SharePoint development in Visual Studio, validation rules"
ms.assetid: 17e818f8-0f3a-4a96-a6fc-1634ddb4825d
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions
  Для проверки пакета решения, сформированного Visual Studio, можно создавать пользовательские правила проверки.  Полную проверку всего "Компонента" или пакета можно выполнить выбрав **Проверить** в контекстном меню пакета или "Компонента" в меню **УпаковкаОбозреватель**.  Частичная проверка выполняется при добавлении новых элементов проекта SharePonit или "Компонентов" проекта для определения действительного состояния "Пакета" или "Компонента".  
  
### Создание пользовательского правила проверки пакета  
  
1.  Создайте проект библиотеки классов.  
  
2.  Добавьте ссылки на следующие сборки:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  Создание класса, реализующего один из перечисленных интерфейсов:  
  
    -   Чтобы создать правило проверки пакета, реализуйте интерфейс <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule>.  
  
    -   Чтобы создать правило проверки компонента, реализуйте интерфейс <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule>.  
  
4.  Добавьте к классу атрибут <xref:System.ComponentModel.Composition.ExportAttribute>.  Этот атрибут позволяет Visual Studio находить и загружать пользовательское правило проверки.  Передайте конструктору атрибута тип <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> или <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule>.  
  
## Пример  
 В следующем примере кода показано как создать пользовательское правило проверки компонента.  
  
 [!code-csharp[SPExtensibility.FeatureValidation#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.featurevalidation/cs/extension/customfeaturevalidationrule.cs#1)]
 [!code-vb[SPExtensibility.FeatureValidation#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.featurevalidation/vb/extension/customvalidationrule.vb#1)]  
  
## Компиляция кода  
 Для этого примера требуются ссылки на следующие сборки:  
  
-   Microsoft.VisualStudio.SharePoint.  
  
-   System.ComponentModel.Composition.  
  
## Развертывание расширения  
 Чтобы развернуть расширение, создайте пакет расширения [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(VSIX\) для сборки и всех остальных файлов, которые предположительно будут распространяться с расширением.  Дополнительные сведения см. в разделе [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## См. также  
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
  
  