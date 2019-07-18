---
title: '&lt;customHostSpecified&gt; элемент (Разработка решений Office в Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <customHostSpecified> element
- <customHostSpecified> element
- customHostSpecified element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 26597796c99d3ab8740812819cf3aa5568e2985b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62956183"
---
# <a name="ltcustomhostspecifiedgt-element-office-development-in-visual-studio"></a>&lt;customHostSpecified&gt; элемент (Разработка решений Office в Visual Studio)
  `customHostSpecified` Элемент указывает, что это решение не является автономным. Решения Office содержат компоненты, которые размещаются в приложениях Microsoft Office.

## <a name="syntax"></a>Синтаксис

```xml
<customHostSpecified />
```

## <a name="elements-and-attributes"></a>Элементы и атрибуты
 `customHostSpecified` Элемент является обязательным для решений Office. Этот элемент имеет `co.v1` пространства имен и указывает, что это развертывание содержит компонент, который будет развернут в настраиваемом узле, а не является автономным приложением.

 Этот элемент является потомком первого `<entrypoint>` в манифесте приложения. Может существовать нет других дочерних элементов, в который `<entrypoint>` элемент или [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] вызовут ошибки проверки во время установки.

 Этот элемент не имеет атрибутов и дочерних элементов.

## <a name="example"></a>Пример
 В следующем примере кода показано `customHostSpecified` элемента в манифесте приложения для решения Office. Данный пример кода является частью большего примера, приведенного в [манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).

```xml
<entryPoint>
    <co.v1:customHostSpecified />
</entryPoint>
```

## <a name="see-also"></a>См. также

- [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md)
- [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)