---
title: '&lt;entryPoints&gt; элемент (Разработка решений Office в Visual Studio)'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <entryPoints> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: bec51fd4d9e6a140d274f028a0e0286a161ac147
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/22/2018
---
# <a name="ltentrypointsgt-element-office-development-in-visual-studio"></a>&lt;entryPoints&gt; элемент (Разработка решений Office в Visual Studio)
  Элемент `entryPoints` пространства имен `vstav3` содержит все элементы `entryPoint` , связанные с решением Office.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
<entryPoints>  
    <entryPoint>  
    </entryPoint>  
    <entryPoint>  
    </entryPoint>  
    <entryPoint>  
    </entryPoint>  
</entryPoints>  
```  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 Элемент `entryPoints` является обязательным и находится в пространстве имен `vstav3` . В манифесте приложения определяется один элемент `entryPoints` для каждого решения Office. Например, при развертывании трех решений Office в многопроектном развертывании в манифесте приложения будет существовать три элемента `entryPoints` .  
  
 Элемент `entryPoints` имеет указанный ниже атрибут.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|id|Требуется для многопроектного развертывания. Имя решения Office. Идентификатор не может содержать знак равенства (=).|  
  
 У элемента`entryPoints` имеются перечисленные ниже элементы.  
  
### <a name="entrypoint"></a>entryPoint  
 Обязательно. Роль `entryPoint` элемент в `vstav3` пространство имен определяется в [ &#60;entryPoint&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/entrypoint-element-office-development-in-visual-studio.md).  
  
## <a name="document-level-customization-example"></a>Пример настройки на уровне документа  
  
### <a name="description"></a>Описание  
 В приведенном ниже примере кода показан элемент `entryPoints` в манифесте приложения для решения на уровне документа, которое развертывается с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Данный пример кода является частью большего примера, приведенного в [манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Код  
  
```xml  
<vstav3:entryPoints>  
  <vstav3:entryPoint   
    class="ContosoExcelWorkbook.ThisWorkbook">  
    <assemblyIdentity   
      name="ContosoExcelWorkbook"   
      version="1.0.0.0"   
      language="neutral"   
      processorArchitecture="msil" />  
  </vstav3:entryPoint>  
  <vstav3:entryPoint   
    class="ContosoExcelWorkbook.Sheet1">  
    <assemblyIdentity   
      name="ContosoExcelWorkbook"   
      version="1.0.0.0"   
      language="neutral"   
      processorArchitecture="msil" />  
  </vstav3:entryPoint>  
  <vstav3:entryPoint   
    class="ContosoExcelWorkbook.Sheet2">  
    <assemblyIdentity   
      name="ContosoExcelWorkbook"   
      version="1.0.0.0"   
      language="neutral"   
      processorArchitecture="msil" />  
  </vstav3:entryPoint>  
  <vstav3:entryPoint   
    class="ContosoExcelWorkbook.Sheet3">  
    <assemblyIdentity   
      name="ContosoExcelWorkbook"   
      version="1.0.0.0"   
      language="neutral"   
      processorArchitecture="msil" />  
  </vstav3:entryPoint>  
</vstav3:entryPoints>  
```  
  
## <a name="vsto-add-in-example"></a>Примеры надстройки VSTO  
  
### <a name="description"></a>Описание  
 В приведенном ниже примере кода показан элемент `entryPoints` манифеста приложения для решения на уровне приложения, которое развертывается с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Данный пример кода является частью большего примера, приведенного в [манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Код  
  
```xml  
<vstav3:entryPoints>  
  <vstav3:entryPoint   
    class="ContosoOutlookAddIn.ThisAddIn">  
    <assemblyIdentity   
      name="ContosoOutlookAddIn"   
      version="1.0.0.0"   
      language="neutral"   
      processorArchitecture="msil" />  
  </vstav3:entryPoint>  
</vstav3:entryPoints>  
```  
  
## <a name="multi-project-deployment-example"></a>Пример развертывания нескольких проектов  
  
### <a name="description"></a>Описание  
 В приведенном ниже примере кода показан элемент `entryPoints` в манифесте приложения для многопроектного развертывания. Данный пример кода является частью большего примера, приведенного в [манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Код  
  
```xml  
<vstav3:entryPoints   
  id="ContosoExcel">  
  <vstav3:entryPoint   
    class="ContosoExcelWorkbook.ThisWorkbook">  
    <assemblyIdentity   
      name="ContosoExcelWorkbook"   
      version="1.0.0.0"   
      language="neutral"   
      processorArchitecture="msil" />  
  </vstav3:entryPoint>  
  <vstav3:entryPoint   
    class="ContosoExcelWorkbook.Sheet1">  
    <assemblyIdentity   
      name="ContosoExcelWorkbook"   
      version="1.0.0.0"   
      language="neutral"   
      processorArchitecture="msil" />  
  </vstav3:entryPoint>  
  <vstav3:entryPoint   
    class="ContosoExcelWorkbook.Sheet2">  
    <assemblyIdentity   
      name="ContosoExcelWorkbook"   
      version="1.0.0.0"   
      language="neutral"   
      processorArchitecture="msil" />  
  </vstav3:entryPoint>  
  <vstav3:entryPoint   
    class="ContosoExcelWorkbook.Sheet3">  
    <assemblyIdentity   
      name="ContosoExcelWorkbook"   
      version="1.0.0.0"   
      language="neutral"   
      processorArchitecture="msil" />  
  </vstav3:entryPoint>  
</vstav3:entryPoints>  
<vstav3:entryPoints   
  id="ContosoOutlook">  
  <vstav3:entryPoint   
    class="ContosoOutlookAddIn.ThisAddIn">  
    <assemblyIdentity   
      name="ContosoOutlookAddIn"   
      version="1.0.0.0"   
      language="neutral"   
      processorArchitecture="msil" />  
  </vstav3:entryPoint>  
</vstav3:entryPoints>  
```  
  
## <a name="see-also"></a>См. также  
 [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md)   
 [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Манифест приложения ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  