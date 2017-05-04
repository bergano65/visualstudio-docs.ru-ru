---
title: "элемент &lt;appAddin&gt; (разработка решений Office в Visual Studio) | Microsoft Docs"
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
  - "манифесты приложения [разработка решений Office в Visual Studio], элемент <appAddin>"
ms.assetid: 6152fe5b-6af1-465d-aee7-19e4fd4d04c1
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# элемент &lt;appAddin&gt; (разработка решений Office в Visual Studio)
  Элемент `appAddin` пространства имен `vstov4`  хранит сведения о настройках для надстроек VSTO.  
  
## Синтаксис  
  
```  
<appAddin  
  application  
  loadBehavior  
  keyName>  
  <friendlyName>  
  <description>  
  <formRegions></formRegions>  
</appAddin>  
```  
  
## Элементы и атрибуты  
 Элемент `appAddin` является обязательным и находится в пространстве имен `vstov4` . В манифесте приложения определен только один элемент `appAddin`.  
  
 Элемент `appAddin` имеет перечисленные ниже атрибуты.  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`application`|Обязательный. Идентифицирует приложение Microsoft Office. Может иметь одно из следующих значений: Excel, InfoPath, Outlook, PowerPoint, Project, Visio или Word.|  
|`loadBehavior`|Необязательный. По умолчанию `loadBehavior` включен путем установки значения . Для отладки надстройку VSTO можно отключить, задав значение 2. Дополнительные сведения см. в разделе [Записи реестра для надстроек VSTO](../vsto/registry-entries-for-vsto-add-ins.md).|  
|`keyName`|Обязательный. Это значение является именем раздела реестра, который будет использоваться приложением для загрузки надстройки VSTO. Для получения дополнительной информации см. [Записи реестра для надстроек VSTO](../vsto/registry-entries-for-vsto-add-ins.md).|  
  
 Элемент `appAddin` имеет указанные ниже дочерние элементы.  
  
### friendlyName  
 Необязательный. Элемент `friendlyName` подробно описывается в разделе [Элемент &#60;friendlyName&#62; &#40;разработка решений Office в Visual Studio&#41;](../vsto/friendlyname-element-office-development-in-visual-studio.md).  
  
### описание  
 Необязательный. Элемент `description` подробно описывается в разделе [элемент &#60;description&#62; &#40;разработка решений Office в Visual Studio&#41;](../vsto/description-element-office-development-in-visual-studio.md).  
  
### formRegions  
 Является обязательным только для надстроек VSTO для Outlook, включающих области форм. Элемент `formRegions` подробно описывается в разделе [элемент &#60;formRegions&#62; &#40;разработка решений Office в Visual Studio&#41;](../vsto/formregions-element-office-development-in-visual-studio.md).  
  
## Примеры надстройки VSTO  
  
### Описание  
 В следующем примере кода показаны элементы `appAddin` в решении Outlook, развернутом с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Этот пример кода является частью большего примера, приведенного в разделе [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Код  
  
```  
<vstov4:appAddIn application="Outlook" loadBehavior="3" keyName="ContosoOutlookAddIn"> <vstov4:friendlyName> ContosoOutlookAddIn </vstov4:friendlyName> <vstov4:description> ContosoOutlookAddIn - Outlook VSTO Add-in created with Visual Studio Tools for Office </vstov4:description> <vstov4:formRegions> <vstov4:formRegion name="OutlookAddIn1.FormRegion1"> <vstov4:messageClass name="IPM.Note" /> <vstov4:messageClass name="IPM.Contact" /> <vstov4:messageClass name="IPM.Appointment" /> </vstov4:formRegion> </vstov4:formRegions> </vstov4:appAddIn>  
```  
  
## См. также  
 [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md)   
 [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)  
  
  