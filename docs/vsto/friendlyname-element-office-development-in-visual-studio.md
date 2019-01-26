---
title: '&lt;friendlyName&gt; элемент (Разработка решений Office в Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <friendlyName> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d038e825173f95ddfe4106022c7c9924090b3a5f
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2019
ms.locfileid: "54873110"
---
# <a name="ltfriendlynamegt-element-office-development-in-visual-studio"></a>&lt;friendlyName&gt; элемент (Разработка решений Office в Visual Studio)
  Элемент `friendlyName` пространства имен `vstov4` хранит имя, которое отображается в списке установленных программ.

## <a name="syntax"></a>Синтаксис

```xml
<friendlyName>
</friendlyName>
```

## <a name="elements-and-attributes"></a>Элементы и атрибуты
 Элемент `friendlyName` находится в пространстве имен `vstov4` . Значение отображается в списке программ, установленных на компьютере, и в диалоговом окне "Надстройки COM VSTO" приложений Microsoft Office.

 У элемента `friendlyName` нет атрибутов и дочерних элементов.

## <a name="vsto-add-in-example"></a>Пример надстройки VSTO

### <a name="description"></a>Описание:
 В приведенном ниже примере кода показан элемент `friendlyName` в решении на уровне приложения, которое развертывается с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Данный пример кода является частью большего примера, приведенного в [манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Код

```xml
<vstov4:friendlyName>
  ContosoOutlookAddIn
</vstov4:friendlyName>
```

## <a name="see-also"></a>См. также

- [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md)
- [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)