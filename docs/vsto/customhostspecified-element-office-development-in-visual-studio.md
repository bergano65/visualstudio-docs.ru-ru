---
title: "&lt;customHostSpecified&gt; элемент (Разработка решений Office в Visual Studio) | Документы Microsoft"
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
- application manifests [Office development in Visual Studio], <customHostSpecified> element
- <customHostSpecified> element
- customHostSpecified element
ms.assetid: 2212b7eb-bf94-4398-b9ea-0ab00203203b
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c7ad3bb1e62e2ea98f5afe1de5cc9eb49f711234
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ltcustomhostspecifiedgt-element-office-development-in-visual-studio"></a>&lt;customHostSpecified&gt; элемент (Разработка решений Office в Visual Studio)
  `customHostSpecified` Элемент указывает, что это решение не является автономным приложением. Решения Office содержат компоненты, которые размещены в приложениях Microsoft Office.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<customHostSpecified />  
```  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 `customHostSpecified` Элемент является обязательным для решений Office. Этот элемент имеет `co.v1` пространства имен и указывает, что это развертывание содержит компонент, который будет развернут в настраиваемом узле и не является автономным приложением.  
  
 Этот элемент является дочерним элементом первого `<entrypoint>` элемента в манифесте приложения. Могут быть другие дочерние элементы в том, что `<entrypoint>` элемент или [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] будет вызывать ошибку проверки во время установки.  
  
 Этот элемент не имеет атрибутов и дочерних элементов.  
  
## <a name="example"></a>Пример  
 В следующем примере кода показан `customHostSpecified` элемента в манифесте приложения для решения Office. Этот пример кода является частью большего примера, приведенного в разделе [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
```  
<entryPoint>  
    <co.v1:customHostSpecified />  
</entryPoint>  
```  
  
## <a name="see-also"></a>См. также  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Манифест приложения ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  