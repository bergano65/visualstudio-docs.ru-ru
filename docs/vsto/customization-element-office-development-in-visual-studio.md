---
title: "элемент &lt;customization&gt; (разработка решений Office в Visual Studio)"
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
  - "манифесты приложения [разработка решений Office в Visual Studio], элемент <customization>"
ms.assetid: a3bf7f35-bd98-4530-9226-46489cd37bb1
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# элемент &lt;customization&gt; (разработка решений Office в Visual Studio)
  Элемент `customization` пространства имен `vstov4` описывает конкретное решение Office. Дочерние элементы настроек уровня документа и надстроек VSTO отличаются друг от друга.  
  
## Синтаксис настроек уровня документа  
  
```  
<customization id <document solutionId /> </customization>  
```  
  
## Синтаксис надстроек VSTO  
  
```  
<customization id <appAddin application loadBehavior keyName> <friendlyName></friendlyName> <description></description> <formRegions></formRegions> </customization>  
```  
  
## Элементы и атрибуты  
 Элемент `customization` содержит сведения о настройках. Этот элемент должен принадлежать следующему пространству имен: `vstov4=urn:schemas-microsoft-com:vsto.v4`. Существует по одному элементу `customization` для каждого решения Office. Например, при развертывании трех решений Office в многопроектном развертывании в манифесте приложения будет существовать три элемента `customization`.  
  
 Дочерние элементы сборки также должны быть в этом пространство имен.  
  
 Элемент `customization` имеет указанный ниже атрибут.  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`id`|Требуется для многопроектного развертывания. Элемент `id` уникальным образом идентифицирует решение Office.|  
  
### Настройки уровня документа  
 Элемент `customization` имеет указанный ниже дочерний элемент.  
  
#### документ  
 Элемент `document` в пространстве имен `vstov4` описывается в разделе [элемент &#60;document&#62; &#40;разработка решений Office в Visual Studio&#41;](../vsto/document-element-office-development-in-visual-studio.md).  
  
### Надстройки VSTO  
 Элемент `customization` имеет указанный ниже дочерний элемент.  
  
#### appAddin  
 Элемент `appAddin` в пространстве имен `vstov4` описывается в разделе [элемент &#60;appAddin&#62; &#40;разработка решений Office в Visual Studio&#41;](../vsto/appaddin-element-office-development-in-visual-studio.md).  
  
## Пример настройки на уровне документа  
  
### Описание  
 В приведенном ниже примере кода показан элемент `customization` для настройки на уровне документа. Этот пример кода является частью большего примера, приведенного в разделе [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Код  
  
```  
<vstov4:customization> <vstov4:document solutionId="73e" /> </vstov4:customization>  
```  
  
## Пример надстройки VSTO  
  
### Описание  
 В приведенном ниже примере кода показан элемент `customization` для надстройки VSTO. Это надстройка VSTO для Outlook, в которой используются области форм. Этот пример кода является частью большего примера, приведенного в разделе [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Код  
  
```  
<vstov4:customization> <vstov4:appAddIn application="Outlook" loadBehavior="3" keyName="ContosoOutlookAddIn"> <vstov4:friendlyName> ContosoOutlookAddIn </vstov4:friendlyName> <vstov4:description> ContosoOutlookAddIn - Outlook VSTO Add-in created with Visual Studio Tools for Office </vstov4:description> <vstov4:formRegions> <vstov4:formRegion name="OutlookAddIn1.FormRegion1"> <vstov4:messageClass name="IPM.Note" /> <vstov4:messageClass name="IPM.Contact" /> <vstov4:messageClass name="IPM.Appointment" /> </vstov4:formRegion> </vstov4:formRegions> </vstov4:appAddIn> </vstov4:customization>  
```  
  
## См. также  
 [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md)   
 [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)  
  
  