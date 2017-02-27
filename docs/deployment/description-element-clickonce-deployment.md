---
title: "Элемент &lt;description&gt; (развертывание ClickOnce) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "urn:schemas-microsoft-com:asm.v2#description"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<description> - элемент [манифест развертывания ClickOnce]"
ms.assetid: 18f6919e-a3ab-4942-a57d-167fabfac44e
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# Элемент &lt;description&gt; (развертывание ClickOnce)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Идентифицирует сведения о приложении, используемом для присутствия в оболочке и создания элемента **Установка или удаление программ** в панели управления.  
  
## Синтаксис  
  
```  
  
      <description   
   publisher   
   product  
   suiteName  
   supportUrl  
/>  
```  
  
## Элементы и атрибуты  
 Элемент `description` является обязательным и находится в пространстве имен `urn:schemas-microsoft-com:asm.v1`.  Не содержит дочерних элементов и имеет следующие атрибуты.  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`publisher`|Обязательный.  Идентифицирует имя компании, используемое для значка в меню **Пуск** Windows и для элемента **Установка или удаление программ** в панели управления, когда развертывание конфигурируется для установки.|  
|`product`|Обязательный.  Идентифицирует полное имя продукта.  Используется в качестве названия значка, установленного в меню **Пуск** системы Windows.|  
|`suiteName`|Необязательный.  Указывает вложенную папку в папке `publisher` меню **Пуск** Windows.|  
|`supportUrl`|Необязательный.  Задает поддержку URL, который показан в элементе **Установка или удаление программ** в панели управления.  Ярлык к этому URL также создается для поддержки приложения в меню **Пуск** системы Windows, когда развертывание конфигурируется для установки.|  
  
## Заметки  
 Элемент описания необходим во всех конфигурациях развертывания.  
  
## Пример  
 В следующем примере кода показан элемент `description` в манифесте развертывания [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Данный пример кода является частью большего примера, приведенного для раздела [ClickOnce Deployment Manifest](../deployment/clickonce-deployment-manifest.md).  
  
```  
<description   
  asmv2:publisher="My Company Name"  
  asmv2:product="My Application"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## См. также  
 [Манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md)