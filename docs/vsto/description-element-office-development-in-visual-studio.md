---
title: '&lt;&gt;элемент Description (разработка решений Office в Visual Studio)'
description: Сведения о том, что элемент Description пространства имен vstov4 хранит описание решения Office, которое отображается в диалоговом окне надстройки COM.
titleSuffix: ''
ms.custom: secdec18, SEO-VS-2020
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- description element
- <description> element
- application manifests [Office development in Visual Studio], <description> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9f065dd07e901ee0d59b39f1096cc351cd70bc02
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897601"
---
# <a name="ltdescriptiongt-element-office-development-in-visual-studio"></a>&lt;&gt;элемент Description (разработка решений Office в Visual Studio)
  Элемент `description` пространства имен `vstov4` хранит описание решения Office, которое отображается в диалоговом окне надстроек COM приложений Microsoft Office.

## <a name="syntax"></a>Синтаксис

```xml
<description>
</description>
```

## <a name="elements-and-attributes"></a>Элементы и атрибуты
 Необязательный элемент. Элемент `description` находится в пространстве имен `vstov4` . Он содержит описание надстройки, которая отображается в диалоговом окне надстроек COM в приложении Microsoft Office.

 У элемента `description` нет атрибутов и дочерних элементов.

## <a name="vsto-add-in-example"></a>Пример надстройки VSTO

### <a name="description"></a>Описание
 В приведенном ниже примере кода показан элемент `description` для решения уровня приложения, которое развертывается с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Этот пример кода является частью большого примера, приведенного в разделе [манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).

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