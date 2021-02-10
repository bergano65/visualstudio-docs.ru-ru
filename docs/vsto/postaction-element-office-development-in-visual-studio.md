---
title: '&lt;&gt;элемент «действие» (разработка решений Office в Visual Studio)'
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <postAction> element
- <postAction> element
- postAction element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 0490e9423cb747782029eb0fd7254407adb3a607
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955766"
---
# <a name="ltpostactiongt-element-office-development-in-visual-studio"></a>&lt;&gt;элемент «действие» (разработка решений Office в Visual Studio)
  Элемент `postAction` пространства имен `vstav3` содержит элементы `entrypoint` и все элементы `postActionData` , связанные с действиями после развертывания, которые выполняются после установки решений Office.

## <a name="syntax"></a>Синтаксис

```xml
<postAction>
  <entryPoint>
  </entryPoint>
  <postActionData>
  </postActionData>
</postAction>
```

## <a name="elements-and-attributes"></a>Элементы и атрибуты
 Элемент `postAction` является необязательным и находится в пространстве имен `vstav3` . В манифесте приложения определяется один элемент `postAction` для каждого выполняемого после развертывания действия.

 У элемента `postAction` нет атрибутов.

 У элемента`postAction` имеются перечисленные ниже элементы.

### <a name="entrypoint"></a>entryPoint
 Необязательный элемент. Роль `entryPoint` элемента в `vstav3` пространстве имен определяется в [&#60;entrypoint&#62; элемент &#40;разработке решений Office в&#41;Visual Studio ](../vsto/entrypoints-element-office-development-in-visual-studio.md).

### <a name="postactiondata"></a>postActionData
 Необязательный элемент. Роль `postActionData` элемента в `vstav3` пространстве имен определяется в [&#60;постактиондата&#62; элемент &#40;разработке решений Office в&#41;Visual Studio ](../vsto/postactiondata-element-office-development-in-visual-studio.md).

## <a name="post-deployment-action-example"></a>Пример действия, выполняемого после развертывания

### <a name="description"></a>Описание
 В приведенном ниже примере кода показан элемент `postAction` манифеста приложения для решения Office, развертываемого с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Этот пример кода является частью большого примера, приведенного в разделе [манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Код

```xml
<vstav3:postAction>
  <vstav3:entryPoint
    class="PostDeploymentAction.PostDeploymentActionSample">
    <assemblyIdentity
      name="PostDeploymentAction"
      version="1.0.0.0"
      language="neutral"
      processorArchitecture="msil" />
  </vstav3:entryPoint>
  <vstav3:postActionData>
  </vstav3:postActionData>
</vstav3:postAction>
```

## <a name="see-also"></a>См. также

- [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md)
- [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)
