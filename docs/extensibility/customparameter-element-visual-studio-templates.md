---
title: Элемент customParameter (Visual Studio Templates) Документы Майкрософт
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameter
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: 743c4489-74ac-403a-bbaa-eed7d785a3ac
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9063a354f03b896e189566e8d84a18caf7509db8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739427"
---
# <a name="customparameter-element-visual-studio-templates"></a>Элемент CustomParameter (шаблоны Visual Studio)
Содержит специальное имя параметра и значение для использования при создании проекта или элемента из шаблона.

## <a name="syntax"></a>Синтаксис

```
<CustomParameter Name="name" Value="value">
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|`Name`|Обязательный элемент. Имя параметра. Формат для параметров составляет $*имя*$ .|
|`Value`|Обязательный элемент. Значение замены параметра.|

### <a name="child-elements"></a>Дочерние элементы
 Нет.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Группирует пользовательские параметры, которые должны быть переданы мастеру шаблона, когда мастер делает замену параметров.|

## <a name="remarks"></a>Примечания
 Когда шаблон `CustomParameter` содержит элементы, `Name` каждый экземпляр `Value` атрибута заменяется атрибутом в созданных файлах проекта или элемента.

## <a name="example"></a>Пример
 Ниже приводится следующий пример, как использовать несколько пользовательских параметров в шаблоне. Когда проект или элемент создается из шаблона со следующими `$color1$` пользовательскими параметрами, все экземпляры и `$color2$` в файлах шаблона будут заменены `Red` и, `Blue`соответственно.

```
<CustomParameters>
    <CustomParameter Name="$color1$" Value="Red"/>
    <CustomParameter Name="$color2$" Value="Blue "/>
</CustomParameters>
```

## <a name="see-also"></a>См. также
- [Элемент пользовательских параметров (шаблоны Visual Studio)](../extensibility/customparameters-element-visual-studio-templates.md)
- [Параметры шаблона](../ide/template-parameters.md)
- [Ссылка на схему шаблона Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
