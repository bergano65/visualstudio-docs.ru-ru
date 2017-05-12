---
title: "Элемент &lt;entryPointsCollection&gt; (разработка решений Office в Visual Studio)"
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
  - "элемент <entryPointsCollection>"
  - "манифесты приложения [разработка решений Office в Visual Studio], элемент <entryPointsCollection>"
  - "entryPointsCollection - элемент"
ms.assetid: da386d67-e45f-467c-a9ba-9b8451b520eb
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# Элемент &lt;entryPointsCollection&gt; (разработка решений Office в Visual Studio)
  Элемент `entryPointsCollection` пространства имен `vstav3`  содержит все элементы `entryPoints`, связанные с решениями Office.  
  
## Синтаксис  
  
```  
<entryPointsCollection>  
  <entryPoints>  
    <entryPoint>  
    </entryPoint>  
    <entryPoint>  
    </entryPoint>  
    <entryPoint>  
    </entryPoint>  
  </entryPoints>  
</entryPointsCollection>  
```  
  
## Элементы и атрибуты  
 Элемент `entryPointsCollection` является обязательным и находится в пространстве имен `vstav3`. Дочерние элементы также необходимо включить в это пространство имен. В манифесте приложения определен только один элемент `entryPointsCollection`.  
  
 У элемента `entryPointsCollection` нет атрибутов.  
  
 У элемента `entryPointsCollection` имеются перечисленные ниже элементы.  
  
### entryPoints  
 Обязательный. Роль элемента `entryPoints` в пространстве имен `vstav3`  определена в разделе [элемент &#60;entryPoints&#62; &#40;разработка решений Office в Visual Studio&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md).  
  
## Пример настройки на уровне документа  
  
### Описание  
 В приведенном ниже примере кода показан элемент `entryPointsCollection` в манифесте приложения для решения на уровне документа, которое развертывается с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Этот пример кода является частью большего примера, приведенного в разделе [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Код  
  
```  
<vstav3:entryPointsCollection> <vstav3:entryPoints> <vstav3:entryPoint class="ContosoExcelWorkbook.ThisWorkbook"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet1"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet2"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet3"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> </vstav3:entryPoints> </vstav3:entryPointsCollection>  
```  
  
## Примеры надстройки VSTO  
  
### Описание  
 В приведенном ниже примере кода показан элемент `entryPointsCollection` манифеста приложения для решения на уровне приложения, которое развертывается с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Этот пример кода является частью большего примера, приведенного в разделе [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Код  
  
```  
<vstav3:entryPointsCollection> <vstav3:entryPoints> <vstav3:entryPoint class="ContosoOutlookAddIn.ThisAddIn"> <assemblyIdentity name="ContosoOutlookAddIn" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> </vstav3:entryPoints> </vstav3:entryPointsCollection>  
```  
  
## Пример развертывания нескольких проектов  
  
### Описание  
 В приведенном ниже примере кода показан элемент `entryPointsCollection` манифеста приложения для многопроектного развертывания двух решений Office. Этот пример кода является частью большего примера, приведенного в разделе [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Код  
  
```  
<vstav3:entryPointsCollection> <vstav3:entryPoints id="ContosoExcel"> <vstav3:entryPoint class="ContosoExcelWorkbook.ThisWorkbook"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet1"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet2"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet3"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> </vstav3:entryPoints> <vstav3:entryPoints id="ContosoOutlook"> <vstav3:entryPoint class="ContosoOutlookAddIn.ThisAddIn"> <assemblyIdentity name="ContosoOutlookAddIn" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> </vstav3:entryPoints> </vstav3:entryPointsCollection>  
```  
  
## См. также  
 [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md)   
 [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)  
  
  