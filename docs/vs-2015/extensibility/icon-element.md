---
title: Элемент Icon | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, Icon
- Icon element (VSCT XML schema)
ms.assetid: 73c58fe3-d53c-4f4e-b025-29567c6cbb7c
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 66c5ea847d348c86c5de5bde611bfbfbdcb963c6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572656"
---
# <a name="icon-element"></a>Элемент Icon
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [элемент Icon](https://docs.microsoft.com/visualstudio/extensibility/icon-element).  
  
Атрибут guid значок тега – идентификатор guid, определенный растрового изображения.  Атрибут id выбирает слота в наборе точечных рисунков. Этот элемент является необязательным.  Если этот элемент отсутствует значение **guidOfficeIcon:msotcidNoIcon** будет содержится в разрешении.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<Icon guid="guidImages" id="bmpPic1" />  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|guid|Обязательно. Идентификатор guid, определенный растрового изображения.|  
|id|Обязательно. Выбор слота в наборе точечных рисунков.|  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|Отсутствует.|Отсутствует.|  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент Buttons](../extensibility/buttons-element.md)||  
  
## <a name="see-also"></a>См. также  
 [Файлы таблицы команд Visual Studio (VSCT-файлы)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

