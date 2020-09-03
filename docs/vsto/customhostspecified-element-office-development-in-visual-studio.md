---
title: '&lt;&gt;элемент customHostSpecified (разработка решений Office в Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
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
ms.openlocfilehash: 689848f14b4540a54489b4ea5bbad67e493fe276
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544915"
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

## <a name="see-also"></a>См. также

- [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md)
- [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)