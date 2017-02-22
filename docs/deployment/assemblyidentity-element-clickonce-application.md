---
title: "Элемент &lt;assemblyIdentity&gt; (приложение ClickOnce) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
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
  - "<assemblyIdentity> - элемент [манифест приложения ClickOnce]"
ms.assetid: f48e9531-efac-4d11-8166-f63a5ece1ac5
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Элемент &lt;assemblyIdentity&gt; (приложение ClickOnce)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Идентифицирует приложение, развертываемое в рамках [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
## Синтаксис  
  
```  
  
      <assemblyIdentity   
   name  
   version  
   publicKeyToken  
   processorArchitecture  
   language  
/>  
```  
  
## Элементы и атрибуты  
 Элемент `assemblyIdentity` является обязательным.  Не содержит дочерних элементов и имеет следующие атрибуты.  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`Name`|Обязательный.  Идентифицирует имя приложения.<br /><br /> Если `Name` содержит специальные знаки, такие как одинарные или двойные кавычки, это может вызвать сбой активации приложения.|  
|`Version`|Обязательный.  Задает номер версии приложения в следующем формате: `основной.дополнительный.построение.редакция`.|  
|`publicKeyToken`|Необязательный.  Задает 16\-символьную шестнадцатеричную строку, которая представляет последние 8 байтов хэша `SHA-1` открытого ключа, которым подписывается приложение или сборка.  Открытый ключ, используемый для подписи каталога, должен иметь длину не менее 2048 бит.<br /><br /> Подписывать сборки рекомендуется, хотя и не обязательно, но этот атрибут является обязательным.  Если сборка не подписана, необходимо скопировать значение из самозаверенной сборки или использовать фиктивное значение, состоящее из всех нулей.|  
|`processorArchitecture`|Обязательный.  Задает процессор.  Возможны следующие значения: `msil` для всех процессоров, `x86` для 32\-разрядной системы Windows, `IA64` для 64\-разрядной системы Windows и `Itanium` для 64\-разрядных процессоров Intel Itanium.|  
|`language`|Обязательный.  Идентифицирует двухкомпонентные коды языка сборки, например `en-US`.  Этот элемент находится в пространстве имен `asmv2`.  Если данный элемент не задан, по умолчанию используется значение `neutral`.|  
  
## Примеры  
  
### Описание  
 В следующем примере кода показан элемент `assemblyIdentity` в манифесте приложения[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Данный пример кода является частью большего примера, приведенного в разделе [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md).  
  
### Код  
  
```  
<asmv1:assemblyIdentity   
  name="My Application Deployment.exe"   
  version="1.0.0.0"   
  publicKeyToken="43cb1e8e7a352766"   
  language="neutral"   
  processorArchitecture="x86"   
  type="win32" />  
```  
  
## См. также  
 [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)   
 [Элемент \<assemblyIdentity\>](../deployment/assemblyidentity-element-clickonce-deployment.md)