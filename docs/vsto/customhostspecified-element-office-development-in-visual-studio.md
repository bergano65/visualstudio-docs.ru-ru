---
title: '&lt;customHostSpecified&gt; элемент (Разработка решений Office в Visual Studio)'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <customHostSpecified> element
- <customHostSpecified> element
- customHostSpecified element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d4eaf874a259251c35a6b01c08f544993092ff4d
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2018
ms.locfileid: "34264039"
---
# <a name="ltcustomhostspecifiedgt-element-office-development-in-visual-studio"></a>&lt;customHostSpecified&gt; элемент (Разработка решений Office в Visual Studio)
  `customHostSpecified` Элемент указывает, что это решение не является автономным приложением. Решения Office содержат компоненты, которые размещены в приложениях Microsoft Office.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml
<customHostSpecified />  
```  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 `customHostSpecified` Элемент является обязательным для решений Office. Этот элемент имеет `co.v1` пространства имен и указывает, что это развертывание содержит компонент, который будет развернут в настраиваемом узле и не является автономным приложением.  
  
 Этот элемент является дочерним элементом первого `<entrypoint>` элемента в манифесте приложения. Могут быть другие дочерние элементы в том, что `<entrypoint>` элемент или [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] будет вызывать ошибку проверки во время установки.  
  
 Этот элемент не имеет атрибутов и дочерних элементов.  
  
## <a name="example"></a>Пример  
 В следующем примере кода показан `customHostSpecified` элемента в манифесте приложения для решения Office. Данный пример кода является частью большего примера, приведенного в [манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).  
  
```xml
<entryPoint>  
    <co.v1:customHostSpecified />  
</entryPoint>  
```  
  
## <a name="see-also"></a>См. также  
 [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md)   
 [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Манифест приложения ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  