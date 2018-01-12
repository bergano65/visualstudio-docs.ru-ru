---
title: "&lt;документ&gt; элемент (Разработка решений Office в Visual Studio) | Документы Microsoft"
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
helpviewer_keywords:
- document element
- application manifests [Office development in Visual Studio], <document> element
- <document> element
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 38b03c2a4980891d9a6841b24365db32ee555de4
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="ltdocumentgt-element-office-development-in-visual-studio"></a>&lt;документ&gt; элемент (Разработка решений Office в Visual Studio)
  `document` Элемент `vstov4` имен хранит сведения о для настроек на уровне документа.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<document solutionId />  
```  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 Является обязательным только для настроек на уровне документа. `document` Элемент находится в `vstov4` пространства имен. `document` Элемент имеет следующие атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`solutionId`|Обязательно. Идентификатор GUID, используемый средой Visual Studio Tools для Office runtime для уникальной идентификации решения на уровне документа. Это значение хранится в виде _AssemblyLocation пользовательского свойства документа. Для получения дополнительной информации см. [Custom Document Properties Overview](../vsto/custom-document-properties-overview.md).|  
  
 `document`не имеет дочерних элементов.  
  
## <a name="document-level-customization-example"></a>Пример настройки на уровне документа  
  
### <a name="description"></a>Описание:  
 В следующем примере кода показан `document` элемент в решении Office уровня документа, развернутом с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Этот пример кода является частью большего примера, приведенного в разделе [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Код  
  
```  
<vstov4:document   
  solutionId="73e" />  
```  
  
## <a name="see-also"></a>См. также  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Манифест приложения ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  