---
title: '&lt;&gt;элемент customHostSpecified (разработка решений Office в Visual Studio)'
description: Узнайте, как элемент customHostSpecified указывает, что это решение не является изолированным приложением.
titleSuffix: ''
ms.custom: seodec18, SEO-VS-2020
ms.date: 02/02/2017
ms.topic: reference
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
ms.openlocfilehash: e8327c6e154f051f5ce79d41ceaa696e330c794f
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2020
ms.locfileid: "96848135"
---
# <a name="ltcustomhostspecifiedgt-element-office-development-in-visual-studio"></a>&lt;&gt;элемент customHostSpecified (разработка решений Office в Visual Studio)
  `customHostSpecified`Элемент указывает, что это решение не является изолированным приложением. Решения Office содержат компоненты, размещенные в Microsoft Office приложениях.

## <a name="syntax"></a>Синтаксис

```xml
<customHostSpecified />
```

## <a name="elements-and-attributes"></a>Элементы и атрибуты
 `customHostSpecified`Элемент необходим для решений Office. Этот элемент находится в `co.v1` пространстве имен и указывает, что это развертывание содержит компонент, который будет развернут внутри пользовательского узла и не является изолированным приложением.

 Этот элемент является дочерним по отношению к первому `<entrypoint>` элементу в манифесте приложения. В этом элементе не может быть других дочерних элементов, `<entrypoint>` или [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] при установке возникнет ошибка проверки.

 Этот элемент не имеет атрибутов и не содержит дочерних элементов.

## <a name="example"></a>Пример
 В следующем примере кода показан `customHostSpecified` элемент в манифесте приложения для решения Office. Этот пример кода является частью большого примера, приведенного в разделе [манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).

```xml
<entryPoint>
    <co.v1:customHostSpecified />
</entryPoint>
```

## <a name="see-also"></a>См. также раздел

- [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md)
- [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)