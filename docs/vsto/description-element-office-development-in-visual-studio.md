---
title: '&lt;Описание&gt; элемент (Разработка решений Office в Visual Studio)'
titleSuffix: ''
ms.custom: secdec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- description element
- <description> element
- application manifests [Office development in Visual Studio], <description> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ede5ac920c1d40402504544a13f8a00905b82e80
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2019
ms.locfileid: "54871329"
---
# <a name="ltdescriptiongt-element-office-development-in-visual-studio"></a>&lt;Описание&gt; элемент (Разработка решений Office в Visual Studio)
  Элемент `description` пространства имен `vstov4` хранит описание решения Office, которое отображается в диалоговом окне надстроек COM приложений Microsoft Office.

## <a name="syntax"></a>Синтаксис

```xml
<description>
</description>
```

## <a name="elements-and-attributes"></a>Элементы и атрибуты
 Необязательный параметр. Элемент `description` находится в пространстве имен `vstov4` . Он содержит описание надстройки, которая отображается в диалоговом окне надстроек COM в приложении Microsoft Office.

 У элемента `description` нет атрибутов и дочерних элементов.

## <a name="vsto-add-in-example"></a>Пример надстройки VSTO

### <a name="description"></a>Описание
 В приведенном ниже примере кода показан элемент `description` для решения уровня приложения, которое развертывается с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Данный пример кода является частью большего примера, приведенного в [манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Код

```xml
<vstov4:description>
  ContosoOutlookAddIn - Outlook add-in
  created with Visual Studio Tools for Office
</vstov4:description>
```

## <a name="see-also"></a>См. также

- [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md)
- [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)