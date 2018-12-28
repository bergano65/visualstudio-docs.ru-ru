---
title: '&lt;postActionData&gt; элемент (Разработка решений Office в Visual Studio)'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- <postActionData> element
- application manifests [Office development in Visual Studio], <postActionData> element
- postActionData element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 58b085e35971fa557d946f3967af4db81b577fff
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/27/2018
ms.locfileid: "53804829"
---
# <a name="ltpostactiondatagt-element-office-development-in-visual-studio"></a>&lt;postActionData&gt; элемент (Разработка решений Office в Visual Studio)
  Элемент `postActionData` пространства имен `vstav3` указывает данные, связанные с действиями, выполняемыми после развертывания при установке решений Office.

## <a name="syntax"></a>Синтаксис

```xml
<postActionData>
</postActionData>
```

## <a name="elements-and-attributes"></a>Элементы и атрибуты
 Элемент `postActionData` является необязательным и находится в пространстве имен `vstav3` . В манифесте приложения определяется один элемент `postActionData` для каждого выполняемого после развертывания действия.

 У элемента `postActions` нет атрибутов.

 У элемента`postActions` нет дочерних элементов.

## <a name="post-deployment-action-example"></a>Пример действия после развертывания

### <a name="description"></a>Описание:
 В приведенном ниже примере кода показан элемент `postAction` манифеста приложения для решения Office, развертываемого с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Данный пример кода является частью большего примера, приведенного в [манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Код

```xml
<vstav3:postActionData>
  data in any format
</vstav3:postActionData>
```

## <a name="see-also"></a>См. также

- [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md)
- [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)
