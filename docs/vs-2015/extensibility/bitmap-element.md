---
title: Элемент Bitmap | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fc1fb57c7ec43421b211b29cfd6ab97b24a1864c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184746"
---
# <a name="bitmap-element"></a>Элемент Bitmap
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Определяет точечный рисунок. Точечный рисунок загружается либо из ресурса, либо из файла.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<Bitmap guid="guidImages" href="images\MyImage.bmp" usedList="bmp1, bmp2, bmp3" />  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|guid|Обязательный. Идентификатор GUID идентификатора команды GUID/ID.<br /><br /> Атрибут GUID для точечного рисунка не связан ни с каким пакетом VSPackage, ни с другой группой команд.  Оно должно быть уникальным для определения битовой карты и не должно использоваться для других целей.|  
|resID|Идентификатор идентификатора команды GUID/ID. Необходимо указать атрибут resID или href.<br /><br /> Атрибут resID — это целочисленный идентификатор ресурса, определяющий полосу битовой карты, которая должна быть загружена при слиянии таблицы команд.  При загрузке таблицы команд точечные рисунки, заданные ИДЕНТИФИКАТОРом ресурса, будут загружены из ресурса того же модуля.|  
|уседлист|Требуется, если имеется атрибут resID. Выбирает доступные изображения в полоске точечного рисунка.|  
|href|Путь к точечному рисунку. Необходимо указать атрибут resID или href.<br /><br /> Выполняется поиск пути включения для указанного файла изображения, который внедряется в результирующий двоичный файл.  Во время слияния Командная таблица копирует образ и не требует дополнительных операций поиска или загрузки ресурсов.  Если атрибут Уседлист отсутствует, будут доступны все изображения в полоске. **Примечание.**  Изображения могут предоставляться в одном из нескольких форматов, включая BMP, PNG и GIF.  Более ранние версии компилятора не поддерживали 32-разрядные растровые изображения, для которых в качестве неполной прозрачности использовались данные Alpha. Обходной путь для этих версий — использовать формат PNG.|  
|Условие|Необязательный элемент. См. раздел [Условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент Bitmaps](../extensibility/bitmaps-element.md)|Группирует элементы битовой карты.|  
  
## <a name="example"></a>Пример  
  
```  
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />  
<Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"  
  usedList="1, 2, 3, 4"/>  
```  
  
## <a name="see-also"></a>См. также:  
 [Файлы таблицы команд Visual Studio (VSCT-файлы)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
