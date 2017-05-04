---
title: "Элемент &lt;vstoRuntime&gt; (разработка решений Office в Visual Studio) | Microsoft Docs"
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
  - "манифесты приложения [разработка решений Office в Visual Studio], элемент <vstoRuntime>"
  - "элемент <vstoRuntime>"
  - "vstoRuntime - элемент"
ms.assetid: e59a8a61-9ff2-4032-9983-4a1e289e70a7
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# Элемент &lt;vstoRuntime&gt; (разработка решений Office в Visual Studio)
  Элемент `vstoRuntime` пространства имен `vstav3`  содержит версию среды выполнения Набора инструментов Visual Studio для Office, поддерживаемую конкретным решением Office.  
  
## Синтаксис  
  
```  
<vstoRuntime  
    release  
    version  
    supportUrl />  
```  
  
## Элементы и атрибуты  
 Элемент `vstoRuntime` является обязательным и находится в пространстве имен `vstav3` . Если решение Office поддерживает две версии среды выполнения Набора инструментов Visual Studio для Office, в манифесте приложения будет два элемента `vstoRuntime`.  
  
 Элемент `vstoRuntime` имеет перечисленные ниже атрибуты.  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`release`|Обязательный. Выпускаемая версия среды выполнения Набора инструментов Visual Studio для Office.|  
|`version`|Обязательный. Номер версии среды выполнения Набора инструментов Visual Studio для Office.|  
|`supportUrl`|Необязательный. Ссылка на расположение установки среды выполнения Набора инструментов Visual Studio для Office.|  
  
 Элемент `vstoRuntime` не содержит элементов.  
  
## Пример  
 В приведенном ниже примере кода показан элемент `vstoRuntime` манифеста приложения для решения Office, развертываемого с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Этот пример кода является частью большего примера, приведенного в разделе [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).  
  
```  
<vstav3:vstoRuntime release="VSTOR40Beta1" version="10.0.20303" supportUrl="http://www.microsoft.com" />  
```  
  
## См. также  
 [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md)   
 [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)  
  
  