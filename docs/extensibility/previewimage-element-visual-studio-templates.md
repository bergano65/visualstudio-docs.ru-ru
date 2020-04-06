---
title: PreviewImage Элемент (Visual Studio шаблоны) Документы Майкрософт
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <PreviewImage> Element (Visual Studio Templates)
- PreviewImage Element (Visual Studio Templates)
ms.assetid: d1796f20-523b-4e0d-8ac3-ca87f3b5a9b6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f20cfe5f3ef35b23a52972ef1e3b7d9d4adc5a39
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702008"
---
# <a name="previewimage-element-visual-studio-templates"></a>Элемент PreviewImage (шаблоны Visual Studio)
Обращите изображение предварительного просмотра, как имя файла, для изображения предварительного просмотра, которое будет отображаться в поле диалога **New Project** или **Добавить new Item.**

 \<VSTemplate \<> TemplateData> \<PreviewImage>

## <a name="syntax"></a>Синтаксис

```
<PreviewImage>"filename"</PreviewImage>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты
 Нет.

### <a name="child-elements"></a>Дочерние элементы
 Нет.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Категоризирует шаблон и определяет, как он отображается либо в **новом проекте,** либо в диалоговом окне **Добавить новый элемент.**|

## <a name="text-value"></a>Текстовое значение
 Текстовое значение является обязательным.

 Текст должен быть строкой, представляющей имя файла.

## <a name="remarks"></a>Примечания
 Параметр `PreviewImage` является необязательным элементом.

## <a name="see-also"></a>См. также
- [Ссылка на схему шаблона Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
