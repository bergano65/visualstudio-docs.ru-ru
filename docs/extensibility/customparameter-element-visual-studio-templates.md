---
title: Элемент Кустомпараметер (шаблоны Visual Studio) | Документация Майкрософт
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739427"
---
# <a name="customparameter-element-visual-studio-templates"></a>Элемент Кустомпараметер (шаблоны Visual Studio)
Содержит имя и значение настраиваемого параметра, используемого при создании проекта или элемента из шаблона.

## <a name="syntax"></a>Синтаксис

```
<CustomParameter Name="name" Value="value">
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|`Name`|Обязательный элемент. Имя параметра. Формат параметров — $*Name*$.|
|`Value`|Обязательный. Заменяющее значение для параметра.|

### <a name="child-elements"></a>Дочерние элементы
 Отсутствует.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Группирует пользовательские параметры, которые должны быть переданы мастеру шаблонов, когда мастер выполняет замену параметров.|

## <a name="remarks"></a>Remarks
 Если шаблон содержит `CustomParameter` элементы, каждый экземпляр `Name` заменяется `Value` атрибутом в создаваемом файле проекта или элемента.

## <a name="example"></a>Пример
 В следующем примере показано, как использовать несколько пользовательских параметров в шаблоне. При создании проекта или элемента на основе шаблона со следующими пользовательскими параметрами все экземпляры `$color1$` и `$color2$` в файлах шаблонов будут заменены на `Red` и `Blue` соответственно.

```
<CustomParameters>
    <CustomParameter Name="$color1$" Value="Red"/>
    <CustomParameter Name="$color2$" Value="Blue "/>
</CustomParameters>
```

## <a name="see-also"></a>См. также раздел
- [Элемент CustomParameters (шаблоны Visual Studio)](../extensibility/customparameters-element-visual-studio-templates.md)
- [Параметры шаблона](../ide/template-parameters.md)
- [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
