---
title: "Битовая карта, элемент | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: eb265aabdb4feda05512e036cda19abc574e2fd4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="bitmap-element"></a>Битовая карта, элемент
Определяет растрового изображения. Загрузке точечного рисунка из ресурса или файла.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<Bitmap guid="guidImages" href="images\MyImage.bmp" usedList="bmp1, bmp2, bmp3" />  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание:|  
|---------------|-----------------|  
|guid|Обязательно. Идентификатор GUID идентификатор GUID или идентификатор команды.<br /><br /> Атрибут guid для растрового изображения не связан с любой VSPackage или другие группы команд.  Он должен быть уникальным на определении точечного рисунка и не должны использоваться для других целей.|  
|Идентификатор ресурса|Идентификатор идентификатор GUID или идентификатор команды. Требуется идентификатор ресурса или атрибут href.<br /><br /> Атрибут resID — целочисленный идентификатор ресурса, определяющий полосе растрового изображения, должен быть загружен во время слияния таблицы команд.  При загрузке таблицы команд растровых изображений, заданных идентификатором ресурса будут загружены из ресурса, одного модуля.|  
|usedList|Требуется, если присутствует атрибут resID. Выбор доступных образов в полосе растрового изображения.|  
|href|Путь к растровому изображению. Требуется идентификатор ресурса или атрибут href.<br /><br /> В путь поиска включаемых выполняется поиск файла указанное изображение, внедренная в выходной двоичный файл.  Во время слияния таблицы команд образ копируется и не поиск дополнительных ресурсов или нагрузки не требуется.  Если отсутствует атрибут usedList, доступны все образы в полосе. **Примечание:** изображения может быть указано в одном из нескольких форматов, которые включают .bmp, PNG и GIF.  Более ранних версиях компилятора не поддерживали 32-разрядных растровых изображений, которые бы данные альфа-канала для частичной прозрачности. Решение для этих версий — использовать формат PNG.|  
|Условие|Необязательный. В разделе [условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание:|  
|-------------|-----------------|  
|[Элемент Bitmaps](../extensibility/bitmaps-element.md)|Группирует элементы растрового изображения.|  
  
## <a name="example"></a>Пример  
  
```  
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />  
<Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"  
  usedList="1, 2, 3, 4"/>  
```  
  
## <a name="see-also"></a>См. также  
 [Файлы таблицы команд Visual Studio (VSCT-файлы)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)