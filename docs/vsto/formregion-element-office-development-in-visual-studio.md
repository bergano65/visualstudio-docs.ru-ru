---
title: "Элемент &lt;formRegion&gt; (разработка решений Office в Visual Studio)"
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
  - "манифесты приложения [разработка решений Office в Visual Studio], элемент <formRegion>"
ms.assetid: d397cf31-c0ef-47f0-860a-cd816e4bf6eb
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# Элемент &lt;formRegion&gt; (разработка решений Office в Visual Studio)
  Элемент `formRegion` пространства имен `vstov4`  определяет область формы Microsoft Office Outlook, связанную с надстройкой VSTO.  
  
## Синтаксис  
  
```  
<formRegion  
  name>  
  <messageClass  
    name/>  
</formRegion>  
```  
  
## Элементы и атрибуты  
 Элемент `formRegion` пространства имен `vstov4`  определяет область формы, связанную с надстройкой VSTO для Outlook. Этот элемент является обязательным только для надстроек VSTO для Outlook, в которых есть области форм.  
  
 Для одной и той же надстройки VSTO можно определить несколько элементов `formRegion` в рамках элемента `formRegions`.  
  
 Элемент `formRegion` имеет перечисленные ниже атрибуты.  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`name`|Обязательный. Определяет имя области формы.|  
  
 Элемент `formRegion` имеет указанные ниже дочерние элементы.  
  
### messageClass  
 Элемент `messageClass`  определяет форму Outlook, которая связана с областью формы.  
  
 Элемент `messageClass` имеет указанный ниже атрибут.  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`name`|Обязательный. Определяет форму, которая связана с областью формы.|  
  
## Пример  
 В приведенном ниже примере кода показан элемент `formRegion` манифеста приложения для надстройки VSTO для Outlook, развертываемой с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Имеется три класса сообщений, связанных с одной и той же областью формы. Этот пример кода является частью большего примера, приведенного в разделе [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).  
  
```  
<vstov4:formRegion name="OutlookAddIn1.FormRegion1"> <vstov4:messageClass name="IPM.Note" /> <vstov4:messageClass name="IPM.Contact" /> <vstov4:messageClass name="IPM.Appointment" /> </vstov4:formRegion>  
```  
  
## См. также  
 [Создание областей форм Outlook](../vsto/creating-outlook-form-regions.md)   
 [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md)   
 [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)  
  
  