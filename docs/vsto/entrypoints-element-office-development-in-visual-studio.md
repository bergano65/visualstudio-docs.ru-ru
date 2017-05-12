---
title: "элемент &lt;entryPoints&gt; (разработка решений Office в Visual Studio)"
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
  - "манифесты приложения [разработка решений Office в Visual Studio], элемент <entryPoints>"
ms.assetid: 991d7cbf-85e5-4307-a470-076b2f74d859
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# элемент &lt;entryPoints&gt; (разработка решений Office в Visual Studio)
  Элемент `entryPoints` пространства имен `vstav3`  содержит все элементы `entryPoint`, связанные с решением Office.  
  
## Синтаксис  
  
```  
<entryPoints>  
    <entryPoint>  
    </entryPoint>  
    <entryPoint>  
    </entryPoint>  
    <entryPoint>  
    </entryPoint>  
</entryPoints>  
```  
  
## Элементы и атрибуты  
 Элемент `entryPoints` является обязательным и находится в пространстве имен `vstav3` . В манифесте приложения определяется один элемент `entryPoints` для каждого решения Office. Например, при развертывании трех решений Office в многопроектном развертывании в манифесте приложения будет существовать три элемента `entryPoints`.  
  
 Элемент `entryPoints` имеет указанный ниже атрибут.  
  
|Атрибут|Описание|  
|-------------|--------------|  
|id|Требуется для многопроектного развертывания. Имя решения Office. Идентификатор не может содержать знак равенства \(\=\).|  
  
 У элемента `entryPoints` имеются перечисленные ниже элементы.  
  
### entryPoint  
 Обязательный. Роль элемента `entryPoint` в пространстве имен `vstav3`  определена в разделе [элемент &#60;entryPoint&#62; &#40;разработка решений Office в Visual Studio&#41;](../vsto/entrypoint-element-office-development-in-visual-studio.md).  
  
## Пример настройки на уровне документа  
  
### Описание  
 В приведенном ниже примере кода показан элемент `entryPoints` в манифесте приложения для решения на уровне документа, которое развертывается с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Этот пример кода является частью большего примера, приведенного в разделе [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Код  
  
```  
<vstav3:entryPoints> <vstav3:entryPoint class="ContosoExcelWorkbook.ThisWorkbook"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet1"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet2"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet3"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> </vstav3:entryPoints>  
```  
  
## Примеры надстройки VSTO  
  
### Описание  
 В приведенном ниже примере кода показан элемент `entryPoints` манифеста приложения для решения на уровне приложения, которое развертывается с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Этот пример кода является частью большего примера, приведенного в разделе [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Код  
  
```  
<vstav3:entryPoints> <vstav3:entryPoint class="ContosoOutlookAddIn.ThisAddIn"> <assemblyIdentity name="ContosoOutlookAddIn" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> </vstav3:entryPoints>  
```  
  
## Пример развертывания нескольких проектов  
  
### Описание  
 В приведенном ниже примере кода показан элемент `entryPoints` в манифесте приложения для многопроектного развертывания. Этот пример кода является частью большего примера, приведенного в разделе [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Код  
  
```  
<vstav3:entryPoints id="ContosoExcel"> <vstav3:entryPoint class="ContosoExcelWorkbook.ThisWorkbook"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet1"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet2"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet3"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> </vstav3:entryPoints> <vstav3:entryPoints id="ContosoOutlook"> <vstav3:entryPoint class="ContosoOutlookAddIn.ThisAddIn"> <assemblyIdentity name="ContosoOutlookAddIn" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> </vstav3:entryPoints>  
```  
  
## См. также  
 [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md)   
 [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)  
  
  