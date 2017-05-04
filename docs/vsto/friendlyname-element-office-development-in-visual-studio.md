---
title: "Элемент &lt;friendlyName&gt; (разработка решений Office в Visual Studio) | Microsoft Docs"
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
  - "манифесты приложения [разработка решений Office в Visual Studio], элемент <friendlyName>"
ms.assetid: 80250fbf-fccf-4baa-948e-ace7f4449e9c
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# Элемент &lt;friendlyName&gt; (разработка решений Office в Visual Studio)
  Элемент `friendlyName` пространства имен `vstov4`  хранит имя, которое отображается в списке установленных программ.  
  
## Синтаксис  
  
```  
<friendlyName>  
</friendlyName>  
```  
  
## Элементы и атрибуты  
 Элемент `friendlyName` находится в пространстве имен `vstov4` . Значение отображается в списке программ, установленных на компьютере, и в диалоговом окне "Надстройки COM VSTO" приложений Microsoft Office.  
  
 У элемента `friendlyName` нет атрибутов и дочерних элементов.  
  
## Примеры надстройки VSTO  
  
### Описание  
 В приведенном ниже примере кода показан элемент `friendlyName` в решении на уровне приложения, которое развертывается с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Этот пример кода является частью большего примера, приведенного в разделе [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Код  
  
```  
<vstov4:friendlyName> ContosoOutlookAddIn </vstov4:friendlyName>  
```  
  
## См. также  
 [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md)   
 [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)  
  
  