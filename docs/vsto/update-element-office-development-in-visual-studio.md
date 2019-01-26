---
title: '&lt;Обновить&gt; элемент (Разработка решений Office в Visual Studio)'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- update element
- <update> element
- application manifests [Office development in Visual Studio], <update> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 461fae79e3af346d64017166b6dae3ace67599e1
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2019
ms.locfileid: "54867394"
---
# <a name="ltupdategt-element-office-development-in-visual-studio"></a>&lt;Обновить&gt; элемент (Разработка решений Office в Visual Studio)
  `update` Элемент указывает интервал, с которым решение будет проверять наличие обновлений.

## <a name="syntax"></a>Синтаксис

```xml
<update
  enabled>
  <expiration
    maximumAge
    unit
  />
</update>
```

## <a name="elements-and-attributes"></a>Элементы и атрибуты
 Элемент `update` является обязательным и находится в пространстве имен `vstav3` .

 Элемент `update` имеет перечисленные ниже атрибуты.

|Атрибут|Описание|
|---------------|-----------------|
|`enabled`|Обязательный. Установите, включен один из следующих значений:<br /><br /> -   **значение true,** для проверки наличия обновлений.<br />-   **false** во избежание проверки наличия обновлений.|

 Элемент `update` имеет указанные ниже дочерние элементы.

### <a name="expiration"></a>expiration
 Элемент `expiration` является обязательным и находится в пространстве имен `vstav3` . Этот элемент задает интервал, с которой решение проверяет наличие обновлений.

 Элемент `expiration` имеет перечисленные ниже атрибуты.

|Атрибут|Описание|
|---------------|-----------------|
|`maximumAge`| Обязательный. Значение этого атрибута в целое число.|
|`unit`|Обязательный. Задайте `unit` к одному из следующих значений:<br /><br /> -   **часы**<br />-   **дней**<br />-   **Недель**|

## <a name="example-of-always-checking-for-updates"></a>Пример всегда проверки на наличие обновлений

### <a name="description"></a>Описание:
 В следующем примере кода показано `update` элемент, который имеет значение всегда проверять наличие обновлений в решениях Office.

### <a name="code"></a>Код

```xml
<vstav3:update enabled="true" />
```

## <a name="example-of-setting-a-default-update-interval"></a>Пример настройки по умолчанию интервал обновления

### <a name="description"></a>Описание:
 В следующем примере кода показано `update` элемента в манифесте приложения для решений Office. Данный пример кода является частью большего примера, приведенного в [манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Код

```xml
<vstav3:update enabled="true">
    <vstav3:expiration maximumAge="7" unit="days" />
</vstav3:update>
```

## <a name="see-also"></a>См. также

- [Развертывание решения Office с помощью ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md)
- [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)
