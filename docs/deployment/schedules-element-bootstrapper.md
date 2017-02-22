---
title: "Элемент &lt;Schedules&gt; (загрузчик) | Microsoft Docs"
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
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<Schedules> - элемент [загрузчик]"
ms.assetid: 28d094cf-64f5-42b1-bd8a-3697082aab4f
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Элемент &lt;Schedules&gt; (загрузчик)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Элемент `Schedules` содержит элементы `Schedule`, которые определяют времена запуска команд, определенных в элементе `Command`.  
  
## Синтаксис  
  
```  
<Schedules>  
    <Schedule  
        Name  
    >  
        <BuildList />  
        <BeforePackage />  
        <AfterPackage />  
    </Schedule>  
</Schedules>  
```  
  
## Элементы и атрибуты  
 Элемент `Schedules` является дочерним для элемента `Product`.  Каждый элемент `Product` может содержать не более одного элемента `Schedules`.  У элемента `Schedules` отсутствуют атрибуты.  
  
## Schedule  
 Элемент `Schedule` является дочерним для элемента `Schedules`.  Элемент `Schedules` должен иметь по крайней мере один элемент `Schedule`.  
  
 Элемент `Schedule` имеет следующий атрибут.  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`Name`|Обязательный.  Имя элемента Schedule.  Соответствует свойству `ScheduleName` элемента `Command`.  Если элемент `Command` ссылается на именованное расписание, он будет выполняться только во время, определенное в элементе `Schedule`.  Расписания также могут быть связаны с элементами `FailIf` и `BypassIf`, которые ограничивают эти условия выполнения по определенному расписанию.  Дополнительные сведения см. в разделе [Элемент \<Commands\>](../deployment/commands-element-bootstrapper.md).|  
  
 Данный элемент `Schedule` может иметь только один из следующих дочерних элементов.  
  
## BuildList  
 Элемент `BuildList` дает указания установщику выполнять команду немедленно после запуска загрузочного приложения.  
  
## BeforePackage  
 Элемент `BeforePackage` дает указания установщику выполнять команду перед установкой указанного пакета.  
  
## AfterPackage  
 Элемент `AfterPackage` дает указания установщику выполнять команду после установки указанного пакета.  
  
## См. также  
 [Элемент \<Product\>](../deployment/product-element-bootstrapper.md)   
 [Справочные сведения о схеме пакетов и продуктов](../deployment/product-and-package-schema-reference.md)