---
title: '&lt;formRegions&gt; элемент (Разработка решений Office в Visual Studio) | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formRegions element
- <formRegions> element
- application manifests [Office development in Visual Studio], <formRegions> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c51b626c104d5342c00dbd45a2c565315c9c2225
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ltformregionsgt-element-office-development-in-visual-studio"></a>&lt;formRegions&gt; элемент (Разработка решений Office в Visual Studio)
  Элемент `formRegions` пространства имен `vstov4` содержит области формы Microsoft Office Outlook, связанные с надстройкой VSTO.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<formRegions>  
  <formRegion>  
  </formRegion>  
</formRegions>  
```  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 Элемент `formRegions` пространства имен `vstov4` содержит все элементы `formRegion` для надстройки VSTO для Outlook. Этот элемент является обязательным только для надстроек VSTO для Outlook, в которых есть области форм.  
  
 В манифесте приложения может быть определен только один элемент `formRegions` .  
  
 У элемента `formRegions` нет атрибутов.  
  
 Элемент `formRegions` имеет следующий элемент.  
  
### <a name="formregion"></a>formRegion  
 Является обязательным для надстроек VSTO для Outlook, включающих области форм. `formRegion` Элемент определен в [ &#60;formRegion&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/formregion-element-office-development-in-visual-studio.md).  
  
## <a name="vsto-add-in-example"></a>Примеры надстройки VSTO  
  
### <a name="description"></a>Описание  
 В приведенном ниже примере кода показан элемент `formRegions` в манифесте приложения для решения Office уровня приложения, которое развертывается с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Этот пример кода является частью большего примера, приведенного в разделе [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Код  
  
```  
<vstov4:formRegions>  
  <vstov4:formRegion  
      name="OutlookAddIn1.FormRegion1">  
    <vstov4:messageClass name="IPM.Note" />  
    <vstov4:messageClass name="IPM.Contact" />  
    <vstov4:messageClass name="IPM.Appointment" />  
  </vstov4:formRegion>  
</vstov4:formRegions>  
```  
  
## <a name="see-also"></a>См. также  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Манифест приложения ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  