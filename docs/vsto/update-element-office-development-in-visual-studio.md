---
title: "элемент &lt;update&gt; (разработка решений Office в Visual Studio) | Microsoft Docs"
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
  - "update - элемент"
  - "элемент <update>"
  - "манифесты приложений [разработка решений Office в Visual Studio], элемент <update>"
ms.assetid: bdd5dbf7-ddda-4ef6-9db5-1fb4405261a0
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# элемент &lt;update&gt; (разработка решений Office в Visual Studio)
  Элемент `update` определяет периодичность, с которой решение проверяет наличие обновлений.  
  
## Синтаксис  
  
```  
<update  
  enabled>  
  <expiration  
    maximumAge  
    unit  
  />  
</update>  
```  
  
## Элементы и атрибуты  
 Элемент `update` является обязательным и находится в пространстве имен `vstav3`.  
  
 Элемент `update` имеет следующие атрибуты.  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`enabled`|Обязательный.  Установите для атрибута «enabled» одно из следующих значений:<br /><br /> -   **ИСТИНА**, чтобы включить проверку обновлений.<br />-   **ЛОЖЬ**, чтобы отключить проверку обновлений.|  
  
 Элемент `update` имеет следующие дочерние элементы.  
  
### expiration  
 Элемент `expiration` является обязательным и находится в пространстве имен `vstav3`.  Этот элемент определяет периодичность, с которой решение проверяет наличие обновлений.  
  
 Элемент `expiration` имеет следующие атрибуты.  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`maximumAge`|-   Обязательный.  Значение этого атрибута должно быть целым числом.|  
|`unit`|Обязательный.  `unit` может иметь одно из следующих значений:<br /><br /> -   **hours**<br />-   **days**<br />-   **weeks**|  
  
## Пример кода с постоянной проверкой обновлений  
  
### Описание  
 В следующем примере кода показан элемент `update`, для которого установлено значение, обеспечивающее постоянную проверку обновлений в решениях Office.  
  
### Код  
  
```  
<vstav3:update enabled="true" />  
```  
  
## Пример кода с установленным интервалом проверки по умолчанию  
  
### Описание  
 В следующем примере кода показан элемент `update` манифеста приложения для решений Office.  Данный пример кода является частью большего примера, приведенного в разделе [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Код  
  
```  
<vstav3:update enabled="true">  
    <vstav3:expiration maximumAge="7" unit="days" />  
</vstav3:update>  
```  
  
## См. также  
 [Развертывание решения Office с помощью ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md)   
 [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)  
  
  