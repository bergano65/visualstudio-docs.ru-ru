---
title: "Элемент &lt;postActionData&gt; (разработка решений Office в Visual Studio)"
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
  - "элемент <postActionData>"
  - "манифесты приложения [разработка решений Office в Visual Studio], элемент <postActionData>"
  - "postActionData - элемент"
ms.assetid: e36cbd64-fd27-4413-b293-cf5546fbdfaf
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# Элемент &lt;postActionData&gt; (разработка решений Office в Visual Studio)
  Элемент `postActionData` пространства имен `vstav3`  указывает данные, связанные с действиями, выполняемыми после развертывания при установке решений Office.  
  
## Синтаксис  
  
```  
<postActionData>  
</postActionData>  
```  
  
## Элементы и атрибуты  
 Элемент `postActionData` является необязательным и находится в пространстве имен `vstav3` . В манифесте приложения определяется один элемент `postActionData` для каждого выполняемого после развертывания действия.  
  
 У элемента `postActions` нет атрибутов.  
  
 У элемента `postActions` нет дочерних элементов.  
  
## Пример действия, выполняемого после развертывания  
  
### Описание  
 В приведенном ниже примере кода показан элемент `postAction` манифеста приложения для решения Office, развертываемого с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Этот пример кода является частью большего примера, приведенного в разделе [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Код  
  
```  
<vstav3:postActionData> data in any format </vstav3:postActionData>  
```  
  
## См. также  
 [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md)   
 [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)  
  
  