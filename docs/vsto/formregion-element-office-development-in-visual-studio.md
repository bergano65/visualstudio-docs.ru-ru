---
title: '&lt;formRegion&gt; элемент (Разработка решений Office в Visual Studio) | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <formRegion> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: af7dd4f3472692def9f05a937297d54d13c6f0d6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ltformregiongt-element-office-development-in-visual-studio"></a>&lt;formRegion&gt; элемент (Разработка решений Office в Visual Studio)
  Элемент `formRegion` пространства имен `vstov4` определяет область формы Microsoft Office Outlook, связанную с надстройкой VSTO.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<formRegion  
  name>  
  <messageClass  
    name/>  
</formRegion>  
```  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 Элемент `formRegion` пространства имен `vstov4` определяет область формы, связанную с надстройкой VSTO для Outlook. Этот элемент является обязательным только для надстроек VSTO для Outlook, в которых есть области форм.  
  
 Для одной и той же надстройки VSTO можно определить несколько элементов `formRegion` в рамках элемента `formRegions` .  
  
 Элемент `formRegion` имеет перечисленные ниже атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`name`|Обязательно. Определяет имя области формы.|  
  
 Элемент `formRegion` имеет указанные ниже дочерние элементы.  
  
### <a name="messageclass"></a>messageClass  
 Элемент `messageClass` определяет форму Outlook, которая связана с областью формы.  
  
 Элемент `messageClass` имеет перечисленные ниже атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`name`|Обязательно. Определяет форму, которая связана с областью формы.|  
  
## <a name="example"></a>Пример  
 В приведенном ниже примере кода показан элемент `formRegion` манифеста приложения для надстройки VSTO для Outlook, развертываемой с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Имеется три класса сообщений, связанных с одной и той же областью формы. Этот пример кода является частью большего примера, приведенного в разделе [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
```  
<vstov4:formRegion  
    name="OutlookAddIn1.FormRegion1">  
  <vstov4:messageClass name="IPM.Note" />  
  <vstov4:messageClass name="IPM.Contact" />  
  <vstov4:messageClass name="IPM.Appointment" />  
</vstov4:formRegion>  
```  
  
## <a name="see-also"></a>См. также  
 [Создание областей форм Outlook](../vsto/creating-outlook-form-regions.md)   
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Манифест приложения ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  