---
title: "&lt;Описание&gt; элемент (Разработка решений Office в Visual Studio) | Документы Microsoft"
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
- description element
- <description> element
- application manifests [Office development in Visual Studio], <description> element
ms.assetid: 27c90f8c-393d-4557-9371-2e4e3c4a2d95
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a4978233c9172dd07cc034cba7f0d0f76374f231
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ltdescriptiongt-element-office-development-in-visual-studio"></a>&lt;Описание&gt; элемент (Разработка решений Office в Visual Studio)
  Элемент `description` пространства имен `vstov4` хранит описание решения Office, которое отображается в диалоговом окне надстроек COM приложений Microsoft Office.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<description>  
</description>  
```  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 Необязательно. Элемент `description` находится в пространстве имен `vstov4` . Он содержит описание надстройки, которая отображается в диалоговом окне надстроек COM в приложении Microsoft Office.  
  
 У элемента `description` нет атрибутов и дочерних элементов.  
  
## <a name="vsto-add-in-example"></a>Примеры надстройки VSTO  
  
### <a name="description"></a>description  
 В приведенном ниже примере кода показан элемент `description` для решения уровня приложения, которое развертывается с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Этот пример кода является частью большего примера, приведенного в разделе [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Код  
  
```  
<vstov4:description>  
  ContosoOutlookAddIn - Outlook add-in   
  created with Visual Studio Tools for Office  
</vstov4:description>  
```  
  
## <a name="see-also"></a>См. также  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Манифест приложения ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  