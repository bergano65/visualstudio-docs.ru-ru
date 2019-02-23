---
title: Элемент CustomParameter (шаблоны Visual Studio) | Документация Майкрософт
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameter
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: 743c4489-74ac-403a-bbaa-eed7d785a3ac
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc0ac3d936037e9b92567a6fcf20b26c25cb5d3f
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56705941"
---
# <a name="customparameter-element-visual-studio-templates"></a>Элемент CustomParameter (шаблоны Visual Studio)
Содержит имя пользовательского параметра и значение, используемое при создании проекта или элемента из шаблона.

## <a name="syntax"></a>Синтаксис

```
<CustomParameter Name="name" Value="value">
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|`Name`|Обязательный. Имя параметра. Формат для параметров: $*имя*$.|
|`Value`|Обязательный. Значение замены для параметра.|

### <a name="child-elements"></a>Дочерние элементы
 Отсутствует.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание:|
|-------------|-----------------|
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Группирует пользовательские параметры, которые должны быть переданы мастера шаблонов, когда мастер замены параметров.|

## <a name="remarks"></a>Примечания
 Если шаблон содержит `CustomParameter` элементов, каждый экземпляр `Name` атрибут заменяется `Value` атрибут в создаваемых файлов проекта или элемента.

## <a name="example"></a>Пример
 В следующем примере показано, как использовать несколько пользовательских параметров в шаблоне. При создании проекта или элемента из шаблона, выполнив следующие пользовательские параметры, все экземпляры `$color1$` и `$color2$` в шаблоне файлов будет заменен `Red` и `Blue`, соответственно.

```
<CustomParameters>
    <CustomParameter Name="$color1$" Value="Red"/>
    <CustomParameter Name="$color2$" Value="Blue "/>
</CustomParameters>
```

## <a name="see-also"></a>См. также
- [Элемент CustomParameters (шаблоны Visual Studio)](../extensibility/customparameters-element-visual-studio-templates.md)
- [Параметры шаблона](../ide/template-parameters.md)
- [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)