---
title: '&lt;Описание&gt; элемент (Разработка решений Office в Visual Studio)'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- description element
- <description> element
- application manifests [Office development in Visual Studio], <description> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9fcdac1e950d98394b5703322f40dd1823b246f6
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2018
ms.locfileid: "34265119"
---
# <a name="ltdescriptiongt-element-office-development-in-visual-studio"></a>&lt;Описание&gt; элемент (Разработка решений Office в Visual Studio)
  Элемент `description` пространства имен `vstov4` хранит описание решения Office, которое отображается в диалоговом окне надстроек COM приложений Microsoft Office.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
<description>  
</description>  
```  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 Необязательный. Элемент `description` находится в пространстве имен `vstov4` . Он содержит описание надстройки, которая отображается в диалоговом окне надстроек COM в приложении Microsoft Office.  
  
 У элемента `description` нет атрибутов и дочерних элементов.  
  
## <a name="vsto-add-in-example"></a>Примеры надстройки VSTO  
  
### <a name="description"></a>Описание  
 В приведенном ниже примере кода показан элемент `description` для решения уровня приложения, которое развертывается с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Данный пример кода является частью большего примера, приведенного в [манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Код  
  
```xml  
<vstov4:description>  
  ContosoOutlookAddIn - Outlook add-in   
  created with Visual Studio Tools for Office  
</vstov4:description>  
```  
  
## <a name="see-also"></a>См. также  
 [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md)   
 [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Манифест приложения ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  