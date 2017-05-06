---
title: "элемент &lt;formRegions&gt; (разработка решений Office в Visual Studio)"
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
  - "formRegions - элемент"
  - "элемент <formRegions>"
  - "манифесты приложения [разработка решений Office в Visual Studio], элемент <formRegions>"
ms.assetid: 71faa2da-9d38-43e8-9d7d-0bcd944ef9a3
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# элемент &lt;formRegions&gt; (разработка решений Office в Visual Studio)
  Элемент `formRegions` пространства имен `vstov4`  содержит области формы Microsoft Office Outlook, связанные с надстройкой VSTO.  
  
## Синтаксис  
  
```  
<formRegions>  
  <formRegion>  
  </formRegion>  
</formRegions>  
```  
  
## Элементы и атрибуты  
 Элемент `formRegions` пространства имен `vstov4`  содержит все элементы `formRegion` для надстройки VSTO для Outlook. Этот элемент является обязательным только для надстроек VSTO для Outlook, в которых есть области форм.  
  
 В манифесте приложения может быть определен только один элемент `formRegions`.  
  
 У элемента `formRegions` нет атрибутов.  
  
 Элемент `formRegions` имеет следующий элемент.  
  
### formRegion  
 Является обязательным для надстроек VSTO для Outlook, включающих области форм. Элемент `formRegion` определен в разделе [Элемент &#60;formRegion&#62; &#40;разработка решений Office в Visual Studio&#41;](../vsto/formregion-element-office-development-in-visual-studio.md)  
  
## Примеры надстройки VSTO  
  
### Описание  
 В приведенном ниже примере кода показан элемент `formRegions` в манифесте приложения для решения Office уровня приложения, которое развертывается с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Этот пример кода является частью большего примера, приведенного в разделе [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Код  
  
```  
<vstov4:formRegions> <vstov4:formRegion name="OutlookAddIn1.FormRegion1"> <vstov4:messageClass name="IPM.Note" /> <vstov4:messageClass name="IPM.Contact" /> <vstov4:messageClass name="IPM.Appointment" /> </vstov4:formRegion> </vstov4:formRegions>  
```  
  
## См. также  
 [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md)   
 [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)  
  
  