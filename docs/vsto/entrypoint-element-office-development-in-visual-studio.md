---
title: '&lt;entryPoint&gt; элемент (Разработка решений Office в Visual Studio)'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <entryPoint> element
- <entryPoint> element
- entryPoint element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6eb617b44eb5360ea8c313431c7d8609505efa16
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/22/2018
---
# <a name="ltentrypointgt-element-office-development-in-visual-studio"></a>&lt;entryPoint&gt; элемент (Разработка решений Office в Visual Studio)
  Каждый элемент `entryPoint` пространства имен `vstav3` идентифицирует сборку настройки, которая должна запускаться при установке этого приложения [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] .  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
<entryPoint class>  
    <assemblyIdentity />  
</entryPoint>  
```  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 Элемент `entryPoint` является обязательным и находится в пространстве имен `vstav3` .  
  
 Каждый элемент `entryPoint` может содержать только одну сборку настройки. Может существовать несколько элементов `entryPoint` , определенных в манифесте приложения.  
  
 Элемент `entryPoint` имеет перечисленные ниже атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`class`|Обязательно. Идентифицирует сборку настройки для выполнения. Синтаксис для этого атрибута: *ИмяПространстваИмен.ИмяКласса*.|  
  
 Объект`entryPoint` имеет следующий элемент.  
  
### <a name="assemblyidentity"></a>assemblyIdentity  
 Обязательно. Элемент `assemblyIdentity` в пространстве имен `vstav3` ссылается на существующий элемент `assemblyIdentity` в манифесте приложения [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] .  
  
 Роль `assemblyIdentity` и его атрибутов, определенных в [ &#60;assemblyIdentity&#62; элемент &#40;приложение ClickOnce&#41;](/visualstudio/deployment/assemblyidentity-element-clickonce-application).  
  
## <a name="document-level-customization-example"></a>Пример настройки на уровне документа  
  
### <a name="description"></a>Описание  
 В приведенном ниже примере кода показан элемент `entryPoint` в манифесте приложения для решения Office уровня документа, которое развертывается с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Данный пример кода является частью большего примера, приведенного в [манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Код  
  
```xml  
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
```  
  
## <a name="vsto-add-in-example"></a>Примеры надстройки VSTO  
  
### <a name="description"></a>Описание  
 В приведенном ниже примере кода показан элемент `entryPoint` в манифесте приложения для решения Office уровня приложения, которое развертывается с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Данный пример кода является частью большего примера, приведенного в [манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Код  
  
```xml
<vstav3:entryPoint   
  class="ContosoOutlookAddIn.ThisAddIn">  
  <assemblyIdentity   
    name="ContosoOutlookAddIn"   
    version="1.0.0.0"   
    language="neutral"   
    processorArchitecture="msil" />  
</vstav3:entryPoint>  
```  
  
## <a name="see-also"></a>См. также  
 [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md)   
 [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Манифест приложения ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  