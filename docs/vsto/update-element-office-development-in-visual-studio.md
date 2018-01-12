---
title: "&lt;Обновить&gt; элемент (Разработка решений Office в Visual Studio) | Документы Microsoft"
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
- update element
- <update> element
- application manifests [Office development in Visual Studio], <update> element
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 72caa5e93b311430f4416946b6ec0bdc9fda5031
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="ltupdategt-element-office-development-in-visual-studio"></a>&lt;Обновить&gt; элемент (Разработка решений Office в Visual Studio)
  `update` Элемент указывает интервал, когда решение будет выполнять проверку обновлений.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<update  
  enabled>  
  <expiration  
    maximumAge  
    unit  
  />  
</update>  
```  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 Элемент `update` обязателен и находится в пространстве имен `vstav3`.  
  
 `update` Элемент имеет следующие атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`enabled`|Обязательно. Установите параметр enabled в одно из следующих значений:<br /><br /> -   **значение true,** для проверки наличия обновлений.<br />-   **false** Чтобы отключить проверку обновлений.|  
  
 `update` Элемент имеет следующие дочерние элементы.  
  
### <a name="expiration"></a>истечение срока действия  
 Элемент `expiration` обязателен и находится в пространстве имен `vstav3`. Этот элемент указывает периодичность, с которой решение проверяет наличие обновлений.  
  
 `expiration` Элемент имеет следующие атрибуты.  
  
|Атрибут|Описание:|  
|---------------|-----------------|  
|`maximumAge`|-Обязательно. Значение этого атрибута в целое число.|  
|`unit`|Обязательно. Задать `unit` одно из следующих значений:<br /><br /> -   **часы**<br />-   **дни**<br />-   **недель**|  
  
## <a name="example-of-always-checking-for-updates"></a>Пример всегда проверка наличия обновлений  
  
### <a name="description"></a>Описание:  
 В следующем примере кода показан `update` элемент, который имеет значение всегда проверять наличие обновлений в решениях Office.  
  
### <a name="code"></a>Код  
  
```  
<vstav3:update enabled="true" />  
```  
  
## <a name="example-of-setting-a-default-update-interval"></a>Пример настройки по умолчанию интервал обновления  
  
### <a name="description"></a>Описание:  
 В следующем примере кода показан `update` элемента в манифесте приложения для решений Office. Этот пример кода является частью большего примера, приведенного в разделе [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Код  
  
```  
<vstav3:update enabled="true">  
    <vstav3:expiration maximumAge="7" unit="days" />  
</vstav3:update>  
```  
  
## <a name="see-also"></a>См. также  
 [Развертывание решения Office с помощью ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Манифест приложения ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  