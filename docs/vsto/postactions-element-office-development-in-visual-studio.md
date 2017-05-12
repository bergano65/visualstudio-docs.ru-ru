---
title: "элемент &lt;postActions&gt; (разработка решений Office в Visual Studio)"
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
  - "манифесты приложения [разработка решений Office в Visual Studio], элемент <postActions>"
  - "postActions - элемент"
  - "элемент <postActions>"
ms.assetid: 6e487549-fdd6-49bd-be7a-b91f1f964594
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# элемент &lt;postActions&gt; (разработка решений Office в Visual Studio)
  Элемент `postActions` пространства имен `vstav3`  содержит все элементы `postAction` , описывающие действия после развертывания, которые выполняются после установки решений Office.  
  
## Синтаксис  
  
```  
<postActions>  
  <postAction>  
    <entryPoint>  
    </entryPoint>  
    <postActionData>  
    </postActionData>  
  </postAction>  
</postActions>  
```  
  
## Элементы и атрибуты  
 Элемент `postActions` является необязательным и находится в пространстве имен `vstav3` . В манифесте приложения определен только один элемент `postActions`.  
  
 У элемента `postActions` нет атрибутов.  
  
 Объект `postActions` имеет следующий элемент.  
  
### postAction  
 Необязательный. Роль элемента `postAction` в пространстве имен `vstav3`  определена в разделе [элемент &#60;postAction&#62; &#40;разработка решений Office в Visual Studio&#41;](../vsto/postaction-element-office-development-in-visual-studio.md).  
  
## Пример действия, выполняемого после развертывания  
  
### Описание  
 В приведенном ниже примере кода показан элемент `postActions` манифеста приложения для решения Office, развертываемого с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Этот пример кода является частью большего примера, приведенного в разделе [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Код  
  
```  
<vstav3:postActions> <vstav3:postAction> <vstav3:entryPoint class="PostDeploymentAction.PostDeploymentActionSample"> <assemblyIdentity name="PostDeploymentAction" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:postActionData> </vstav3:postActionData> </vstav3:postAction> </vstav3:postActions>  
```  
  
## См. также  
 [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md)   
 [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)  
  
  