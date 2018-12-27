---
title: Элемент CustomDataSignature (шаблоны Visual Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <CustomDataSignature> Element (Visual Studio Templates)
- CustomDataSignature Element (Visual Studio Templates)
ms.assetid: 8c3db51d-7014-4484-802a-15aa1353dbdb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: eddff64680dd41637f78f33c46fe78f32bbc3a85
ms.sourcegitcommit: 35bebf794f528d73d82602e096fd97d7b8f82c25
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/18/2018
ms.locfileid: "53561321"
---
# <a name="customdatasignature-element-visual-studio-templates"></a>Элемент CustomDataSignature (шаблоны Visual Studio)
Задает текст подписи для поиска пользовательских данных.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<CustomDataSignature >  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<CustomDataSignature>"string"</CustomDataSignature>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Определяет, как он отображается в любом категорию шаблона и **новый проект** или **Добавление нового элемента** диалоговое окно.|  
  
## <a name="text-value"></a>Текстовое значение  
 Текстовое значение является обязательным.  
  
 Текст — это строки, которая содержит текстовую подпись, которая необходим для поиска пользовательских данных.  
  
## <a name="remarks"></a>Примечания  
 `CustomDataSignature` — это необязательный элемент.  
  
## <a name="see-also"></a>См. также  
 [Справочник по схеме Visual Studio шаблон](../extensibility/visual-studio-template-schema-reference.md)   
 [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)