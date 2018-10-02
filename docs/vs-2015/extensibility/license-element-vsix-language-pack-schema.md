---
title: Лицензии элемент (схема языкового пакета VSIX) | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 57dac3b7-0cdd-405c-9af5-30ed9ca45e53
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ecf1913878137d84346275beccb512027f74f8f3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47563111"
---
# <a name="license-element-vsix-language-pack-schema"></a>Элемент License (схема языкового пакета VSIX)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [элемент License (схема языкового пакета VSIX)](https://docs.microsoft.com/visualstudio/extensibility/license-element-vsix-language-pack-schema).  
  
Необязательный. Путь к локализованной версии файла лицензии для расширения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<License>FilePath\license.txt</License>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|Нет||  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|Нет||  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент LanguagePack VSIX](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|Обязательно. Предоставляет корневой элемент для языкового пакета VSIX.|  
  
## <a name="text-value"></a>Текстовое значение  
 Относительный путь к локализованному файлу лицензии для отображения.  
  
## <a name="remarks"></a>Примечания  
 Если `License` элемент задан, то во время установки отображается текст назначенного файла лицензии, и пользователь должен принять лицензию для продолжения.  
  
## <a name="element-information"></a>Сведения об элементе  
  
|||  
|-|-|  
|Пространство имен|http://schemas.microsoft.com/developer/vsx-schema-lp/2010|  
|Имя схемы|Схема языкового пакета VSIX|  
|Файл проверки|VSIXLanguagePackSchema.xsd|  
|Может быть пустым|Неприменимо|  
  
## <a name="see-also"></a>См. также  
 [Справочник по схеме VSX языкового пакета](../extensibility/vsx-language-pack-schema-reference.md)   
 [Локализация пакетов VSIX](../extensibility/localizing-vsix-packages.md)   
 [Справочник по схеме 1.0 расширение VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)

