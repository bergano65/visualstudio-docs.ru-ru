---
title: '&lt;Настройка&gt; элемент (Разработка решений Office в Visual Studio) | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <customization> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4384dd8bea4fc5829362ccdb06ea3912607cd263
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ltcustomizationgt-element-office-development-in-visual-studio"></a>&lt;Настройка&gt; элемент (Разработка решений Office в Visual Studio)
  Элемент `customization` пространства имен `vstov4` описывает конкретное решение Office. Дочерние элементы настроек уровня документа и надстроек VSTO отличаются друг от друга.  
  
## <a name="syntax-for-document-level-customizations"></a>Синтаксис настроек уровня документа  
  
```  
<customization  
  id  
  <document  
    solutionId  
  />  
</customization>  
```  
  
## <a name="syntax-for-vsto-add-ins"></a>Синтаксис надстроек VSTO  
  
```  
<customization  
  id  
  <appAddin  
    application  
    loadBehavior  
    keyName>  
  <friendlyName></friendlyName>  
  <description></description>  
  <formRegions></formRegions>  
</customization>  
```  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 Элемент `customization` содержит сведения о настройках. Этот элемент должен принадлежать следующему пространству имен: `vstov4=urn:schemas-microsoft-com:vsto.v4`. Существует по одному элементу `customization` для каждого решения Office. Например, при развертывании трех решений Office в многопроектном развертывании в манифесте приложения будет существовать три элемента `customization` .  
  
 Дочерние элементы сборки также должны быть в этом пространство имен.  
  
 Элемент `customization` имеет указанный ниже атрибут.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`id`|Требуется для многопроектного развертывания. Элемент `id` уникальным образом идентифицирует решение Office.|  
  
### <a name="document-level-customizations"></a>Настройки уровня документа  
 Элемент `customization` имеет указанный ниже дочерний элемент.  
  
#### <a name="document"></a>документ  
 `document` Элемент в `vstov4` пространство имен определяется в [ &#60;документа&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/document-element-office-development-in-visual-studio.md).  
  
### <a name="vsto-add-ins"></a>Надстройки VSTO  
 Элемент `customization` имеет указанный ниже дочерний элемент.  
  
#### <a name="appaddin"></a>appAddin  
 `appAddin` Элемент в `vstov4` пространство имен определяется в [ &#60;appAddin&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/appaddin-element-office-development-in-visual-studio.md).  
  
## <a name="example-of-a-document-level-customization"></a>Пример настройки на уровне документа  
  
### <a name="description"></a>Описание  
 В приведенном ниже примере кода показан элемент `customization` для настройки на уровне документа. Этот пример кода является частью большего примера, приведенного в разделе [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Код  
  
```  
<vstov4:customization>  
  <vstov4:document   
    solutionId="73e" />  
</vstov4:customization>  
```  
  
## <a name="example-of-an-vsto-add-in"></a>Пример надстройки VSTO  
  
### <a name="description"></a>Описание  
 В приведенном ниже примере кода показан элемент `customization` для надстройки VSTO. Это надстройка VSTO для Outlook, в которой используются области форм. Этот пример кода является частью большего примера, приведенного в разделе [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Код  
  
```  
<vstov4:customization>  
  <vstov4:appAddIn   
    application="Outlook"   
    loadBehavior="3"   
    keyName="ContosoOutlookAddIn">  
    <vstov4:friendlyName>  
      ContosoOutlookAddIn  
    </vstov4:friendlyName>  
    <vstov4:description>  
      ContosoOutlookAddIn - Outlook VSTO Add-in   
      created with Visual Studio Tools for Office  
    </vstov4:description>  
    <vstov4:formRegions>  
      <vstov4:formRegion  
          name="OutlookAddIn1.FormRegion1">  
        <vstov4:messageClass name="IPM.Note" />  
        <vstov4:messageClass name="IPM.Contact" />  
        <vstov4:messageClass name="IPM.Appointment" />  
      </vstov4:formRegion>  
    </vstov4:formRegions>  
  </vstov4:appAddIn>  
</vstov4:customization>  
```  
  
## <a name="see-also"></a>См. также  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Манифест приложения ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  