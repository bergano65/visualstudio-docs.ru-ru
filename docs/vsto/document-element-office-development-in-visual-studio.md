---
title: '&lt;документ&gt; элемент (Разработка решений Office в Visual Studio)'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document element
- application manifests [Office development in Visual Studio], <document> element
- <document> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 07d8172ec4e56352c2244aef02d947ac48833ab7
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/22/2018
ms.locfileid: "34447339"
---
# <a name="ltdocumentgt-element-office-development-in-visual-studio"></a>&lt;документ&gt; элемент (Разработка решений Office в Visual Studio)
  `document` Элемент `vstov4` имен хранит сведения о для настроек на уровне документа.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
<document solutionId />  
```  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 Является обязательным только для настроек на уровне документа. `document` Элемент находится в `vstov4` пространства имен. `document` Элемент имеет следующие атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`solutionId`|Обязательно. Идентификатор GUID, используемый средой Visual Studio Tools для Office runtime для уникальной идентификации решения на уровне документа. Это значение хранится в виде _AssemblyLocation пользовательского свойства документа. Дополнительные сведения см. в разделе [Общие сведения о свойствах пользовательского документа](../vsto/custom-document-properties-overview.md).|  
  
 `document` не имеет дочерних элементов.  
  
## <a name="document-level-customization-example"></a>Пример настройки на уровне документа  
  
### <a name="description"></a>Описание  
 В следующем примере кода показан `document` элемент в решении Office уровня документа, развернутом с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Данный пример кода является частью большего примера, приведенного в [манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Код  
  
```xml
<vstov4:document   
  solutionId="73e" />  
```  
  
## <a name="see-also"></a>См. также  
 [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md)   
 [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Манифест приложения ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  