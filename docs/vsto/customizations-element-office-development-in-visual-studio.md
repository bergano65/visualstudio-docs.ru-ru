---
title: "Элемент &lt;customizations&gt; (разработка решений Office в Visual Studio) | Microsoft Docs"
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
  - "элемент <customizations>"
  - "customizations - элемент"
  - "манифесты приложения [разработка решений Office в Visual Studio], элемент <customizations>"
ms.assetid: fe1133ef-5fdf-4945-a67b-55a66a4e2109
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Элемент &lt;customizations&gt; (разработка решений Office в Visual Studio)
  Элемент `customizations` пространства имен `vstov4` содержит все сведения об установке и загрузке каждого решения Office.  
  
## Синтаксис настроек на уровне документа  
  
```  
<customizations> <customization id <document solutionId /> </customization> </customizations>  
```  
  
## Синтаксис надстроек VSTO  
  
```  
<customizations> <customization id <appAddin application loadBehavior keyName> <friendlyName></friendlyName> <description></description> <formRegions></formRegions> </customization> </customizations>  
```  
  
## Элементы и атрибуты  
 Элемент `customizations` содержит конкретные сведения о каждом решении Office. Этот элемент должен принадлежать следующему пространству имен: `vstov4=urn:schemas-microsoft-com:vsto.v4`. Дочерние элементы сборки также необходимо включить в это пространство имен.  
  
 У элемента `customizations` нет атрибутов.  
  
 Элемент `customizations` имеет указанный ниже дочерний элемент.  
  
### настройка  
 Обязательный. Определение элемента `customization` в пространстве имен `vstov4` содержится в разделе [элемент &#60;customization&#62; &#40;разработка решений Office в Visual Studio&#41;](../vsto/customization-element-office-development-in-visual-studio.md).  
  
## Пример настройки на уровне документа  
  
### Описание  
 В приведенном ниже примере кода показан элемент `customizations` для настройки на уровне документа.  
  
> [!NOTE]  
>  Этот пример кода является частью большего примера, приведенного в разделе [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Код  
  
```  
<vstov4:customizations xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4"> <vstov4:customization> <vstov4:document solutionId="73e" /> </vstov4:customization> </vstov4:customizations>  
```  
  
## Пример надстройки VSTO  
  
### Описание  
 В приведенном ниже примере кода показан элемент `customizations` для надстройки VSTO. Это надстройка VSTO для Outlook, в которой используются области форм. Этот пример кода является частью большего примера, приведенного в разделе [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Код  
  
```  
<vstov4:customizations xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4"> <vstov4:customization> <vstov4:appAddIn application="Outlook" loadBehavior="3" keyName="ContosoOutlookAddIn"> <vstov4:friendlyName> ContosoOutlookAddIn </vstov4:friendlyName> <vstov4:description> ContosoOutlookAddIn - Outlook VSTO Add-in created with Visual Studio Tools for Office </vstov4:description> <vstov4:formRegions> <vstov4:formRegion name="OutlookAddIn1.FormRegion1"> <vstov4:messageClass name="IPM.Note" /> <vstov4:messageClass name="IPM.Contact" /> <vstov4:messageClass name="IPM.Appointment" /> </vstov4:formRegion> </vstov4:formRegions> </vstov4:appAddIn> </vstov4:customization> </vstov4:customizations>  
```  
  
## См. также  
 [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md)   
 [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)  
  
  