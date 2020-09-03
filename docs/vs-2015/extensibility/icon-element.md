---
title: Icon, элемент | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Icon
- Icon element (VSCT XML schema)
ms.assetid: 73c58fe3-d53c-4f4e-b025-29567c6cbb7c
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ca5ced87596b5e40ae70e3faa06e58493da3d8ab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203996"
---
# <a name="icon-element"></a>Элемент Icon
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Атрибут GUID тега Icon является идентификатором GUID определенного растрового изображения.  Атрибут ID выбирает слот на панели растрового изображения. Этот элемент является необязательным.  Если этот элемент опущен, значение **гуидоффицеикон: мсотЦидноикон** будет подразумеваемым.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<Icon guid="guidImages" id="bmpPic1" />  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|guid|Обязательный. Идентификатор GUID определенного растрового изображения.|  
|идентификатор|Обязательный. Выбирает слот в полоске точечного рисунка.|  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|Нет.|Отсутствует.|  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент Buttons](../extensibility/buttons-element.md)||  
  
## <a name="see-also"></a>См. также:  
 [Файлы таблицы команд Visual Studio (VSCT-файлы)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
