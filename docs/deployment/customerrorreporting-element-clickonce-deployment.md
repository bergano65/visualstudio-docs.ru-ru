---
title: "Элемент &lt;customErrorReporting&gt; (развертывание ClickOnce) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<customErrorReporting> - элемент [манифест развертывания ClickOnce]"
ms.assetid: 7d31816e-c692-46b5-9cc9-753284b3bcda
caps.latest.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 6
---
# Элемент &lt;customErrorReporting&gt; (развертывание ClickOnce)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Задает универсальный код ресурса \(URI\) для отображения в случае ошибки.  
  
## Синтаксис  
  
```  
<customErrorReporting  
   uri  
/>  
```  
  
## Заметки  
 Этот элемент является необязательным.  Без него [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] выводит сообщение об ошибке со стеком исключения.  Если присутствует элемент `customErrorReporting`, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] будет выводить универсальный код ресурса \(URI\), задаваемый параметром `uri`.  Список параметров целевого универсального кода ресурса \(URI\) будет включать класс внешних исключений, класс внутренних исключений и сообщение внутреннего исключения.  
  
 Этот элемент служит для добавления в приложение функций создания отчетов.  Поскольку создаваемый универсальный код ресурса \(URI\) включают сведения о типе ошибки, веб\-узел может проанализировать эти сведения и отобразить, например, информацию об устранении проблемы.  
  
## Пример  
 В следующем фрагменте показан элемент `customErrorReporting`, а также универсальный код ресурса \(URI\), который может быть им создан.  
  
```  
<customErrorReporting uri=http://www.contoso.com/applications/error.asp />  
  
Example Generated Error:  
http://www.contoso.com/applications/error.asp? outer=System.Deployment.Application.InvalidDeploymentException&&inner=System.Deployment.Application.InvalidDeploymentException&&msg=The%20application%20manifest%20is%20signed,%20but%20the%20deployment%20manifest%20is%20unsigned.%20Both%20manifests%20must%20be%20either%20signed%20or%20unsigned.  
```  
  
## См. также  
 [Манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md)