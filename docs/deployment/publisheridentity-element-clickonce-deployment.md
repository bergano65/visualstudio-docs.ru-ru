---
title: "Элемент &lt;publisherIdentity&gt; (развертывание ClickOnce) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
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
  - "publisherIdentity - элемент [манифест развертывания ClickOnce], введение"
  - "publisherIdentity - элемент [манифест развертывания ClickOnce], синтаксис, элементы, и атрибуты"
  - "обязательный элемент подписанных манифестов [ClickOnce], publisherIdentity - элемент"
ms.assetid: 34c579db-d2f2-4b66-b9c8-47207f33d950
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Элемент &lt;publisherIdentity&gt; (развертывание ClickOnce)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Содержит сведения об издателе, подписавшем этот манифест развертывания.  
  
## Синтаксис  
  
```  
<publisherIdentity  
   name  
   issuerKeyHash  
/>  
```  
  
## Элементы и атрибуты  
 Элемент `publisherIdentity` необходим для подписанных манифестов.  В следующей таблице приведены поддерживаемые атрибуты элемента `publisherIdentity`.  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`name`|Обязательный.  Идентифицирует сторону, подписавшую приложение.|  
|`issuerKeyHash`|Обязательный.  Содержит хэш SHA\-1 публичного ключа издателя сертификата.|  
  
#### Параметры  
  
## Значение свойства или возвращаемое значение  
  
## Исключения  
  
## Заметки  
  
## Требования  
  
## Подзаголовок