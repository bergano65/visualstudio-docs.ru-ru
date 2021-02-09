---
title: Элемент TemplateGroupID (шаблоны Visual Studio) | Документация Майкрософт
description: Сведения об элементе TemplateGroupID и о том, как он указывает, в каком типе проекта будут отображаться шаблоны элементов.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateGroupID
helpviewer_keywords:
- TemplateGroupID element [Visual Studio Templates]
- <TemplateGroupID> element [Visual Studio Templates]
ms.assetid: bce7b49a-90bc-4691-aff3-a87e209f6d83
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d9db0d2744648901a9389bd2d2805d8c6a4073ae
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895366"
---
# <a name="templategroupid-element-visual-studio-templates"></a>Элемент TemplateGroupID (шаблоны Visual Studio)
Указывает, в каком типе проекта будут отображаться шаблоны элементов. Этот элемент важен, если [шовбидефаулт (шаблоны Visual Studio)](../extensibility/showbydefault-visual-studio-templates.md) имеет значение `false` . Если для [шовбидефаулт (шаблоны Visual Studio)](../extensibility/showbydefault-visual-studio-templates.md) задано значение `true` , то шаблон элемента доступен во всех типах проектов.

 \<VSTemplate> \<TemplateData>
 \<TemplateGroupID>

## <a name="syntax"></a>Синтаксис

```
<TemplateGroupID> ... </TemplateGroupID>
```

## <a name="attributes-and-elements"></a>Атрибуты и элементы
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты
 Отсутствует.

### <a name="child-elements"></a>Дочерние элементы
 Отсутствует.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Определяет категорию шаблона и то, отображается ли он в диалоговом окне **Новый проект** или **Добавить новый элемент** .|

## <a name="text-value"></a>Текстовое значение
 Текстовое значение является обязательным.

 Этот текст задает идентификатор для категории шаблонов элементов.

## <a name="remarks"></a>Remarks
 `TemplateGroupID` является элементом.

 Значение `TemplateGroupID` элемента используется вместе с регистрацией системы проекта (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\ *\<version number>* \Projects \\ ) для фильтрации шаблонов, которые отображаются в диалоговом окне **Добавление нового элемента** .

|Значение Visual C++|Значение|
|------------------------|-------------|
|VC-Native|Используется для собственных проектов. Кроме того, используется по умолчанию, когда не удается определить тип проекта.|
|VC-Managed|Используется для управляемых проектов (/clr).|
|VC-Windows|Используется для всех проектов, нацеленных на платформу Windows (машинный код/управляемый код/хранилище).|
|WinRT-Native-UAP|Используется для проектов хранилища Windows 10.|
|CodeSharing-Native|Используется для общих проектов элементов.|
|WinRT-Native-6.3|Используется для проектов Магазина Windows 8.1.|
|WinRT-Native-Phone-6.3|Используется для проектов Магазина Windows Phone 8.1.|
|WinRT-Native|Используется для проектов Магазина Windows 8.0.|
|VC-Android|Используется для проектов Android.|

## <a name="see-also"></a>См. также раздел
- [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
