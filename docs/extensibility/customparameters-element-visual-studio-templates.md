---
title: Элемент пользовательских параметров (Visual Studio Templates) Документы Майкрософт
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameters
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: cf3efc91-1532-4022-bbb8-a18658424fee
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f524996c226f001c68ddc7ac9aa8cb3b99857fc5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739420"
---
# <a name="customparameters-element-visual-studio-templates"></a>Элемент пользовательских параметров (шаблоны Visual Studio)
Группирует пользовательские параметры, которые должны быть переданы мастеру шаблона, когда мастер делает замену параметров.

## <a name="syntax"></a>Синтаксис

```
<CustomParameters>
    <CustomParameter/>
    <CustomParameter/>
</CustomParameters>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты
 Нет.

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|[CustomParameter](../extensibility/customparameter-element-visual-studio-templates.md)|Необязательный элемент.<br /><br /> Содержит специальное имя параметра и значение для использования при создании проекта или элемента из шаблона. Элемент `CustomParameter` может содержать любое число элементов `CustomParameters`, включая ноль.|

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Определяет содержимое шаблона.|

## <a name="remarks"></a>Примечания

## <a name="example"></a>Пример
 Ниже приводится следующий пример, как использовать несколько пользовательских параметров в шаблоне. Когда проект или элемент создается из шаблона со следующими `$color1$` пользовательскими параметрами, все экземпляры и `$color2$` в файлах шаблона будут заменены `Red` и, `Blue`соответственно.

```
<CustomParameters>
    <CustomParameter Name="$color1$" Value="Red"/>
    <CustomParameter Name="$color2$" Value="Blue "/>
</CustomParameters>
```

## <a name="see-also"></a>См. также
- [Элемент CustomParameter (шаблоны Visual Studio)](../extensibility/customparameter-element-visual-studio-templates.md)
- [Параметры шаблона](../ide/template-parameters.md)
- [Ссылка на схему шаблона Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
