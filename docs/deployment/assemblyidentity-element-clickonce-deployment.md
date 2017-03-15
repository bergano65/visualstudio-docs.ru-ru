---
title: "Элемент &lt;assemblyIdentity&gt; (развертывание ClickOnce) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "urn:schemas-microsoft-com:asm.v2#assemblyIdentity"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<assemblyIdentity> - элемент [манифест развертывания ClickOnce]"
ms.assetid: f4a3bb83-c800-47d0-9905-9a5ae2486838
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 23
---
# Элемент &lt;assemblyIdentity&gt; (развертывание ClickOnce)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Определяет основную сборку приложения [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
## Синтаксис  
  
```  
  
      <assemblyIdentity    
   name   
   version  
   publicKeyToken  
   processorArchitecture  
    type  
/>  
```  
  
## Элементы и атрибуты  
 Элемент `assemblyIdentity` является обязательным.  Не содержит дочерних элементов и имеет следующие атрибуты.  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`name`|Обязательный.  Задает понятное для человека имя развертывания для справочных целей.<br /><br /> Если `name` содержит специальные знаки, такие как одинарные или двойные кавычки, это может вызвать сбой активации приложения.|  
|`version`|Обязательный.  Задает номер версии сборки в следующем формате: `основной.дополнительный.построение.редакция.`<br /><br /> Для начала обновления приложения необходимо увеличить это значение.|  
|`publicKeyToken`|Обязательный.  Задает 16\-символьную шестнадцатеричную строку, которая представляет последние 8 байтов хэша SHA\-1 открытого ключа, которым подписывается манифест развертывания.  Открытый ключ, используемый для подписи, должен иметь длину не менее 2048 бит.<br /><br /> Подписывать сборки рекомендуется, хотя и не обязательно, но этот атрибут является обязательным.  Если сборка не подписана, необходимо скопировать значение из самозаверенной сборки или использовать фиктивное значение, состоящее из всех нулей.|  
|`processorArchitecture`|Обязательный.  Задает процессор.  Возможны следующие значения: `msil` для всех процессоров, `x86` для 32\-разрядной системы Windows, `IA64` для 64\-разрядной системы Windows и `Itanium` для 64\-разрядных процессоров Intel Itanium.|  
|`type`|Обязательный.  Для совместимости с технологией параллельной установки Windows.  Единственным допустимым значением является `win32`.|  
  
## Заметки  
  
## Пример  
 В следующем примере кода показан элемент `assemblyIdentity` в манифесте развертывания [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Данный пример кода является частью большого примера, приведенного в разделе [Манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md).  
  
```  
<!-- Identify the deployment. -->  
<assemblyIdentity   
  name="My Application Deployment.app"  
  version="1.0.0.0"  
  publicKeyToken="43cb1e8e7a352766"  
  language="neutral"  
  processorArchitecture="x86"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## См. также  
 [Манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [Элемент \<assemblyIdentity\>](../deployment/assemblyidentity-element-clickonce-application.md)