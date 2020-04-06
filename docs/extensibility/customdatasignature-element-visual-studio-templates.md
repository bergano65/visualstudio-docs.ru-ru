---
title: Элемент customDataSignature (Шаблоны визуальных студий) Документы Майкрософт
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <CustomDataSignature> Element (Visual Studio Templates)
- CustomDataSignature Element (Visual Studio Templates)
ms.assetid: 8c3db51d-7014-4484-802a-15aa1353dbdb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ec8bae34da0f007bac65f26c4e442c1d03e56d08
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739443"
---
# <a name="customdatasignature-element-visual-studio-templates"></a>Элемент CustomDataSignature (шаблоны Visual Studio)
Определяет текстовую подпись для поиска пользовательских данных.

 \<VSTemplate \<> TemplateData> \<> customDataSignature

## <a name="syntax"></a>Синтаксис

```
<CustomDataSignature>"string"</CustomDataSignature>
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

 Текст представляет собой строку с текстовой подписью, которая необходима для поиска пользовательских данных.

## <a name="remarks"></a>Примечания
 Параметр `CustomDataSignature` является необязательным элементом.

## <a name="see-also"></a>См. также
- [Ссылка на схему шаблонов визуальной студии](../extensibility/visual-studio-template-schema-reference.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
