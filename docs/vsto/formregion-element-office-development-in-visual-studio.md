---
title: "&lt;formRegion&gt; элемент (Разработка решений Office в Visual Studio) | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: application manifests [Office development in Visual Studio], <formRegion> element
ms.assetid: d397cf31-c0ef-47f0-860a-cd816e4bf6eb
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: bc425459cee4b4398ead78939283ab4db6efc134
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
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
  
  