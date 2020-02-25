---
title: Элемент VSIXLanguagePack (схема языкового пакета VSIX) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
ms.assetid: 767f5c22-8b87-49ca-92aa-a7a3f026469f
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e2e1df362fddeab5be98ff90460a8a1a7d4b7876
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2020
ms.locfileid: "77558003"
---
# <a name="vsixlanguagepack-element-vsix-language-pack-schema"></a>Элемент VSIXLanguagePack (схема языкового пакета VSIX)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Обязательное. Предоставляет корневой элемент для языкового пакета VSIX. Языковой пакет VSIX предоставляет локализованные сведения об установке для пакета VSIX.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<VSIXLanguagePack>  
  <LocalizedName>...</LocalizedName>  
  <LocalizedDescription>...</LocalizedDescription>  
  <MoreInfoURL>...</MoreInfoURL>  
  <License>...</License>  
</VSIXLanguagePack>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 Следующие разделы описывают атрибуты, дочерние элементы и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`xmlns`|Пространство имен XML, в котором определена схема языкового пакета VSIX.|  
  
## <a name="xmlns-attribute"></a>Атрибут xmlns  
  
|Значение|Описание|  
|-----------|-----------------|  
|`http://schemas.microsoft.com/developer/vsx-schema-lp/2010`|Обязательное. Расположение файла, определяющего схему для языковых пакетов.|  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент LocalizedName](../extensibility/localizedname-element-vsix-language-pack-schema.md)|Обязательное. Локализованное имя устанавливаемого расширения.|  
|[Элемент LocalizedDescription](../extensibility/localizeddescription-element-vsix-language-pack-schema.md)|Обязательное. Локализованное описание устанавливаемого расширения.|  
|[Элемент MoreInfoURL](../extensibility/moreinfourl-element-vsix-language-pack-schema.md)|Необязательно. Ссылка на локализованные сведения о расширении.|  
|[Элемент License](../extensibility/license-element-vsix-language-pack-schema.md)|Необязательно. Путь к локализованной версии файла лицензии для расширения.|  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|Нет||  
  
## <a name="element-information"></a>Сведения об элементе  
  
|                 |                                                           |
|-----------------|-----------------------------------------------------------|
|    Пространство имен    | `http://schemas.microsoft.com/developer/vsx-schema-lp/2010` |
|   Имя схемы   |                 Схема языкового пакета VSIX                 |
| Файл проверки |                Всикслангуажепакксчема. xsd                 |
|  Может быть пустым   |                            Нет                             |
  
## <a name="see-also"></a>См. также:  
 [Справочник по схеме языкового пакета VSX](../extensibility/vsx-language-pack-schema-reference.md) [Локализация пакетов VSIX](../extensibility/localizing-vsix-packages.md) [справочник по схеме расширения VSIX 1,0](/previous-versions/dd393700(v=vs.110))
