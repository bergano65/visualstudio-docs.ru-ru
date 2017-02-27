---
title: "Элемент &lt;assembly&gt; (развертывание ClickOnce) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "urn:schemas-microsoft-com:asm.v2#assembly"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<assembly> - элемент [манифест развертывания ClickOnce]"
ms.assetid: b8e3362a-f821-4696-b98d-571d4bbfe431
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# Элемент &lt;assembly&gt; (развертывание ClickOnce)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Элемент верхнего уровня для манифеста развертывания.  
  
## Синтаксис  
  
```  
  
      <assembly    
   manifestVersion  
/>  
```  
  
## Элементы и атрибуты  
 Элемент `assembly` является корневым и обязательным элементом.  Его первым вложенным элементом должен быть элемент `assemblyIdentity`.  Элементы манифеста должны располагаться в следующих пространствах имен: `urn:schemas-microsoft-com:asm.v1`, `urn:schemas-microsoft-com:asm.v2` и `http://www.w3.org/2000/09/xmldsig#`.  Дочерние элементы сборки также необходимо включить в эти пространства имен путем наследования или маркировки.  
  
 Элемент `assembly` имеет следующий атрибут.  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`manifestVersion`|Обязательный.  Этому атрибуту должно быть присвоено значение `1.0`.|  
  
## Пример  
 В следующем примере кода показан элемент `assembly` в манифесте развертывания для приложения, развертываемого с помощью [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Данный пример кода является частью большего примера, приведенного для раздела [ClickOnce Deployment Manifest](../deployment/clickonce-deployment-manifest.md).  
  
```  
<asmv1:assembly   
  xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"  
  manifestVersion="1.0"  
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"  
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#  
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1"  
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"  
  xmlns="urn:schemas-microsoft-com:asm.v2"  
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"  
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"  
  xmlns:xrml="urn:mpeg:mpeg21:2003:01-REL-R-NS"  
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
```  
  
## См. также  
 [Манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [Элемент \<assembly\>](../deployment/assembly-element-clickonce-application.md)