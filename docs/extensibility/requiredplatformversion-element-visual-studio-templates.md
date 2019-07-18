---
title: Элемент RequiredPlatformVersion (шаблоны Visual Studio) | Документация Майкрософт
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 6f0e4986-3157-4bba-aed3-c28413ebe976
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cd166e41588ee440d9e0a1e90494aaa8f5091909
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66334157"
---
# <a name="requiredplatformversion-element-visual-studio-templates"></a>Элемент RequiredPlatformVersion (шаблоны Visual Studio)
Указывает минимальную версию операционной системы, шаблон проекта необходима для правильной работы. Этот элемент используется для шаблонов проектов, которые создают [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] приложений.

 `RequiredPlatformVersion` Значение сравнивается непосредственно с версией операционной системы. Если `RequiredPlatformVersion` выше, чем версия операционной системы, шаблон не отображается в **новый проект** диалоговое окно. Для указания шаблона для [!INCLUDE[win8](../debugger/includes/win8_md.md)] или более поздней версии, задайте `RequiredPlatformVersion` для 6.2.0. Для указания шаблона для [!INCLUDE[win81](../debugger/includes/win81_md.md)] или более поздней версии, задайте `RequiredPlatformVersion` для 6.3.0.

 Шаблоны, которые указывают `RequiredPlatformVersion`= 8, совместимы с предыдущей клиента [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] шаблонов.

 VSTemplate TemplateData... TargetPlatformName RequiredPlatformVersion

## <a name="syntax"></a>Синтаксис

```xml
<RequiredPlatformVersion> OperatingSystem </RequiredPlatformVersion>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 Отсутствует.

### <a name="attributes"></a>Атрибуты
 Отсутствует.

### <a name="child-elements"></a>Дочерние элементы
 Отсутствует.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[TemplatePlatformName](../extensibility/templatedata-element-visual-studio-templates.md)|Задает платформу, для которой предназначен шаблон проекта.|

## <a name="text-value"></a>Текстовое значение
 Текстовое значение является обязательным.

## <a name="remarks"></a>Примечания
 Данный текст задает минимальную версию операционной системы для шаблона.

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
- [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)