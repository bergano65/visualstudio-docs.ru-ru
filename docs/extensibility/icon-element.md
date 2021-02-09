---
title: Icon, элемент | Документация Майкрософт
description: Сведения об элементе Icon, который представляет значки, используемые в расширениях интегрированной среды разработки Visual Studio, включая атрибуты для точечного рисунка и область точечного рисунка.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Icon
- Icon element (VSCT XML schema)
ms.assetid: 73c58fe3-d53c-4f4e-b025-29567c6cbb7c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c4e68889ae6ea8396795137243cf732a9b028931
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883276"
---
# <a name="icon-element"></a>Icon, элемент
Атрибут GUID тега Icon является идентификатором GUID определенного растрового изображения. `id`Атрибут выбирает слот на панели растрового изображения. Этот элемент является необязательным. Если этот элемент не включен в значение **гуидоффицеикон: мсотЦидноикон** будет подразумеваемым.

## <a name="syntax"></a>Синтаксис

```xml
<Icon guid="guidImages" id="bmpPic1" />
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|guid|Обязательный элемент. Идентификатор GUID определенного растрового изображения.|
|идентификатор|Обязательный элемент. Выбирает слот в полоске точечного рисунка.|

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|Нет.|Отсутствует.|

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Button, элемент](../extensibility/buttons-element.md)||

## <a name="see-also"></a>См. также раздел
- [Файлы таблицы команд Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
