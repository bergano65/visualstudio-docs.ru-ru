---
title: Элемент Icon | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Icon
- Icon element (VSCT XML schema)
ms.assetid: 73c58fe3-d53c-4f4e-b025-29567c6cbb7c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dd56391084788729c0f8439728f9afffd59da946
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66311252"
---
# <a name="icon-element"></a>Элемент Icon
Атрибут guid значок тега – идентификатор guid, определенный растрового изображения. `id` Атрибут выбирает слота в наборе точечных рисунков. Этот элемент является необязательным. Если этот элемент не включали значение **guidOfficeIcon:msotcidNoIcon** будет содержится в разрешении.

## <a name="syntax"></a>Синтаксис

```xml
<Icon guid="guidImages" id="bmpPic1" />
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|guid|Обязательный. Идентификатор guid, определенный растрового изображения.|
|id|Обязательный. Выбор слота в наборе точечных рисунков.|

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|Отсутствует.|Отсутствует.|

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Элемент Buttons](../extensibility/buttons-element.md)||

## <a name="see-also"></a>См. также
- [Visual Studio командные файлы table (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)