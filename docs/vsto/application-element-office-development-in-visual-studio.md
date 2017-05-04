---
title: "элемент &lt;application&gt; (разработка решений Office в Visual Studio) | Microsoft Docs"
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
  - "манифесты приложения [разработка решений Office в Visual Studio], элемент <application>"
ms.assetid: b8d3db7c-9127-4812-b18f-bb17e1f8788f
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# элемент &lt;application&gt; (разработка решений Office в Visual Studio)
  Элемент `application` пространства имен `vstav3` служит оболочкой для описания решений Office. Дочерние элементы настроек уровня документа и надстроек VSTO отличаются друг от друга.  
  
## Синтаксис настроек уровня документа  
  
```  
<application> <customization id <document solutionId /> </customization> </application>  
```  
  
## Синтаксис надстроек уровня приложения  
  
```  
<application> <customization id <appAddin application loadBehavior keyName> <friendlyName></friendlyName> <description></description> <formRegions></formRegions> </customization> </application>  
```  
  
## Элементы и атрибуты  
 Элемент `application` пространства имен `vstav3` — это узел, который включает все сведения о настройке, содержащиеся в пространстве имен `vstov4`.  
  
 У элемента `application` нет атрибутов.  
  
 Элемент `application` имеет следующий элемент.  
  
### настройка  
 Роль элемента `customization` в пространстве имен `vstov3` определена в разделе [элемент &#60;customization&#62; &#40;разработка решений Office в Visual Studio&#41;](../vsto/customization-element-office-development-in-visual-studio.md).  
  
## Пример настройки на уровне документа  
  
### Описание  
 В следующем примере кода показан элемент `application` в решении Office уровня документа, развернутом с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Этот пример кода является частью большего примера, приведенного в разделе [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Код  
  
```  
<vstav3:application> <vstov4:customizations xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4"> <vstov4:customization> <vstov4:document solutionId="73e" /> </vstov4:customization> </vstov4:customizations> </vstav3:application>  
```  
  
## Примеры надстройки VSTO  
  
### Описание  
 В следующем примере кода показан элемент `application` в решении Office уровня приложения, развернутом с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Этот пример кода является частью большего примера, приведенного в разделе [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Код  
  
```  
<vstav3:application> <vstov4:customizations xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4"> <vstov4:customization> <vstov4:appAddIn application="Outlook" loadBehavior="3" keyName="ContosoOutlookAddIn"> <vstov4:friendlyName> ContosoOutlookAddIn </vstov4:friendlyName> <vstov4:description> ContosoOutlookAddIn - Outlook VSTO Add-in created with Visual Studio Tools for Office </vstov4:description> <vstov4:formRegions> <vstov4:formRegion name="OutlookAddIn1.FormRegion1"> <vstov4:messageClass name="IPM.Note" /> <vstov4:messageClass name="IPM.Contact" /> <vstov4:messageClass name="IPM.Appointment" /> </vstov4:formRegion> </vstov4:formRegions> </vstov4:appAddIn> </vstov4:customization> </vstov4:customizations> </vstav3:application>  
```  
  
## См. также  
 [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md)   
 [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)  
  
  