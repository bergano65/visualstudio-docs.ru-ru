---
title: Элемент ButtonText | Документы Microsoft
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
ms.openlocfilehash: 2fca0fbb22bf51353eeaa64f519face53bfb23c8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31100183"
---
# <a name="buttontext-element"></a>Элемент ButtonText
Это поле позволяет указать текст, отображаемый в разных меню. По умолчанию `ButtonText` элемент отображается в контроллеры меню. `ButtonText` Элемент становится значением по умолчанию, если другие текстовые поля остаются пустыми. `ButtonText` Элемент не может быть пустым, даже если указаны другие текстовые поля.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<ButtonText>My Command</ButtonText>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
 Отсутствует.  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент Strings](../extensibility/strings-element.md)|Группирует текстовые элементы, такие как `ButtonText` и `CommandName`.|  
  
## <a name="text-value"></a>Текстовое значение  
 Текстовое значение `ButtonText` элемент содержит текст, отображаемый для пунктов меню, комбинировать и других элементах пользовательского интерфейса (UI), отображается текст.  
  
## <a name="see-also"></a>См. также  
 [Файлы таблицы команд Visual Studio (VSCT-файлы)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)