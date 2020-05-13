---
title: ОбязательныйЭлементПлатформной версии (Visual Studio Templates) Документы Майкрософт
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 6f0e4986-3157-4bba-aed3-c28413ebe976
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3bc22f97401fe5e3724f2e44c873c72acbf65be1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701494"
---
# <a name="requiredplatformversion-element-visual-studio-templates"></a>Элемент RequiredPlatformVersion (шаблоны Visual Studio)
Упоняет минимальную версию операционной системы, которая требует правильной работы шаблона проекта. Этот элемент используется для шаблонов [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] проектов, которые создают приложения.

 Значение `RequiredPlatformVersion` сравнивается непосредственно с версией операционной системы. `RequiredPlatformVersion` Если версия операционной системы выше, то шаблон не отображается в диалоговом окне **нового проекта.** Чтобы указать [!INCLUDE[win8](../debugger/includes/win8_md.md)] шаблон для `RequiredPlatformVersion` или выше, установите 6.2.0. Чтобы указать [!INCLUDE[win81](../debugger/includes/win81_md.md)] шаблон для `RequiredPlatformVersion` или выше, установите 6.3.0.

 Шаблоны, `RequiredPlatformVersion`указывающие No8, совместимы [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] с предыдущими шаблонами клиента.

 VSTemplate TemplateData ..... TargetPlatformName ТребуетсяПлатформа

## <a name="syntax"></a>Синтаксис

```xml
<RequiredPlatformVersion> OperatingSystem </RequiredPlatformVersion>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 Нет.

### <a name="attributes"></a>Атрибуты
 Нет.

### <a name="child-elements"></a>Дочерние элементы
 Нет.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[ШаблонПлатформаНамл](../extensibility/templatedata-element-visual-studio-templates.md)|Задает платформу, для которой предназначен шаблон проекта.|

## <a name="text-value"></a>Текстовое значение
 Текстовое значение является обязательным.

## <a name="remarks"></a>Примечания
 В этом тексте оговаривается минимальная версия операционной системы, требуемая шаблоном.

## <a name="example"></a>Пример
 В этом примере указывается, что шаблон проекта предназначен для [!INCLUDE[win8](../debugger/includes/win8_md.md)] или более поздней версии.

```xml
<VSTemplate Type="Project" Version="3.0.0"    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <TargetPlatformName>Windows</TargetPlatformName>
            <RequiredPlatformVersion>6.3.0</RequiredPlatformVersion>

    </TemplateData>
    <TemplateContent>

    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>См. также
- [Элемент TargetPlatformName (шаблоны Visual Studio)](../extensibility/targetplatformname-element-visual-studio-templates.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
- [Ссылка на схему шаблона Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
