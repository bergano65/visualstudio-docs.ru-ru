---
title: "элемент &lt;document&gt; (разработка решений Office в Visual Studio) | Microsoft Docs"
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
  - "document - элемент"
  - "манифесты приложений [разработка решений Office в Visual Studio], элемент <document>"
  - "элемент <document>"
ms.assetid: b4525a0e-8a03-4881-a3e2-8cc019029071
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# элемент &lt;document&gt; (разработка решений Office в Visual Studio)
  Элемент `document` пространства имен `vstov4` хранит сведения о настройках для настроек уровня документа.  
  
## Синтаксис  
  
```  
<document solutionId />  
```  
  
## Элементы и атрибуты  
 Данный элемент является обязательным только для настроек на уровне документа.  Элемент `document` находится в пространстве имен `vstov4` .  Элемент `document` имеет следующие атрибуты.  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`solutionId`|Обязательный.  GUID, используемый среды выполнения Visual Studio tools for office для уникального определения решения уровня документа.  Это значение хранится в настраиваемом свойстве документа «\_AssemblyLocation».  Дополнительные сведения см. в разделе [Общие сведения о настраиваемых свойствах документа](../vsto/custom-document-properties-overview.md).|  
  
 Элемент `document` не имеет дочерних элементов.  
  
## Пример настройки на уровне документа  
  
### Описание  
 В следующем примере кода показан элемент `document` в решении Office на уровне документа, развертываемом с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)].  Данный пример кода является частью большего примера, приведенного в разделе [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Код  
  
```  
<vstov4:document   
  solutionId="73e" />  
```  
  
## См. также  
 [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md)   
 [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)  
  
  