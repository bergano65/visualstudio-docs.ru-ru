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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0880e0ddf4763cf2c67c10871992a24b76f59ef2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53896647"
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