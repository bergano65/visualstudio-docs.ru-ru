---
title: '&lt;&gt;элемент Document (разработка решений Office в Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document element
- application manifests [Office development in Visual Studio], <document> element
- <document> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 36d822d60d1a28d48f660f6d358b75bf4a913048
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "63000027"
---
# <a name="ltdocumentgt-element-office-development-in-visual-studio"></a>&lt;&gt;элемент Document (разработка решений Office в Visual Studio)
  `document`Элемент `vstov4` пространства имен хранит сведения о настройке для настроек на уровне документа.

## <a name="syntax"></a>Синтаксис

```xml
<document solutionId />
```

## <a name="elements-and-attributes"></a>Элементы и атрибуты
 Требуется только для настроек на уровне документа. Элемент `document` находится в пространстве имен `vstov4` . Элемент `document` имеет перечисленные ниже атрибуты.

|Атрибут|Описание|
|---------------|-----------------|
|`solutionId`|Обязательный. Идентификатор GUID, используемый Инструменты Visual Studio для среды выполнения Office для уникальной идентификации решения на уровне документа. Это значение сохраняется как свойство пользовательского документа _AssemblyLocation. Дополнительные сведения см. в разделе [Общие сведения о настраиваемых свойствах документа](../vsto/custom-document-properties-overview.md).|

 У элемента`document` нет дочерних элементов.

## <a name="document-level-customization-example"></a>Пример настройки на уровне документа

### <a name="description"></a>Описание
 В следующем примере кода показан `document` элемент в решении Office на уровне документа, развернутом с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Этот пример кода является частью большого примера, приведенного в разделе [манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Код

```xml
<vstov4:document
  solutionId="73e" />
```

## <a name="see-also"></a>См. также

- [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md)
- [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)