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
ms.openlocfilehash: cd3ed1477d1c4d345e5fc6f6496d12044d4af244
ms.sourcegitcommit: d9254e54079ae01cdf2d07b11f988faf688f80fc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/11/2020
ms.locfileid: "88114236"
---
# <a name="vsixlanguagepack-element-vsix-language-pack-schema"></a>Элемент VSIXLanguagePack (схема языкового пакета VSIX)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Обязательный элемент. Предоставляет корневой элемент для языкового пакета VSIX. Языковой пакет VSIX предоставляет локализованные сведения об установке для пакета VSIX.  
  
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
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`xmlns`|Пространство имен XML, в котором определена схема языкового пакета VSIX.|  
  
## <a name="xmlns-attribute"></a>Атрибут xmlns  
  
|Значение|Описание|  
|-----------|-----------------|  
|`http://schemas.microsoft.com/developer/vsx-schema-lp/2010`|Обязательный элемент. Расположение файла, определяющего схему для языковых пакетов.|  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент LocalizedName](../extensibility/localizedname-element-vsix-language-pack-schema.md)|Обязательный элемент. Локализованное имя устанавливаемого расширения.|  
|[Элемент LocalizedDescription](../extensibility/localizeddescription-element-vsix-language-pack-schema.md)|Обязательный элемент. Локализованное описание устанавливаемого расширения.|  
|[Элемент MoreInfoURL](../extensibility/moreinfourl-element-vsix-language-pack-schema.md)|Необязательный элемент. Ссылка на локализованные сведения о расширении.|  
|[Элемент License](../extensibility/license-element-vsix-language-pack-schema.md)|Необязательный элемент. Путь к локализованной версии файла лицензии для расширения.|  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|Отсутствуют||  
  
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
        Нет
    :::column-end:::
:::row-end:::
  
## <a name="see-also"></a>См. также:  
 [Справочник по схеме языкового пакета VSX](../extensibility/vsx-language-pack-schema-reference.md) [Локализация пакетов VSIX](../extensibility/localizing-vsix-packages.md) [справочник по схеме расширения VSIX 1,0](/previous-versions/dd393700(v=vs.110))
