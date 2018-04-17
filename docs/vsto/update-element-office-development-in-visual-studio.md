---
title: '&lt;Обновить&gt; элемент (Разработка решений Office в Visual Studio) | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- update element
- <update> element
- application manifests [Office development in Visual Studio], <update> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2f0e1fdc26e285ce9b6a1fd5ecc1aa638fe909b8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`maximumAge`|-Обязательно. Значение этого атрибута в целое число.|  
|`unit`|Обязательно. Задать `unit` одно из следующих значений:<br /><br /> -   **Часы**<br />-   **Дни**<br />-   **Недель**|  
  
## <a name="example-of-always-checking-for-updates"></a>Пример всегда проверка наличия обновлений  
  
### <a name="description"></a>Описание  
 В следующем примере кода показан `update` элемент, который имеет значение всегда проверять наличие обновлений в решениях Office.  
  
### <a name="code"></a>Код  
  
```  
<vstav3:update enabled="true" />  
```  
  
## <a name="example-of-setting-a-default-update-interval"></a>Пример настройки по умолчанию интервал обновления  
  
### <a name="description"></a>Описание  
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
  
  