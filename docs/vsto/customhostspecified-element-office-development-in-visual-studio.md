---
title: "элемент &lt;customHostSpecified&gt; (разработка решений Office в Visual Studio) | Microsoft Docs"
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
  - "манифесты приложений [разработка решений Office в Visual Studio], элемент <customHostSpecified>"
  - "элемент <customHostSpecified>"
  - "customHostSpecified - элемент"
ms.assetid: 2212b7eb-bf94-4398-b9ea-0ab00203203b
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# элемент &lt;customHostSpecified&gt; (разработка решений Office в Visual Studio)
  Элемент `customHostSpecified` указывает, что данное решение не является автономным.  Некоторые компоненты решений Office размещаются внутри ведущих приложений Microsoft Office.  
  
## Синтаксис  
  
```  
<customHostSpecified />  
```  
  
## Элементы и атрибуты  
 Элемент `customHostSpecified` является обязательным для решений Office.  Этот элемент находится в пространстве имен `co.v1` и указывает, что данное развертывание не является автономным приложением и содержит компонент, который будет развернут в настраиваемом узле.  
  
 Данный элемент является дочерним элементом первого элемента `<entrypoint>` в манифесте приложения.  Других дочерних элементов у `<entrypoint>` быть не должно; в противном случае [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] сообщит об ошибке проверки во время установки.  
  
 У этого элемента нет атрибутов и дочерних элементов.  
  
## Пример  
 В следующем примере кода показан элемент `customHostSpecified` в манифесте приложения для решения office.  Данный пример кода является частью большего примера, приведенного в разделе [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).  
  
```  
<entryPoint>  
    <co.v1:customHostSpecified />  
</entryPoint>  
```  
  
## См. также  
 [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md)   
 [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)  
  
  