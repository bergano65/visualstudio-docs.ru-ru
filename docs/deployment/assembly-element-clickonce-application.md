---
title: "Элемент &lt;assembly&gt; (приложение ClickOnce) | Microsoft Docs"
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
  - "urn:schemas-microsoft-com:asm.v2#assembly"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<assembly> - элемент [манифест приложения ClickOnce]"
ms.assetid: 51410569-10f9-4c0a-96b5-d39185edbefc
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Элемент &lt;assembly&gt; (приложение ClickOnce)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Элемент верхнего уровня манифеста приложения.  
  
## Синтаксис  
  
```  
  
      <assembly  
   manifestVersion  
/>  
```  
  
## Элементы и атрибуты  
 Элемент `assembly` является корневым и обязательным элементом.  Его первым вложенным элементом должен быть элемент `assemblyIdentity`.  Элементы манифеста должны принадлежать следующему пространству имен:  
  
 `urn:schemas-microsoft-com:asm.v1`  
  
 `urn:schemas-microsoft-com:asm.v2`  
  
 `http://www.w3.org/2000/09/xmldsig#`  
  
 Дочерние элементы сборки также необходимо включить в эти пространства имен путем наследования или маркировки.  
  
 Элемент `assembly` имеет следующий атрибут.  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`manifestVersion`|Обязательный.  Атрибут `manifestVersion` должен иметь значение `1.0`.|  
  
## Пример  
 В следующем примере кода показан элемент `assembly` файла  манифеста приложения для приложения [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Данный пример кода является частью большего примера, приведенного в разделе [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md).  
  
```  
<asmv1:assembly   
  xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"   
  manifestVersion="1.0"   
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"  
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#  
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"  
  xmlns="urn:schemas-microsoft-com:asm.v2"  
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"  
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"  
  xmlns:xsi=http://www.w3.org/2001/XMLSchema-instance  
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1">  
```  
  
## См. также  
 [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)   
 [Элемент \<assembly\>](../deployment/assembly-element-clickonce-deployment.md)