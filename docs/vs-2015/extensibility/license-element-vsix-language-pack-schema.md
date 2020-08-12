---
title: Элемент License (схема языкового пакета VSIX) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
ms.assetid: 57dac3b7-0cdd-405c-9af5-30ed9ca45e53
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 91f0792f64e09292836a3b2d60f669c67903b3a7
ms.sourcegitcommit: d9254e54079ae01cdf2d07b11f988faf688f80fc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/11/2020
ms.locfileid: "88114187"
---
# <a name="license-element-vsix-language-pack-schema"></a>Элемент License (схема языкового пакета VSIX)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Необязательный элемент. Путь к локализованной версии файла лицензии для расширения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<License>FilePath\license.txt</License>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|Отсутствуют||  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|Отсутствуют||  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент LanguagePack VSIX](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|Обязательный элемент. Предоставляет корневой элемент для языкового пакета VSIX.|  
  
## <a name="text-value"></a>Текстовое значение  
 Относительный путь к локализованному файлу лицензии, который должен быть отображен.  
  
## <a name="remarks"></a>Remarks  
 Если `License` элемент определен, то текст назначенного файла лицензии отображается во время установки, и пользователь должен принять условия лицензии, чтобы продолжить.  
  
## <a name="element-information"></a>Сведения об элементе  

:::row:::
    :::column:::
        Пространство имен  
    :::column-end:::
    :::column:::
        `http://schemas.microsoft.com/developer/vsx-schema-lp/2010`
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        Имя схемы
    :::column-end:::
    :::column:::
        Схема языкового пакета VSIX
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        Файл проверки
    :::column-end:::
    :::column:::
        Всикслангуажепакксчема. xsd
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        Может быть пустым
    :::column-end:::
    :::column:::
        Неприменимо
    :::column-end:::
:::row-end:::
  
## <a name="see-also"></a>См. также:  
 [Справочник по схеме языкового пакета VSX](../extensibility/vsx-language-pack-schema-reference.md)   
 [Локализация пакетов VSIX](../extensibility/localizing-vsix-packages.md)   
 [Справочник по схеме расширения VSIX 1,0](/previous-versions/dd393700(v=vs.110))
