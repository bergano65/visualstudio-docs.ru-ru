---
title: Элемент ButtonText | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ButtonText element (VSCT XML schema)
- VSCT XML schema elements, ButtonText
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f8ba4667a34594c764a57788ee468d32733ded8e
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/24/2018
ms.locfileid: "39232017"
---
# <a name="buttontext-element"></a>Элемент ButtonText
Это поле позволяет указать текст, отображаемый в различные меню. По умолчанию `ButtonText` элемент появляется в контроллеры меню. `ButtonText` Элемент становится значением по умолчанию, если другие текстовые поля будут пусты. `ButtonText` Элемент не может быть пустым, даже если указаны другие текстовые поля.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
<ButtonText>My Command</ButtonText>  
```  
  
## <a name="attributes-and-elements"></a>Элементы и атрибуты  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
 Отсутствует.  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание:|  
|-------------|-----------------|  
|[Элемент Strings](../extensibility/strings-element.md)|Группирует элементы текста, таких как `ButtonText` и `CommandName`.|  
  
## <a name="text-value"></a>Текстовое значение  
 Текстовое значение `ButtonText` элемент содержит текст, отображаемый для пунктов меню, комбинировать и других элементов пользовательского интерфейса (UI), которые имеют видимым текстом.  
  
## <a name="see-also"></a>См. также  
 [Visual Studio командные файлы table (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)